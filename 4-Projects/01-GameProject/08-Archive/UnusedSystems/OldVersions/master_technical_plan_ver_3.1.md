Of course. Here is the Master Technical Plan v3.1, which reintegrates the detailed principles, processes, and specific systems from v2.0 and its enterprise upgrades into a single, comprehensive document. The original structure and intent have been preserved, with the missing items added to their logical sections.

***

# Project Constellation: Master Technical Plan v3.1

## Part I: Core Philosophy & Guiding Principles 📜

This document outlines the definitive architectural blueprint for Project Constellation. It is founded on a philosophy of **over-engineering for quality**, prioritizing the project's 50-year lifespan over short-term development velocity.

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

* **Entity:** A simple, unique identifier (an ID). It is an empty container representing a "thing" that exists.
* **Component:** **Pure data**. A component is a block of variables describing a single aspect of an entity (e.g., `Position`, `Health`). Components contain **zero logic**.
* **System:** **Pure logic**. A system is a function that operates on all entities possessing a specific set of components.
* **Performance Model:** The ECS will be an **Archetype ECS with a job graph**. The IoC container builds a dependency graph from systems' declared data inputs/outputs each tick, allowing a scheduler to run non-conflicting jobs in parallel.

### Layer 1: The Communication Layer (Event & Command Bus)

This is the central nervous system of the architecture, ensuring systems remain decoupled.

* **Event Bus (Pub/Sub):** When a system's action has consequences, it publishes an **Event** (a data object describing what *has happened*). Other systems can subscribe to these events and react independently.
* **Command Bus:** To separate intent from execution, systems issue **Commands** (requests for an action to be *performed*). Each command has exactly one handler system responsible for its logic.
* **Scaling & Observability:** The bus will be monitored for queue length and drop rates, with detection for slow subscribers. It will also support **priority classes** to distinguish simulation-critical messages from cosmetic ones.

### Layer 2: The Construction Layer (Dependency Injection & IoC)

This layer manages how systems are built and connected, eliminating hidden dependencies.

* **Inversion of Control (IoC) Container:** At startup, a central IoC container constructs all services and systems, automatically **injecting** required dependencies into each system's constructor.

### Layer 3: The Structural Layer (Plugin/Module Architecture)

The "Genre Ladder" is physically enforced by compiling the code into separate, independently compiled modules (DLLs/Assemblies).

* **`Core.dll`:** Contains only the absolute essentials: the ECS framework, bus interfaces, and universal components. It has no knowledge of any specific game genre.
* **`Genre.dll` (e.g., `CRPG.dll`, `ColonySim.dll`):** Each major gameplay layer is its own module. It can only reference `Core.dll`, enforcing perfect decoupling via a **strict module graph with no back-edges**.

### Layer 4: The Persistence Layer (Serialization & Migration)

This is the "time capsule" of the architecture, ensuring data survives forever through an **event-sourced model with snapshots**.

* **Event-Sourced Journal:** The canonical state is an append-only **world journal** of events. This allows for rollbacks and time-travel debugging. For fast loads, periodic **snapshots** of the compact state are generated.
* **Migration:** Upon loading, the system checks the data version. If it's an old version, a series of pre-written migration scripts are executed to upgrade the data structure to the current one, ensuring no save file is ever invalidated.
* **Durability:** Save integrity is paramount, enforced via **double-writing with checksums**, background scrubbing for corruption, and automated shadow-backups.

### Layer 5: The Presentation Layer (Engine Abstraction)

This layer defines the strict boundary between the simulation and the game engine, which are run as **two separate processes** (a headless Simulation Core and a Presentation Host).

* **Thin Adapters Only:** The Presentation Host reads **RenderIntent** components (pure data) and maps them to engine objects. **No game logic resides in the presentation layer**.
* **The Border:** A small, isolated layer of code translates the simulation's state into specific engine commands, typically passing data via copy-on-write snapshots at frame boundaries to avoid locks.

### Layer 6: The Quality Layer (Automated Testing & Concurrency)

This is the non-negotiable safety net that guarantees stability. While this layer defines the principle, the full strategy is detailed in Part IV.

* **Automated Testing:** A comprehensive suite of tests is maintained, including Unit Tests and Integration Tests.
* **Concurrency by Design:** Because systems are inherently decoupled via the job graph, the architecture is designed for parallel execution from the start.

---

## Part III: Implementation Strategy & Workflow ⚙️

These are the practical, day-to-day rules for development.

* **The Bootstrap:** A single `SimulationHost.cs` script serves as the game's sole entry point. It programmatically loads all blueprints, has the IoC container build the systems, and starts the main simulation loop.
* **The Role of the Editor:** The engine's Inspector is an indispensable **live diagnostic and debugging tool**. It is a **read-only** window into the running simulation. It will **never** be used as a source for defining canonical game data.
* **Content Pipeline:** The official content pipeline follows a three-stage process: **Authoring** (in human-readable files like CSV/JSON) → **Importing** (conversion into an intermediate format) → **Baking** (creation of game-ready, high-performance binary blobs and code-generated structs to avoid runtime reflection).
* **Architectural Governance:** Any significant change to the Core API or Save Schema requires a lightweight **Architecture Decision Record (ADR)** or a mini-**Request for Comments (RFC)** process to ensure changes are deliberate and well-documented.

---

## Part IV: Quality & Reliability Strategy 🛡️

This section expands on Layer 6 to detail the advanced strategies for ensuring the project remains stable and performant over decades.

### Advanced Testing Frameworks

* **Deterministic Replay Harness:** Every play session can be recorded as a seed plus an input stream. The CI server replays these nightly to automatically catch any determinism regressions.
* **Property-Based Tests & Fuzzers:** Automated tests will generate vast quantities of valid (and semi-valid) entity sets and action sequences to find edge-case bugs and invariant breaks that human testers would miss.
* **Soak & Chaos Testing:** The CI will run 24-hour "soak" tests to find memory leaks and rare bugs. These runs will include **fault injection** (simulated I/O stalls, bus delays, partial data writes) to validate the system's recovery paths.
* **Golden Scenarios Suite:** A curated set of canonical save files and seeds (e.g., "First Winter," "Succession Crisis") will have their key performance indicators (KPIs) tracked over time to detect gameplay regressions.

### Performance & Budgets

* **Tick Budget:** A strict per-frame budget will be defined (e.g., 8 ms for simulation, 8 ms for rendering on the target spec). Every system must report its time slice, with violations flagged in CI.
* **Memory Budget:** Budgets will be set per region and entity class to prevent leaks. Pull requests will be scanned for heap allocation changes.

### Development Checklists

* **Per-PR Checklist:** Code cannot be merged unless it passes checks for determinism, includes telemetry for new systems, has full unit/integration test coverage, and includes an ADR if it alters a core contract.
* **Per-Release Checklist:** A release cannot be shipped unless all schema migration scripts are tested, the full replay suite is green, the save-compatibility matrix is updated, and a Software Bill of Materials (SBOM) is generated.

---

## Part V: The Path Forward: Milestones 🏁

The development will proceed in two major stages to validate the architecture and then harden it for production.

### Initial Proof-of-Concept Milestone

The very first goal is to implement the simplest possible end-to-end slice of the architecture to prove the core loop.

1.  **Setup:** Implement the IoC container, Event Bus, and the `Core.dll` project structure.
2.  **Blueprint:** Create a `blueprint.json` file defining a single entity with `Temperature` and `Renderable` components.
3.  **Systems:**
    * Create a `HeatDissipationSystem` that reduces the `Temperature` value each tick and publishes a `TemperatureChangedEvent`.
    * Create a `DebugRenderingSystem` that subscribes to `TemperatureChangedEvent` and prints the new value to the console.
4.  **Execution & Persistence:** The `SimulationHost.cs` script will load the blueprint, build the systems, run the loop, and save the entity's final state on close.

### Platform Hardening Milestones (M0-M3)

Following the PoC, these milestones will build out the enterprise-grade features.

* **M0 — Platform Skeleton:** Split the **Simulation Core** and **Presentation Host**. Implement the IoC, typed Bus, SeededRandom service, and job graph. Get the deterministic replay harness running in CI.
* **M1 — Regioned World:** Implement the region file layout, asynchronous entity hydration, and predictive prefetching. Upgrade persistence to full event-sourcing with snapshots and corruption tests.
* **M2 — Observability & Test Suite:** Implement the in-game Perf HUD and flight recorder. Build the property-based test suites and the 12-hour soak/chaos test profile.
* **M3 — Plugin SDK Alpha:** Publish the first version of the `Constellation.SDK` with capability manifests and semantic versioning. Provide an example mod and a stub for the optional WASM sandboxing path.

---

## Appendix A: Target Systems & Components

The following are examples of major systems planned for development within this architecture:

* History & Lineage Engine
* Planet Streaming & Chunking System
* "Maker" Systems (Diegetic Blueprint Studio)
* Top-Down Tile Renderer
* Model Impostor Batcher