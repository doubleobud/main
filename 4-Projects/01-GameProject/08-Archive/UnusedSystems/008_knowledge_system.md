# **Knowledge Management System**

### **Version: 2.2**

### **Date: 2025-08-20**

> **Change summary (v2.2):**
>
> * Formalized **Manifest schema** (machine-readable fields).
> * Added **Retrieval Plan Protocol v0.1** (inputs, scoring, budget, template).
> * Introduced **Quality Gates & Linting** and **Assistant Command Set**.
> * Required **Executive Summary** and **Interfaces & Hand-offs** blocks in frontmatter.
> * Clarified **ID & naming** rules (immutable IDs) and **parent/child dependencies**.
> * Kept directory structure and ontology intact; wording tightened for precision.

---

## **Part I: Core Philosophy**

### **Overview**

This document defines the operating system for knowledge, design, and AI collaboration on the Simulation Universe. It supports a decades-long, modular development effort by a solo developer working with an AI assistant. All design is **documentation-centric** and **manifest-driven**; implementation proceeds **from** these documents, not alongside them.

### **1. Documentation-Centric Architecture**

The canonical source of truth is the documentation itself. GDDs (design intent) and TDDs (implementable specs) are first-class artifacts. Code changes must point to a governing document and update it when behavior changes. The **state of the docs** equals the **state of the project**.

---

## **Part II: The Knowledge Lifecycle**

### **2. Document Lifecycle & Taxonomy**

**Tiers (design lineage):**

* **Tier 1: Domain** — Foundational pillars (e.g., *World Simulation*, *Player Experience*).
* **Tier 2: Module** — Major, self-contained feature areas within a Domain (e.g., *Weather System*).
* **Tier 3: Sub-Module** — Cohesive parts of a Module (e.g., *Hydrological Cycle*).
* **Tier 4: Specification** — Implementable TDD for a single Component, System, or Blueprint.

**Stages (document journey):**

1. **Initialization** → created in `01_Knowledge/01_WORKBENCH/`; add frontmatter; scoped goal.
2. **Expansion** → research, notes, wild breadth; avoid premature structure.
3. **Distillation** → progressive summarization; split into children where needed; wire dependencies.
4. **Graduation** → move to `02_CANON/` (GDD) or `03_IMPLEMENTATION/` (TDD); mark **Official**; archive original.

**Required frontmatter blocks** (additions in v2.2):

* `summary_exec` *(150–300 words)* — an **Executive Summary** for fast AI/context packing.
* `interfaces` *(bullets)* — **Inputs, Outputs, Invariants, Dependencies** (“**Interfaces & Hand-offs**”).
* `id` is **immutable**; `title`, `summary`, and `tags` may evolve.

**Status labels:** `Draft` → `Review` → `Official` (only Official appears in MANIFEST by default; others are opt-in).

---

## **Part III: AI Collaboration Protocol**

### **3. Always-Include Base Context**

Unless the task is purely mechanical, the assistant assumes three baseline docs are relevant:

1. **Vision Statement** (the “why”),
2. **Technical Foundations** (the “how”),
3. **Knowledge System** (this document: the “working rules”).

### **4. Manifest-Driven Context Protocol (Three Steps)**

1. **Briefing (You):** Provide **MANIFEST.md** + today’s task in natural language.
2. **Retrieval Plan (AI):** I propose the exact **document IDs** to load (see policy below).
3. **Context Load (You):** Paste the requested docs; we confirm “**Context locked**” and proceed to produce a GDD/TDD (or implementation plan).

### **5. Retrieval Plan Policy (v0.1)**

**Inputs:** Task text + MANIFEST.
**Targeting:** Detect the task’s **Tier** (Domain/Module/Sub-Module/Spec).
**Candidate set:**

* Title/summary/tag matches;
* * their **parents up to Domain**;
* * all declared **dependencies**.

**Scoring & budget (defaults):**

* **Tier match** (closer to target tier = higher).
* **Tag overlap** (task↔doc).
* **Dependency distance** (parents/children favored).
* **Status** (Official > Review > Draft).
* **Freshness** (latest edit preferred).
  **Budget:** ≤ **12 docs** per plan (can be lowered for tiny tasks).

**Retrieval Plan — Output Template**

```
Retrieval Plan v0.1
Task: <natural-language>
Budget: max 12 docs

A) Must-Load (with reasons)
  - [id] <title> — <reason>

B) Nice-to-Have (load if room)
  - [id] <title> — <reason>

C) Missing/Thin (proposed stubs to create)
  - <YYYYMMDD-type-short-name> <title> — <gap the stub will fill>

Notes: extracted constraints and definitions (from Vision/Tech/KS)
```

### **6. Assistant Command Set (logical “moves”)**

* `propose_retrieval_plan([ids])`
* `request_docs([ids])`
* `draft_spec(parent_id, scope)`
* `flag_conflict(a_id, b_id, note)`
* `propose_stub(id, title, type, parent_id, reason)`

### **7. Quality Gates & Linting (pre-Graduation)**

Before any document graduates to **Official**, the assistant runs checks:

**Linkage**

* Has **parent** (except Domains) and no **orphan dependencies**.
* Dependencies reference **existing IDs**; no cycles, unless explicitly allowed.

**Content**

* Has **Executive Summary** and **Interfaces & Hand-offs**.
* Title is clear; **scope/boundary statement** present.
* Status updated; **owner/date** present or N/A.

**Metadata**

* Valid **id** (immutable, `YYYYMMDD-type-short-name`).
* Tags from approved ontology; no unknown prefixes without rationale.
* File path matches its **type**.

---

## **Part IV: Project Directory Structure**

*(Unchanged in spirit; wording tightened for precision.)*

```
/SimulationUniverse/
├── 01_Knowledge/
│   ├── 01_WORKBENCH/
│   ├── 02_CANON/
│   │   ├── 01_Simulation_Systems/
│   │   │   ├── 01_Spatial_Timebase/
│   │   │   ├── 02_Planet_Atmosphere_Sim/
│   │   │   ├── 03_Ecosystem_Sim/
│   │   │   ├── 04_Resources_Energy/
│   │   │   ├── 05_Production_Crafting/
│   │   │   ├── 06_Settlements_Logistics/
│   │   │   ├── 07_Economy_Governance/
│   │   │   ├── 08_AgentAI_Social/
│   │   │   └── 09_Risk_Conflict/
│   │   ├── 02_Player_Systems/
│   │   │   ├── 01_Modes_Cameras/
│   │   │   ├── 02_Rendering_LOD/
│   │   │   ├── 03_UI_Framework_HUD/
│   │   │   ├── 04_Narrative_Events/
│   │   │   └── 05_Accessibility_Localization/
│   │   └── 03_Platform_Tooling/
│   │       ├── 01_Runtime_Scheduler/
│   │       ├── 02_Persistence_Versioning/
│   │       ├── 03_Modding_API/
│   │       └── 04_Networking_Sync/
│   ├── 03_IMPLEMENTATION/
│   │   ├── 01_Components/
│   │   └── 02_Systems/
│   ├── 04__ARCHIVE/
│   └── 05_MANIFEST.md
│
├── 02_Source/
│   ├── 01_Simulation.Core/
│   ├── 02_Simulation.Blueprints/
│   ├── 03_Simulation.API/
│   └── 04_Simulation.sln
│
├── 03_Engine/
│   └── 01_Unity.Project/
│       ├── 01_Assets/
│       │   ├── 01__Project/
│       │   │   ├── 01_Scripts/
│       │   │   │   ├── 01_Bootstrap/
│       │   │   │   ├── 02_Rendering/
│       │   │   │   └── 03_Editor/
│       │   ├── 02_Art/
│       │   └── 03_Audio/
│       ├── 02_Packages/
│       └── 03_ProjectSettings/
│
├── 04_Universe/
│   ├── 01_WrittenWorks/
│   ├── 02_Cinematics/
│   └── 03_ConceptArt/
│
└── 05_Project/
    ├── 01_Administration/
    ├── 02_Strategy/
    ├── 03_Research/
    ├── 04_Learning/
    └── 05_Journal/


**Directory Rules**

* **01\_Knowledge** is the **design truth**.

  * WORKBENCH = active drafting; CANON = Official GDDs; IMPLEMENTATION = Official TDDs; \_ARCHIVE = retired.
  * **MANIFEST.md** is the machine-readable index used to bootstrap AI work.
* **02\_Source** is engine-agnostic simulation code; **03\_Engine** is Unity (presentation layer only).
* **04\_Universe** and **05\_Project** house creative and operational meta-material, respectively.

DOMAIN BOUNDARY CHEAT SHEET

Spatial & Timebase — Owns units/coords/time; provides transforms & calendars; no rendering.

Planet & Atmosphere Sim — Owns terrain/air/water dynamics; outputs fields/meshes; no visuals.

Ecosystem Sim — Owns populations & interactions; outputs state deltas/events.

Resources & Energy — Owns resource graph & power; outputs network states.

Production & Crafting — Owns recipes/research; outputs jobs, buildables.

Settlements & Logistics — Owns placement/storage/transport; outputs routes/flows.

Economy & Governance — Owns price/tax/contract rules; outputs market events.

Agent AI & Social — Owns goals/utility/skills/groups; outputs actions/requests.

Risk & Conflict — Owns hazards/combat; outputs threats/combat states.

Modes & Cameras — Owns perspectives & camera rigs; calls Rendering/UI.

Rendering & LOD — Owns scene assembly, shaders, LOD; consumes sim data.

UI Framework & HUD — Owns widgets/layout; surfaces sim/player states.

Narrative & Events — Owns event graphs; schedules tasks/goals.

Accessibility & Localization — Owns language packs & access rules.

Runtime & Scheduler — Owns ECS schemas, order, jobs; enforces determinism.

Persistence & Versioning — Owns save schema, snapshots, migrations.

Modding & API — Owns plugin caps, content format, hooks.

Networking & Sync — Owns sync model; optional.

---

## **Part V: The Project Manifest (schema & policy)**

**Purpose:** Single entry point for AI sessions and automation.

**Scope:** By default, include **Official** docs from CANON and IMPLEMENTATION. Optionally include others via a `visibility: included` flag.

**Entry schema (YAML)**

```yaml
- id: "20250820-spec-persistence-fileformat"   # immutable
  title: "Spec: Persistence File Format"
  type: "Specification"                        # Domain | Module | Sub-Module | Specification
  status: "Official"                           # Draft | Review | Official
  summary: "Binary, chunked save format w/ versioning & migrations."
  summary_exec: "150–300 word executive summary here..."
  path: "01_Knowledge/03_IMPLEMENTATION/02_Systems/persistence_fileformat.md"
  parent: "20250820-module-persistence"
  dependencies: ["20250820-module-persistence"]
  interfaces:
    inputs: ["world_state", "time_step"]
    outputs: ["save_blob", "schema_version"]
    invariants: ["forward-compatible", "deterministic"]
  tags: ["doc-tdd","data-serialization","system-ecs"]
  last_modified: "2025-08-20"
  visibility: "included"                       # optional override for non-Official docs
```

**Generation:** MANIFEST is **auto-generated** from frontmatter and validated by the linter. Manual edits are allowed but should be rare and flagged in CI.

---

## **Appendix A: Tagging Ontology**

*(Preserved; minor clarifications.)*

### 1. Knowledge & Design — `doc-*`

Examples: `doc-philosophy`, `doc-gdd`, `doc-tdd`, `doc-lore`, `doc-api-reference`, `doc-postmortem`

### 2. Source & Architecture — `system-*`, `component-*`, `data-*`, `api-*`

Examples: `system-ai`, `system-physics`, `component-inventory`, `data-serialization`, `api-modding`

### 3. Engine Implementation — `engine-*`

Examples: `engine-rendering`, `engine-ui`, `engine-editor-tool`, `engine-performance`

### 4. Universe & Creative — `world-*`, `narrative-*`, `art-*`, `audio-*`

Examples: `world-location`, `narrative-quest`, `art-concept`, `audio-sfx`

### 5. Project Management — `project-*`

Examples: `project-roadmap`, `project-task`, `project-research`, `project-marketing`

### 6. Status & Workflow — `status-*`

Examples: `status-needs-review`, `status-prototype-ready`, `status-blocked`

**Tagging rules:** Prefer **few, durable** tags; add new prefixes only with justification. Tags are part of retrieval scoring.

---

## **Appendix B: Frontmatter Templates**

### **Domain (Tier 1)**

```yaml
---
id: "YYYYMMDD-domain-short-name"
title: "Domain: <Name>"
type: "Domain"
status: "Draft"
summary: "One-sentence purpose."
summary_exec: "<150–300 words>"
interfaces:
  inputs: []
  outputs: []
  invariants: []
dependencies: []
tags: ["doc-gdd"]
---
# Boundary Statement
<what's in / what's out>
```

### **Module (Tier 2)**

```yaml
---
id: "YYYYMMDD-module-short-name"
title: "Module: <Name>"
type: "Module"
status: "Draft"
summary: "One-sentence purpose."
summary_exec: "<150–300 words>"
interfaces:
  inputs: []
  outputs: []
  invariants: []
parent: "YYYYMMDD-domain-short-name"
dependencies: ["YYYYMMDD-domain-short-name"]
tags: ["doc-gdd"]
---
```

### **Sub-Module (Tier 3)**

```yaml
---
id: "YYYYMMDD-submodule-short-name"
title: "Sub-Module: <Name>"
type: "Sub-Module"
status: "Draft"
summary: "One-sentence purpose."
summary_exec: "<150–300 words>"
interfaces:
  inputs: []
  outputs: []
  invariants: []
parent: "YYYYMMDD-module-short-name"
dependencies: ["YYYYMMDD-module-short-name"]
tags: ["doc-gdd"]
---
```

### **Specification / TDD (Tier 4)**

```yaml
---
id: "YYYYMMDD-spec-short-name"
title: "Spec: <Name>"
type: "Specification"
status: "Draft"
summary: "One-sentence purpose."
summary_exec: "<150–300 words>"
interfaces:
  inputs: []
  outputs: []
  invariants: []
parent: "YYYYMMDD-<module-or-submodule-id>"
dependencies: ["YYYYMMDD-<module-or-submodule-id>"]
tags: ["doc-tdd","system-*","component-*","data-*","api-*"]
---
# Problem
# Goals / Non-Goals
# Invariants / Constraints
# Data Model (schemas)
# Algorithms / Control Flow
# API / Messages
# Open Questions / Risks
# Test Plan / Telemetry
# Migration / Back-Compat
```

---

## **Appendix C: Governance & Versioning**

* **Version bump** this document when changing schemas, protocols, or required fields.
* **Changelogs** live at the top; keep terse and actionable.
* **Conflicts** between docs are flagged via `flag_conflict()` and resolved before Graduation.
* **IDs** never change; superseded docs link forward via `superseded_by: id`.

---

## **Appendix D: Linting & Automation**

* **Manifest Generator:** aggregates frontmatter into `05_MANIFEST.md`.
* **Doc Linter:** runs **Quality Gates**, validates frontmatter, path/type alignment, and dependency graph.
* **CI Checks:** block Graduation if gates fail; emits a checklist for fixes.
* **Headless Runs:** optional: nightly “context packs” (subset of Official docs + summaries) for faster AI boot.

---

### **Handshake (operational)**

* **You:** post `05_MANIFEST.md` + “Today’s task: …”
* **Me:** reply with **Retrieval Plan v0.1** (A/B/C).
* **You:** paste Must-Load docs.
* **Me:** “**Context locked**” → deliver GDD/TDD (or impl plan) and run Quality Gates.

---

If you want, I can also generate:

* a **starter MANIFEST.md** conforming to the schema above, and
* a **Doc Linter checklist** you can paste into CI to enforce the gates.
