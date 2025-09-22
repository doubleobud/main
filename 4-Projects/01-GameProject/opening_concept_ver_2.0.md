# opening\_concept\_ver\_2.0 — Witness/Integrator, Post‑Apoc Bunker Edition

> A comprehensive, implementation‑ready concept scaffold that preserves **authentic historical progression**, uses **real products/people/events** descriptively (no copied assets/code), and frames the experience via a **post‑apocalyptic archival bunker**. No BCI elements.

---

## 0) North Star

* **Premise:** An 8‑year‑old prodigy in **1970** grows alongside computing and video games, absorbing every tiny advance and translating the **concepts** (not assets/code) into a private, lifelong **simulation**.
* **Player Lens (Future):** Decades later, the player explores an **archival bunker** where era‑sealed builds are preserved exactly as they were, with layers of later extensions mounted on top.
* **Design Axiom:** **Extend, never scrap.** Earlier shells remain intact; new capabilities mount as strata you can toggle/observe.
* **Divergence Gate:** Track real history closely until \~**2000**, then gradually branch into an alternate trajectory.

---

## 1) Canonical Rules (Non‑negotiables)

1. **Era Seal:** Each playable slice is locked to its year’s constraints (I/O, memory, storage, display, toolchain). The **bunker UI frames** but never enhances a sealed run.
2. **Witness/Integrator:** Real products/people/happenings appear factually. We **re‑implement ideas** and interfaces in our own stack—never original assets or code.
3. **Extend‑Only Architecture:** Every added capability is a new layer. We don’t rewrite prior semantics; we **compose**.
4. **Receipts & Provenance:** Every major step includes a **receipt** (magazine clipping, badge, terminal account, parts invoice) and updates a **serial number** in saves for lineage.
5. **Legible Granularity:** Each unlock adds **1 marquee capability** + up to **2 QoL tweaks** and updates a **constraint ledger** of what still isn’t possible.
6. **Determinism & Tests:** Turn‑based core with property‑based tests for stepping, RNG, conflict resolution, and migration.
7. **Legal Guardrails:** Descriptive use of trademarks; no copied assets/text/code; rename when dramatizing; avoid defamatory depictions of living individuals.

---

## 2) World Premise & Minimal Post‑Apoc Context

* **Backdrop:** Cycles of crisis in late 20th/early 21st century (pandemics, resource shocks, governance failures) erode archives and infrastructure.
* **Family Lineage:** Grandfather → Father → **You (1970 prodigy)** maintain a habit of preserving builds, logs, and hardware against instability.
* **Bunker Genesis:** A practical **archive‑lab**: underground concrete, conditioned racks, tape libraries, terminals, notebooks.
* **Why It Matters:** Much primary material is lost topside. The bunker houses a uniquely complete **computing/gaming culture record** and your evolving sim.
* **Player Arrival (Future):** The player is a custodian/legatee/discoverer charged with continuing the project and deciding how to diverge post‑2000.

---

## 3) Player Experience

### A) Bunker Hub (Exploration & Instrumentation)

* **Rooms:** Intake, Power, Cooling, Tape Vault, Terminal Row, Workshop, Map Room, Instrument Lab (profilers/oscilloscope UI), Dark Room (secret logs), Archive Gallery.
* **Progression:** Upgrades expand power/cooling, unlock shelves, unseal rooms, activate analyzers. **Receipts Wall** displays found provenance artifacts.
* **Interactions:** Boot sealed builds; run diagnostics; mount extensions; read logs; annotate Codex entries; archive/export run data.

### B) Simulation Runs (Era‑Sealed)

* **Loop:** Boot era build → complete **concept showcase** scenario → earn **Developer Log** → unlock next capability (if prerequisites met) → update **constraint ledger** → repeat.
* **Constraints:** Strict budgets on memory/IO/compute; era‑accurate UI affordances; no forward‑era features.

### C) Knowledge Systems

* **Developer Logs:** Era‑dated documents that bridge real‑world inspiration → abstraction → translation plan → patchlist → receipts → ledger update.
* **Codex:** Two lanes: (1) factual history of computing/games; (2) internal sim design notes. Cross‑links between logs, receipts, and scenarios.
* **Secret Logs:** Off‑path unlocks (hidden caches, false walls, coded labels) revealing deeper family history and optional shortcuts.

---

## 4) Developer Log — Template (Fill‑in‑the‑Blank)

* **Header:** `[Year‑Code] Title` (e.g., `1970‑A Paged Output`)
* **What I Studied (Factual):** Real product/event/idea observed; short note + source magazine/journal/club/program.
* **Abstraction (Idea):** The concept extracted (e.g., “paged output with ‘MORE’ prompt”).
* **Translation Plan (My Sim):** Data structures, interfaces, budgets.
* **Patchlist:** **1 marquee** capability + up to **2 QoL** tweaks; include byte/cycle/IO estimates.
* **Receipts:** Physical/digital proof (scan/photo/text snippet) + location in bunker.
* **Constraint Ledger Update:** What remains impossible and why.

> **Unlock Rule:** Applying this log’s patch enables the capability if power/memory/parts preconditions are satisfied.

---

## 5) Receipts System (Provenance Mechanics)

* **Types:** Badges, letters, terminal slips, invoices, magazine clippings, photos, part labels, code printouts (non‑copyright), schematics.
* **Acquisition:** Found in rooms/caches; rewarded from scenarios; assembled from fragments; restored in the Workshop.
* **Function:** Authenticate presence/influence; gate some logs; decorate the Archive Gallery; enrich Codex entries.

---

## 6) Constraint Ledger (Player‑Visible)

* **Format:** A table per era build: **Can Do / Cannot Do / Budget** (bytes, cycles, IO ops), **Why Not**, **Paths to Enable** (references to logs/parts/rooms).
* **Purpose:** Makes authenticity legible; motivates next unlock; prevents feature confusion.

---

## 7) Serial Number Scheme (Save/Run Provenance)

* **Structure:** `YY‑Track‑Run‑Variant` (e.g., `70‑A1‑03‑b`) where:

  * `YY` = start era; `Track` = path within era ladder; `Run` = attempt index; `Variant` = optional flags (secret paths, modifiers).
* **Use:** Gates certain logs; enables reproducibility; helps with migration and analytics.

---

## 8) Persistent Clock Semantics

* **Bunker Time:** Real‑time or scheduled cadence; gates room resets, shipments (parts), and archival climate cycles.
* **Sim Time:** Turn‑based; compresses time within scenarios; never drifts from determinism guarantees.
* **Events:** Some logs/receipts only surface under specific clock windows (e.g., nightly indexing).

---

## 9) Architecture (Extend‑Never‑Scrap)

* **Strata:**

  * **S0 — Shell:** Period UI + IO behavior preserved as reference implementation.
  * **S1 — Adapters:** Thin shims enabling new capabilities without mutating S0 contracts.
  * **S2 — Services:** Parsers, schedulers, storage, pathing, report engines.
  * **S3 — Instruments:** Profilers, tracers, exporters; observe‑only.
* **Contracts:** New layers must declare **budgets**, maintain **determinism**, register **capability flags**, and pass **property‑based tests**.
* **Event Sourcing & Migration:** Versioned state; “content archaeology” keeps all prior runs loadable under new executables.
* **Capability Flags:** Era gates flip features on/off; bunker toggles allow comparison runs.

---

## 10) UI/UX Evolution (Era‑Accurate)

* **Phase A — TTY/ASCII:** Fixed grid, paged output, status lines, command grammar; minimal glyph charts.
* **Phase B — Richer TUI:** Split panes, scrollback, forms, cursor addressing, inline charts.
* **Phase C — Proto‑GUI:** Windows/icons/pointers where historically plausible; mouse support emerges; better visualization of sim internals.
* **Usability Principle:** Every unlock explicitly states “what changed this era” in both visuals and interaction.

---

## 11) Capability Ladder (Early 1970s – example micro‑roadmap)

> Each notch = **1 marquee** capability + ≤ **2 QoL** tweaks + **Receipt** + **Ledger Update**.

* **1970‑A — Paged Output**
  *Marquee:* Paged output with `MORE` prompt.
  *QoL:* Fixed‑width status line; command queue.
  *Receipt:* TTY usage guide.
  *Ledger:* No scrollback; no persistence.

* **1971‑A — Line Editing**
  *Marquee:* Input buffer with backspace, re‑type.
  *QoL:* History(5); minimal validation.
  *Receipt:* Lab terminal settings slip.
  *Ledger:* No random access storage; no NPC ticks.

* **1972‑A — Tape Persistence**
  *Marquee:* Save/load tiny worldstate to tape.
  *QoL:* Integrity checksum; two save slots.
  *Receipt:* Parts invoice for reels.
  *Ledger:* No structured files; world size cap.

* **1973‑A — Split‑Pane TUI**
  *Marquee:* Log pane + command pane.
  *QoL:* Inline glyph chart; simple form prompts.
  *Receipt:* Panel layout workshop flyer.
  *Ledger:* Limited cursor addressing.

* **1974‑A — Parser Verbs**
  *Marquee:* LOOK/GET/USE/INV with aliases.
  *QoL:* Room link cache; noun disambiguation hint.
  *Receipt:* Verb taxonomy notebook page.
  *Ledger:* No complex AI; limited object states.

* **1975‑A — Turn Scheduler**
  *Marquee:* NPC ticks with budgets; event queue.
  *QoL:* Fast‑step empty turns; tick profiler.
  *Receipt:* Printout with cycle counts.
  *Ledger:* No pathfinding; no multi‑map streaming.

*(Continue through late ’70s/’80s/’90s by repeating the same rhythm; bind each notch to a specific real‑world product/event observed, then translated.)*

---

## 12) Scenario Pattern (per Unlock)

* **Setup:** Short flavor text + receipt discovery.
* **Objective:** Use the new capability in a constrained task.
* **Observation:** Instruments reveal the performance/limits.
* **Reflection:** Log adds an anecdote about the historical inspiration.
* **Outcome:** Unlock next log; ledger updates.

---

## 13) Legal & Ethical Posture (Built‑in)

* **Use factual names** of products/companies/people descriptively; avoid implying endorsement/ownership.
* **No copying** of original code, art, or text (e.g., *Colossal Cave Adventure* passages).
* **Mechanics ≠ Copyright:** We can emulate **ideas** (two‑word parsers, paddle‑ball physics, dungeon topology) with original implementations.
* **Living People:** Avoid defamatory alternate histories; when dramatizing beyond facts, use **renamed analogs**.
* **Trademarks:** Don’t use marks in titles/marketing as if ours; descriptive references in‑story are fine.

---

## 14) Bunker — Physical & Progression Design

* **Power/Cooling:** Limited at start; expansion milestones increase stable uptime and allow multi‑rig runs.
* **Rooms/Gates:** Keypad doors, degraded shelves (need restoration), jammed tape robots.
* **Discovery:** Secret wall panels; mislabeled crates; cryptic shelf codes; sparse map that fills as you explore.
* **Hazards:** Moisture risk, magnetic exposure zones, failing capacitors (fictionalized but grounded).
* **Instruments:** Logic analyzer UI; tape indexer; thermal map; byte/IO budget dashboard.

---

## 15) Opening Sequence (Rewritten; no BCI)

**On first boot, the player is bringing a dormant archive system back online. Feature unlocks are shown as system messages while a curator voice provides context.**

**System Messages (diegetic):**

```
SYSTEM
ARCHIVE POWER BUS: STABLE
COOLING LOOP: NOMINAL
TERMINAL GRID: ONLINE
BLOCK TEXT RENDERER: ACTIVE
STATIC LINE NAVIGATION: READY
```

**Curator Voice (text):**

> Welcome to the archive. These first minutes are always spare—one component at a time. We’ll start with the basic text grid; we’ll gain more affordances as subsystems warm.

**Unlock Beats:**

* `SPACE CHARACTER: ENABLED` → “You don’t appreciate a space until you’re without one.”
* `PUNCTUATION SET: LOADED` → “Now we can talk like humans, not teletypes.”
* `LOWERCASE GLYPHS: AVAILABLE` → “A small luxury from a time when each byte mattered.”
* `WORD PRINTING: ACTIVE` → “Faster than letter‑by‑letter; still era‑true.”
* `SCROLLBACK BUFFER: INITIALIZED` → “Careful—scrollback was a luxury in the early days.”
* `SAVE MODULE: ONLINE` → “Two slots only for now; tapes are temperamental.”

**Choice Prompt:**

> This archive is yours to tend. You can walk the decades exactly as they were, or you can push ahead once we cross into the 2000s. Either way, we never discard—we observe, we extend.

---

## 16) Production Roadmap (Skeleton)

* **M0 — Archive Boot & Bunker Shell**: Basic grid UI, receipts wall, codex seed, constraint ledger UI.
* **M1 — 1970–1972 Ladder**: Paged output; line editing; tape save/load; two showcase scenarios.
* **M2 — Logs Graph & Secret Paths**: Dependency visualization; first hidden cache; provenance UI polish.
* **M3 — 1973–1975 Ladder**: Split‑pane TUI; parser verbs; scheduler; migration proofing.
* **M4 — Instruments & Analytics**: Profiler/tracer; performance dashboards; run diffing.
* **M5 — 1976–1980 Ladder**: Early networking concepts; richer file structures; bigger scenarios.
* **M6+ — Continue cadence**: +1 era slice, +1 marquee capability, +1 narrative receipt per cycle; prepare divergence groundwork approaching \~2000.

---

## 17) Open Questions

* Ideal **granularity** per year (how many notches before fatigue)?
* When to surface **real product names** vs. analogs (per scene guidelines)?
* How explicit to make **family backstory** early vs. letting secret logs reveal it gradually?
* Boundaries for **hacking seams** so they feel sanctioned yet risky.
* Balance between **bunker chores** (power/cooling maintenance) and narrative momentum.

---

## 18) Risks & Mitigations

* **Scope Creep:** Lock the 1‑marquee‑capability rule; avoid feature bundles.
* **Authenticity Fatigue:** Use receipts & ledger to keep progress legible and meaningful.
* **Legal Risk:** Keep code/assets original; rename when dramatizing; avoid defamatory claims about living people.
* **Save Fragility:** Invest early in migration tests and event‑sourced state.

---

## 19) Success Criteria

* Players can articulate **what changed** at each notch and **why** it mattered historically.
* Old runs remain loadable; **compatibility** feels magical, not brittle.
* The bunker reads as a **real place** with believable constraints and history.
* Curiosity sustains through decades—each unlock is small, legible, and satisfying.

---

### Appendix A — Developer Log Quick‑Fill

```
[YYYY‑Code] Title
What I Studied (Factual):
Abstraction (Idea):
Translation Plan (My Sim):
Patchlist: 1 marquee + up to 2 QoL (with budgets)
Receipts: [type, location]
Constraint Ledger Update:
Prereqs (Power/Memory/Parts):
```

### Appendix B — Receipt Types (Examples)

* Homebrew club flyer; ARPANET node list; terminal account slip; part invoice; conference badge; photo of prototype; notebook page (diagram);
* Magazine clipping (review/ad); repair log; mislabeled crate tag.

### Appendix C — Serial Number Spec (Example)

* `YY‑Track‑Run‑Variant` with optional suffixes: `S` (secret path), `X` (experimental), `D` (divergence‑era feature). Example: `75‑B2‑07‑S`.

### Appendix D — Capability Matrix (Starter Outline)

* **Display:** grid → panes → windows → sprites
* **Input:** queued commands → line edit → forms → mouse
* **Storage:** none → tape → files → indexed DB
* **Logic:** single loop → event queue → scheduler → AI ticks
* **Networking:** offline → local interconnect → timesharing → internet‑like
* **Visualization:** raw text → glyph charts → inline graphs → map views
