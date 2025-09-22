# Project Constellation — Master Technical Plan v3.3 (Ultimate, Hardened)

> **Intent:** Over-engineered, enterprise-grade foundation designed for decades. Every area is addressed so detailed planning cannot “discover” a missing pillar later. Deterministic, observable, testable, sandboxed, versioned, and recoverable by default.

* **4.1. The Technical Vision Statement**  
  * **4.1.1.** Guiding Tenets: (e.g., "Simplicity over Complexity," "Data-Oriented," "Built to Evolve").  
  * **4.1.2.** The Target Platform Philosophy.  
* **4.2. The Core Architectural Mandates**  
  * **4.2.1.** The Principle of Decoupling: Ensuring Gameplay, Simulation, and Graphics can operate independently.  
  * **4.2.2.** The Data & Persistence Strategy Charter.  
  * **4.2.3.** The Networking & Online Services Philosophy.  
* **4.3. The Artificial Intelligence (AI) Charter**  
  * **4.3.1.** The Philosophical Goal of AI: What is the intended role and behavior of AI entities? (e.g., "Believable Agents," "Challenging Opponents," "Tools for the Player").  
  * **4.3.2.** The Ethical Boundaries of AI Design.  
  * **4.3.3.** The Architectural Principles of the AI System.

---

## 0) Scope, Non‑Negotiables, and Unknowns Ledger

**Scope:** Single-player first, **multiplayer-ready**. Engine-agnostic **Simulation Core** (truth) + Presentation Hosts (Unity 6 LTS initially). Planet-scale sandbox with meta/sim split, genre-ladder lenses, diegetic modding.

**Non‑Negotiables:**

* Determinism in the Simulation Core; fixed timestep; seeded RNG; platform-stable math paths.
* Two-process optional split (Sim ↔ Presentation) with versioned IPC; crash isolation.
* Event-sourced persistence with snapshots; journal integrity, repair, and forensics.
* Regionized world streaming; async hydration; predictive prefetch; strict budgets.
* Plugin SDK with capability manifests, signatures, optional WASM sandbox.
* Observability everywhere (metrics, logs, traces, flight recorder, truth overlay).
* Schema registry with migrations and long-term compatibility gates.

**Unknowns Ledger (tracked & bounded):**

* **Physics determinism:** final integrator choice, tolerance bounds, sub-stepping strategy.
* **Large-battle resolution:** final router thresholds and deterministic downsampling.
* **WASM embedders:** exact runtime host and ABI shape.
* **Terrain representation:** signed distance fields vs. heightfields vs. voxel hybrid and clipmap parameters.
* **Multiplayer pivot:** authoritative server vs. lockstep vs. rollback netcode; chosen after SP stabilizes.
* **AI flavor:** BT vs. Utility vs. GOAP hybrid; authoring DSL selection.
* **Audio synthesis depth:** built-in synthesis vs. sample-based pipeline.

Each unknown has an **Assumption** (initial pick), **Experiment** (bounded PoC), **Kill/Keep Criteria**, and **Owner** recorded in ADRs.

---

## 1) Architecture Topology

**1.1 Process Model**

* **Simulation Core (headless .NET)**: ECS, schedulers, buses, persistence, RegionFS, AI, economy, conflict routing.
* **Presentation Host(s)**: Unity adapters (render, audio, input/UI). Optional command-line hosts (server/replay/CI).
* **IPC**: Named pipes or domain sockets; protocol via Protobuf/FlatBuffers; back-pressure and flow control.
* **Dev fusion**: `RUN_INPROC` flag for single-process dev iteration.

**1.2 Module Graph (no back-edges)**

```
Core.dll (ECS, Bus, Contracts, RNG, Schedulers, RegionFS, Persistence, Telemetry)
  ├─ Simulation.Colony.dll
  ├─ Simulation.CRPG.dll
  ├─ Simulation.GrandStrategy.dll
  └─ Services.* (AI Nav, Crafting, Economy, Conflict, L10n)
Engine.Unity.dll (Adapters: RenderIntent->Unity, Audio, Input, Haptics, UI)
Constellation.SDK (Plugin surfaces)
Tooling (Inspector, Replay, Save Doctor, Perf HUD, Blueprint Studio)
```

* Rungs of the **Genre Ladder** map 1:1 to Simulation.\* modules; state sharing through versioned events/components only.

**1.3 Versioning & Compatibility Domains**

* **Core API**, **Save Schema**, **SDK Contracts**, **Plugin API**, **Content Data** each bump independently; boot gates check compatibility and instruct auto-migrations.
* **Save-Compat Matrix** tested in CI across all supported versions.

---

## 2) Data Model, Time & Math

**2.1 ECS**: Entities=GUIDs; Components=POD structs (SoA storage); Systems=stateless logic with declared R/W sets.

**2.2 Scheduling**: IoC compiles **job DAG** each tick. Scheduler parallelizes non-conflicting jobs; budget hints (ms) and barrier phases (Physics→AI→Economy→Sync).

**2.3 Time Domains**

* **Sim Time** (fixed tick; pause/ffwd); **Meta Time** (real-time with away-time resolver). Meta-time is monotonic (+ signed hints) to prevent spoofing.

**2.4 Determinism Kit**

* SeededRandom with per-system streams; verboten non-deterministic APIs in Sim; platform-stable math paths for critical code; periodic checksums; **deterministic replay** baseline.

**2.5 Precision & Coordinates**

* **Floating Origin** with region-local coordinates; origin rebasing at barriers.
* Precision strategy: `double` for world transforms & economy; `float` or fixed-point for hot loops (configurable by system).
* Physics sub-stepping window and epsilon policy documented per system.

---

## 3) Communication Layer (Events & Commands)

**3.1 Contracts & Evolution**: DTOs are versioned with schema IDs. Translators upcast old versions on load and at bus boundaries.

**3.2 Semantics**: Single-tick delivery inside Sim; priority classes (critical vs. cosmetic); bounded queues; back-pressure; slow-subscriber detection; tracing per topic.

**3.3 Game-Specific Contracts**

* **Resolution Engine Router**: Listens to `ConflictDeclared` (participants, scale, terrain, tech), selects engine (TBT/TD/Auto-battler/TBS) based on thresholds; emits `ConflictResolved` with deterministic summary. Includes **deterministic downsampling** for replays.
* **AgencyBudgetUpdated**: Global resource changes broadcast for UI/AI; capability-filtered for plugins.
* **UnlockSignal/BCIBandwidthChanged**: Meta progression gates; used by Presentation to surface new affordances.

---

## 4) Persistence & Forensics

**4.1 Event-Sourced Saves**: Append-only **World Journal** segmented by RegionID + periodic **Snapshots** for fast load. Snapshot formats are versioned.

**4.2 Durability**: Double-write, CRC, fsync policy, periodic scrubbing, shadow backups, compaction schedule.

**4.3 Security & Privacy**: Optional encryption-at-rest for saves; user-consent gates for telemetry bundles.

**4.4 Save Doctor & Recovery**: Detect and quarantine bad segments; forward/back replay; partial world load; integrity reports with suggested fixes.

**4.5 Diagnostic Bundles**: One-click zip (logs, journal tail, snapshot, replay seed, perf traces). **Crash-to-Replay** auto-emits bundles on unhandled exception.

**4.6 Cloud Sync (optional)**: Content-addressed snapshot + journal tails; conflict resolution rules; offline-first.

---

## 5) Planet-Scale Streaming (RegionFS)

**5.1 Layout**: `(worldId/LOD/regionX/regionY)` directories; columnar component blobs; local journal per region.

**5.2 Prefetch/Hydration**: Camera velocity + sim forecasts prefetch neighbor regions; entities spawn minimal then hydrate lazily.

**5.3 Eviction**: Heat-based (recency/frequency) + memory budgets; cold compaction and defrag passes.

**5.4 Terrain & Nav Data**: Clipmapped terrain/voxels per LOD; navmesh tiles & flow fields streamed alongside components; rebuild budgeted per frame.

**5.5 Content Addressing**: Region blobs hashed for dedupe, caching, reproducibility.

---

## 6) Presentation Boundary (Unity)

**6.1 RenderIntent**: Pure data for tiles, impostors, overlays, decals, cross-sections; adapters map to Unity; **no rules** in Presentation.

**6.2 Snapshot Sync**: Copy-on-write snapshots at frame fences; **Truth Overlay** renders from snapshot for desync hunts.

**6.3 Accessibility & UX**: Color-blind palettes, scalable fonts, input remap, readable pacing; **Micro-Goals** surfacer for 10–15 min sessions; haptics pipeline.

**6.4 Localization**: Full L10n/I18n pipeline; ICU message format; directionality; font fallback; number/date units; hot-reload of strings.

**6.5 Input & Replay**: Input is event-sourced; replays inject input streams with exact timing.

---

## 7) Modularity, Plugins & Mods

**7.1 SDK Surfaces**: Component/event schemas, command handlers, content importers, UI meta hooks, audio hooks.

**7.2 Capability Manifests**: Declare read/write component sets, topics, quotas; loader enforces at runtime.

**7.3 Security**: Plugin signatures verified at load; **WASM sandbox** option (WASI subset) with CPU/mem quotas; no FS/network unless granted.

**7.4 Distribution**: Versioned plugin packages; compatibility matrix; channel policy (stable/beta/experimental); crash quarantine for bad plugins.

**7.5 Moderation & Policy**: Content policy hooks; manifest metadata (author, license, age rating); report/disable pipeline.

---

## 8) AI & Pathfinding

**8.1 Agent Architecture**: Pluggable BT/Utility/GOAP hybrid; authoring DSL with visual inspector; deterministic random streams per agent.

**8.2 Navigation**: Hierarchical pathfinding (navmesh tiles + HPA\*), flow fields for mass movement, local steering (ORCA/RVO) with deterministic fallback.

**8.3 Knowledge & Perception**: Blackboard components; sensory systems with update budgets; LOS queries batched via job graph.

---

## 9) Physics & Constraints

**9.1 Deterministic Physics**: Fixed-step solver with system-defined substeps; integration choice documented; shared epsilon policy.

**9.2 Collision/Queries**: Broadphase structures per region; narrowphase budgeted; queries cached per tick for re-use by AI.

**9.3 Constraint Systems**: Joints and resource constraints solved deterministically; rollback-safe states for replays.

---

## 10) Audio Architecture

**10.1 Event-Driven Audio**: Audio is driven by events & state probes; **IAudioEventSource/IAudioSynthesisHook** for diegetic music systems.

**10.2 Mixing & Latency**: Budgeted mixer graph; latency targets; audio determinism where it affects gameplay.

**10.3 Assets & Synthesis**: Hybrid pipeline (samples + optional synthesis); loudness normalization; L10n of VO pipeline (future).

---

## 11) Content Pipeline (Config‑as‑Code)

**11.1 Author→Import→Bake**: CSV/JSON→importers→codegen’d structs → binary blobs (no reflection in hot paths).

**11.2 Validation**: Schemas, referential integrity, rule/property tests (e.g., conservation laws, domain bounds).

**11.3 Hot-Reload (Safe)**: Stage into shadow world; transactional swap at tick barrier; audit logs of diffs.

**11.4 Idea Alchemy Grammar**: Typed slots (\[Material]+\[Method]+\[Concept]) generate Recipes/Practices/Tech with validation.

**11.5 L10n Pipeline**: Extraction, pseudo-loc, font coverage tests; right-to-left support.

**11.6 Build Reproducibility**: Content-hash addressing; hermetic builds; cache keys; provenance (SBOM for data).

---

## 12) Observability & SRE

**12.1 Metrics**: Tick time, system budgets, allocation churn, queue pressure, region churn, hydration time, nav build time.

**12.2 Logs & Traces**: Structured logs; topic traces; sample rates; PII-free policies.

**12.3 Flight Recorder**: Rolling buffer of events/commands; spill to disk on crash or on-demand.

**12.4 Perf HUD & Inspector**: On-screen HUD; **World Inspector** with ECS browser, time-scrubber, event waterfall, "what changed this tick?" diffs.

**12.5 Incidents**: Severity levels, capture bundles, RCA template, replay-linked bug tickets.

---

## 13) Security, Privacy & Supply Chain

**13.1 Threat Model**: Mod abuse, malformed content, save corruption, tamper, impersonation of plugins, telemetry leaks.

**13.2 Controls**: Sign all builds; verify plugin signatures; capability gates; WASM sandbox; integrity checksums; optional save encryption.

**13.3 SBOM & SLSA**: Generate SBOM; pinned dependencies; reproducible CI builds; provenance attestations.

**13.4 Compliance Hooks**: GDPR/CCPA data exports & delete; age‑gated content flags; offline-first crash reporting.

---

## 14) Performance Targets & Hardware Tiers

**14.1 Tiers**: Min/Rec/Ultra profiles (CPU, RAM, GPU).

**14.2 Budgets**: Sim 8 ms / Render 8 ms on Rec; per-system budget reporting; memory caps per region/entity class.

**14.3 Feature Detection**: CPU SIMD, GPU features; graceful fallbacks; impostor paths for low-end.

**14.4 Scalability Matrix**: Resolution/LOD/AI density toggles bound to Agency/BCI gates where applicable.

---

## 15) Networking Readiness (Future)

**15.1 Modes**: Single-player canonical; optional future MP with **lockstep** or **rollback** or **server-authoritative**. Choose based on prototype KPIs.

**15.2 Contracts**: Deterministic input streams; snapshot deltas; authority and anti-cheat baselines (validation hooks).

**15.3 Replay/Net Convergence**: Replays double as net-sim validation vectors.

---

## 16) Governance & Process

**16.1 ADR/RFC**: Lightweight ADRs for architectural choices; RFC gate for contract changes.

**16.2 Branching & CI**: Trunk-based with short-lived branches; green main enforced; mutation tests for critical code.

**16.3 Release Packages (RPs)**: RP-0..N map to vertical slices; per-RP gates: replay suite, migrations, SBOM, perf budgets.

**16.4 Licensing**: Third-party license audit; compatible licenses for mods; contributor license statement for community content.

**16.5 Issue Triage**: Severity rubric; reproduction via replay seed; SLA for hotfix path.

---

## 17) Risk Register & Contingencies (Signals → Mitigations)

* **Determinism drift** → replay diffs + checksum alarms → bisect via golden scenarios.
* **Save corruption** → Save Doctor quarantine + shadow backups → guided repair wizard.
* **Region thrash** → heatmap tuning + cache sizing tool → prefetch heuristics tests.
* **Plugin crash** → sandbox/process isolation → quarantine on next boot.
* **Perf regression** → KPI thresholds in CI → automatic perf bisect.
* **Design sprawl** → ADR/RFC gate + capability manifests → periodic architecture reviews.
* **Localization regressions** → pseudo-loc CI job → string coverage gates.
* **Security incident** → plugin signature revocation list → incident response runbook.

---

## 18) Roadmap — Release Packages (RPs)

**RP‑0 Seed & Word:** Two-process skeleton; ECS/Bus/IoC; HeatDissipation + DebugRender; snapshot+journal v1; replay harness.

**RP‑1 World From Above:** RegionFS baseline; async hydration; prefetch/eviction; Save Doctor.

**RP‑2 Step Into the World:** Perf HUD, World Inspector, Flight Recorder; property tests; 12‑hour soak.

**RP‑3 Open the Workshop:** Constellation.SDK alpha; capability manifests; plugin signatures; WASM sandbox stub; Blueprint Studio (basic).

**RP‑4 Five Views & Fidelity:** Tactical→Global adapters; Fidelity Ladder; Micro-Goals surfacer.

**RP‑5 Conflict Engines:** Resolution Router; TBT/TD/Auto-battler baseline; deterministic downsampling.

(Future RPs: lineage depth, economy scale, music maker, net-ready prototype, etc.)

---

## 19) Done Definitions

**Per PR:** determinism lint clean; telemetry added; perf budget met; tests (unit/integration/property); ADR attached if schemas/contracts touched.

**Per Release:** migrations green; replay & golden scenarios green; save-compat matrix updated; SBOM & provenance generated; diagnostics bundles verified; plugin signatures validated.

---

## Appendices

**A. ADR Template** — What/Why/Alternatives/Tradeoffs/Migrations/Impact/Owner.

**B. Schema Registry** — ID assignment, deprecation policy, compat test matrix, migration authoring.

**C. Capability Manifest Spec** — allowed components/events/commands, quotas, permissions, signatures.

**D. RegionFS** — paths, blob formats, compaction schedule, hashing strategy.

**E. Replay Bundle** — seed, inputs, checksums, timeline markers, compression.

**F. Threat Model** — assets, attack surfaces, controls, test scenarios.

**G. Backup/Restore Runbook** — cadence, retention, verification drills.

**H. Accessibility & L10n Guide** — WCAG targets, pseudo-loc, font coverage.

**I. Perf Playbook** — profiling steps, budget dashboards, regression triage.

**J. HW Matrix** — CPU/GPU/OS coverage, feature flags, fallback policy.
