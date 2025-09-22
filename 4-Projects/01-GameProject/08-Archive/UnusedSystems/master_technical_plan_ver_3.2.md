Of course. Here is the Master Technical Plan v3.2. It incorporates the "ultimate" patch set, merging the clarity and structure of v3.1 with the enterprise-grade hardening and specific subsystems requested. This version is intentionally over-engineered to account for every specified contingency.

***

# Project Constellation: Master Technical Plan v3.2

## Part I: Core Philosophy & Guiding Principles 📜

This document outlines the definitive architectural blueprint for Project Constellation. It is founded on a philosophy of **over-engineering for quality**, prioritizing the project's decades-scale lifespan over short-term development velocity.

* **Longevity over Speed:** All architectural decisions are made in service of scalability, maintainability, and portability for a multi-decade development cycle.
* **Simulation Purity:** The core simulation logic exists as an abstract, engine-agnostic layer. It calculates the "truth" of the universe, completely unaware of how that truth is rendered, heard, or displayed.
* **Decoupling is Paramount:** Systems are fully isolated and communicate indirectly. This prevents a "web" of dependencies, ensuring the project remains manageable as its complexity grows exponentially.
* **Atoms, Not Molds:** The universe is built from **atoms (raw data)**, not from **molds (rigid classes)**. An object's properties and behaviors are defined by the data components attached to it, not by a restrictive inheritance hierarchy.
* **Configuration as Code:** The **canonical source of truth** for all game data, logic, and initial state resides in version-controlled text and data files (e.g., C#, JSON), not in opaque, editor-specific scene files. This ensures that the entire game state is reproducible, diff-able, and auditable.

---

## Part II: The Architectural Blueprint: The Seven Layers 🏛️

The architecture is a stack of seven distinct, interacting layers, each with a specific responsibility.

### Layer 0: The Data Layer (ECS)

This is the foundational model for the entire simulation state.

* **Entity:** A simple, unique identifier (an ID).
* **Component:** **Pure data** with **zero logic** (e.g., `Position`, `Health`).
* **System:** **Pure logic** that operates on entities with specific components.
* **Performance Model:** The ECS will be an **Archetype ECS with a job graph**. The IoC container builds a dependency graph from systems' declared data inputs/outputs each tick, allowing a scheduler to run non-conflicting jobs in parallel.

### Layer 1: The Communication Layer (Event & Command Bus)

This is the central nervous system, ensuring systems remain decoupled.

* **Event Bus (Pub/Sub):** Publishes **Events** (what *has happened*) for zero-to-many subscribers.
* **Command Bus:** Issues **Commands** (what *should happen*) to exactly one handler system.
* **Game-Specific Contracts:**
    * **Resolution Engine Router:** A specialized bus service that listens for `ConflictDeclared` events. Based on conflict scale and type, it routes the conflict to the appropriate genre-specific resolution system (e.g., Auto-Battler, TBS) and publishes a `ConflictResolved` event upon completion. It supports deterministic downsampling of event streams for replays.
    * **Meta/Sim Guardrails:** The bus enforces **Meta-time authority** via monotonic counters and signed hints to prevent clock spoofing. It publishes a core `AgencyBudgetUpdated` event, allowing UI and other systems to react to changes in the player's core resource for actions.
* **Scaling & Observability:** The bus will be monitored for queue length and drop rates, with detection for slow subscribers. It will also support **priority classes** to distinguish simulation-critical messages from cosmetic ones.

### Layer 2: The Construction Layer (Dependency Injection & IoC)

This layer manages how systems are built and connected.

* **Inversion of Control (IoC) Container:** At startup, a central container constructs all services and systems, automatically **injecting** required dependencies.

### Layer 3: The Structural Layer (Plugin/Module Architecture)

The "Genre Ladder" is physically enforced by compiling code into separate modules (DLLs/Assemblies).

* **Strict Module Graph:** A strict dependency graph is enforced: `Core.dll` → `Genre.dll`s → `Engine.dll`, with no back-edges allowed.
* **Plugin Runtime Safety & Sandboxing:** Modularity extends beyond compile-time to runtime containment.
    * **Capability Manifests:** Every plugin must ship with a manifest file declaring the specific components, events, and commands it is allowed to access, read, or write. The plugin loader enforces these gates at runtime.
    * **Signature Checks:** All first-party and trusted third-party plugins must be cryptographically signed. The loader will verify these signatures before loading.
    * **WASM Sandbox:** An optional mode for community mods will run them in a **sandboxed WASM (WebAssembly) environment**. This enforces strict CPU and memory quotas and provides no default access to the file system or network, communicating with the core simulation only via the event bus.

### Layer 4: The Persistence Layer (Serialization & Migration)

This is the "time capsule" of the architecture, ensuring data survives forever.

* **Event-Sourced Journal with Snapshots:** The canonical state is an append-only **world journal** of events, segmented by region. For fast loads, periodic **snapshots** are generated.
* **Schema Registry & Migration:** All data schemas are tracked in a formal **Schema Registry** (see Appendix B). Upon loading old data, pre-written migration scripts are executed to upgrade the structure.
* **Repair & Forensics:**
    * **Save Doctor:** An automated tool that can validate save integrity. It can quarantine corrupted journal segments, allowing the rest of the world to load, and can perform safe forward/backward rollbacks of the event stream to repair state.
    * **Diagnostic Bundles:** The game can generate a one-click export containing logs, a save snapshot, and a replay seed for bug reporting.
    * **Crash-to-Replay:** On an unhandled exception, the engine will automatically package the flight recorder buffer and a minimal replay bundle for post-mortem analysis.

### Layer 5: The Presentation Layer (Engine Abstraction)

This layer defines the strict boundary between the two main processes: the headless **Simulation Core** and the **Presentation Host**.

* **Thin Adapters Only:** The Presentation Host reads **RenderIntent** components and maps them to engine objects. **No game logic resides in the presentation layer**.

### Layer 6: The Quality Layer (Automated Testing & Concurrency)

This is the non-negotiable safety net that guarantees stability. The full strategy is detailed in Part VI.

---

## Part III: Core Subsystems Deep Dive

This section details the design of critical, large-scale subsystems.

### Planet-Scale Streaming: The Region File System (RegionFS)

To handle a planet-scale world, data is not stored in monolithic files but in a specialized region-based file system.

* **Path Layout:** The world is split into a directory structure like `(worldId / LOD / regionX / regionY)`.
* **Columnar Blobs:** Within each region directory, component data is stored in **columnar (Structure of Arrays) binary blobs** instead of row-based (Array of Structures) formats. This allows systems to load only the specific component data they need (e.g., all `Position` components) without reading unrelated data.
* **Asynchronous Hydration:** Entities spawn in a minimal "hydrated" state. Additional, less critical components are streamed in lazily as needed.
* **Prefetching & Eviction:** A predictive prefetcher uses camera velocity and simulation clock forecasts to begin loading neighboring regions asynchronously. An eviction policy based on a "heat map" (recency and frequency of access) and memory budget determines which regions to unload.

---

## Part IV: Implementation & Workflow ⚙️

* **The Bootstrap:** A single `SimulationHost.cs` script serves as the game's sole entry point.
* **The Role of the Editor:** The engine's Inspector is an indispensable **read-only** diagnostic and debugging tool. It will **never** be used to define canonical game data.
* **Content Pipeline:** The official pipeline is **Authoring** (CSV/JSON) → **Importing** → **Baking** (game-ready binary blobs) to eliminate runtime reflection.

---

## Part V: Observability & Tooling

A suite of first-class tools is essential for development and debugging.

* **World Inspector:** A multifaceted diagnostic tool featuring:
    * A filterable ECS browser to inspect entities and components.
    * A time-scrubber to replay and step through the event journal.
    * A "what changed this tick?" diff viewer for granular analysis.
* **Performance HUD (Perf HUD):** An in-game overlay displaying real-time metrics, including tick time, bus queue pressure, region churn, and memory allocations.
* **Flight Recorder:** A rolling in-memory buffer of the last N seconds of all events and commands, which is packaged into diagnostic bundles on crash.
* **Truth Overlay:** A debug rendering mode that draws its data directly from the simulation state snapshot sent to the renderer, allowing for perfect visualization of desyncs between simulation and presentation.
* **Diegetic Tools ("Blueprint Studio"):** In-game "Maker" tools will use the exact same import/bake content pipeline that developers use, ensuring they are a first-class feature.

---

## Part VI: Quality, Security, & Reliability 🛡️

### Advanced Testing Frameworks

* **Deterministic Replay Harness:** Nightly CI runs replay recorded player sessions to catch determinism regressions.
* **Property-Based Tests & Fuzzers:** Automated tests generate massive, varied inputs to find edge cases in complex systems like crafting and lineage.
* **Soak & Chaos Testing with Fault Injection:** Long-duration tests run with simulated I/O stalls, bus delays, and partial data writes to validate system recovery paths.
* **Golden Scenarios Suite:** Curated save files are used to lock down gameplay KPIs and detect regressions.

### Security & Supply Chain

* **Signed Builds & SBOM:** All shipped binaries will be cryptographically signed. Every release will produce a **Software Bill of Materials (SBOM)** to track dependencies.
* **Plugin Verification:** The engine verifies plugin signatures at load time, enforcing the security policies defined in Layer 3.

### Development Checklists

* **Per-PR Checklist:** Code must pass checks for determinism, include telemetry, have full test coverage, and include an ADR if it alters a core contract.
* **Per-Release Checklist:** A release requires tested migration scripts, a green replay suite, an updated save-compat matrix, and a generated SBOM.

---

## Part VII: The Path Forward: Milestones 🏁

* **Initial Proof-of-Concept:** Implement the simple `Temperature` component and `HeatDissipationSystem` to validate the core architectural loop from end to end.
* **Platform Hardening Milestones (M0-M3):**
    * **M0 — Platform Skeleton:** Split the two processes, implement the core IoC/Bus/Job Graph, and stand up the deterministic replay harness.
    * **M1 — Regioned World:** Implement the RegionFS, async hydration, and event-sourced persistence.
    * **M2 — Observability & Test Suite:** Build the Perf HUD, flight recorder, and property-based test suites.
    * **M3 — Plugin SDK Alpha:** Publish the first `Constellation.SDK` with capability manifests and a WASM sandbox stub.

---

## Appendix A: Target Systems & Components

The following are examples of major systems planned for development within this architecture:

* History & Lineage Engine
* Planet Streaming & Chunking System
* "Maker" Systems (Diegetic Blueprint Studio)
* Top-Down Tile Renderer
* Model Impostor Batcher

## Appendix B: Schema Registry Conventions

To ensure persistence and API stability over decades, all versioned data structures (Components, Events, Commands) must adhere to a formal registry.

* **Schema IDs:** Every schema will have a unique, permanent ID that never changes.
* **Semantic Versioning:** Schemas will be versioned. The registry will track compatibility between versions.
* **Deprecation Policy:** A formal policy will govern how fields are deprecated (marked as obsolete, no longer written) and eventually removed in future major versions.
* **Compatibility Tests:** A dedicated suite of tests in CI will verify that migration scripts correctly upgrade data from all previously supported save versions to the current version.