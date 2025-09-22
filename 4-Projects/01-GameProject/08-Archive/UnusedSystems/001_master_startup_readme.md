Yes—everything needed to run the daily boot is in place. You **don’t** need the verbatim sections; the executive summaries plus the Retrieval Plan flow are sufficient because the full docs will be loaded in the **second** chat (Must-Load set). Below is a **final, trimmed Master Kick-Off README** with no fluff and all the operational details, including your **hierarchical numeric naming/ID convention**.

---

```markdown
---
id: "master-kickoff"
title: "Simulation Universe — Master Kick-Off README"
version: "1.0"
status: "Operational"
---

# Quick Start (Daily Flow)
1) Paste **this README only** into a fresh chat.  
2) Assistant replies with **Retrieval Plan v0.1** (Must-Load / Nice-to-Have / Missing).  
3) Open a **brand-new chat** and paste **only** the Must-Load docs (use the paste boundaries below).  
4) Assistant says **“Context locked”** and delivers the requested **GDD/TDD/Implementation Plan**.

**Assistant must reply in this order:**
1) Restated Task  
2) Assumptions & Non-Goals  
3) Retrieval Plan v0.1 (A/B/C)  
4) New-Chat Prompt (one paragraph, ready to paste)

---

# Today’s Task
> Describe the goal in natural language.  
> *(Optional hints: target Family/Domain; deliverable type (GDD/TDD); timebox.)*

---

# Retrieval Plan Protocol (v0.1)
**Inputs:** this README (+ MANIFEST if provided) and Today’s Task.  
**Targeting:** detect task Tier (Domain / Module / Sub-Module / Specification).  
**Candidate set:** title/summary/tag matches **+** parents up to Domain **+** declared dependencies.  
**Scoring:** tier match • tag overlap • dependency distance • status (Official > Review > Draft) • freshness.  
**Budget:** ≤ 12 docs.

**Return format (verbatim):**
```

Retrieval Plan v0.1
Task: <restated task>
Budget: max 12 docs

A) Must-Load (with reasons)

* \[id] <title> — <reason>

B) Nice-to-Have

* \[id] <title> — <reason>

C) Missing/Thin (proposed stubs)

* <YYYYMMDD-type-short-name> <title> — <gap>

Notes: constraints extracted from Vision/Tech/KS

```

**Doc paste boundaries for the next chat:**
```

\=== BEGIN DOC id:<id> === <full markdown including frontmatter>
\=== END DOC id:<id> ===

````

**Manifest fallback (if none is supplied):**
- Treat **Vision**, **Technical Foundations**, and **Knowledge System** as baseline context and propose up to 9 additional candidates based on the task and taxonomy.

---

# Assistant Contract
- `propose_retrieval_plan([ids])`  
- `request_docs([ids])`  
- `draft_spec(parent_id, scope)`  
- `flag_conflict(a_id, b_id, note)`  
- `propose_stub(id, title, type, parent_id, reason)`

---

# Quality Gates (pre-Graduation)
**Linkage:** has parent (except Domains); valid dependencies; no orphans/cycles (unless explicitly allowed).  
**Content:** **Executive Summary (150–300 words)** + **Interfaces & Hand-offs** (Inputs / Outputs / Invariants).  
**Metadata:** immutable `id`; approved tags; file path matches `type`.

**Definition of Done**
- **GDD:** Problem & Player Value • Scope/Boundaries • Core Loops & State • Interfaces & Hand-offs • Open Risks • Exec Summary.  
- **TDD:** Data Model • Systems & Ordering • Algorithms/Control Flow • APIs & Messages • Test Plan & Telemetry • Migration/Back-Compat • Exec Summary.

---

# MANIFEST Entry Schema (machine-readable)
```yaml
- id: "01-02-01-03_ecosystem_sim"              # hierarchical numeric chain + slug (see Naming)
  title: "Spec: Ecosystem Sim – Population Update"
  type: "Specification"                        # Domain | Module | Sub-Module | Specification
  status: "Official"                           # Draft | Review | Official
  summary: "Implements population dynamics update over time."
  summary_exec: "<150–300 words>"
  path: "01_Knowledge/03_IMPLEMENTATION/02_Systems/01-02-01-03_ecosystem_sim.md"
  parent: "01-02-01_ecosystem_sim"            # immediate parent's hierarchical id
  dependencies: ["01-01_spatial_timebase"]    # examples
  interfaces:
    inputs: ["time_step","species_state"]
    outputs: ["population_delta"]
    invariants: ["deterministic_given_seed"]
  tags: ["doc-tdd","system-ecs","data-serialization"]
  last_modified: "YYYY-MM-DD"
  visibility: "included"                      # optional override for non-Official docs
````

---

# Naming & Hierarchical ID Convention (authoritative)

**Purpose:** Every new doc starts with a **hierarchical numeric chain** (numbers joined with hyphens; “kebab on numbers”) followed by `_` and a **snake\_case** slug. This stem is both the **filename** and the immutable **id**.

* **Digits per level:** 2 (e.g., `01`, `02`).

  > If you prefer 3-digit segments (`001`), apply consistently at all levels; rule remains identical.
* **Levels & numbering:**

  * **Family (top level):** `01` Simulation\_Systems, `02` Player\_Systems, `03` Platform\_Tooling
  * **Domain under Family:** `01..99`
  * **Module under Domain:** `01..99`
  * **Sub-Module under Module:** `01..99`
  * **Specification under its parent:** `01..99`
* **Chain:** concatenate ancestor numbers with hyphens, then `_slug`.
* **Increment:** only the **last segment** increments within its parent folder.
* **Frontmatter:** include the full chain in `id` and the parent’s chain in `parent`.

**Examples**

* Domain (second under Simulation\_Systems):

  * File: `01-02_planet_atmosphere_sim.md`
  * `id: "01-02_planet_atmosphere_sim"`
* Module (first under that Domain):

  * File: `01-02-01_atmospheric_fields.md`
  * `id: "01-02-01_atmospheric_fields"`
* Sub-Module (third under that Module):

  * File: `01-02-01-03_ecosystem_sim.md`
  * `id: "01-02-01-03_ecosystem_sim"`
* Spec (fourth under that Sub-Module):

  * File: `01-02-01-03-04_population_update.md`
  * `id: "01-02-01-03-04_population_update"`

**Frontmatter minimum (for any new doc):**

```yaml
---
id: "<numeric_chain>_<slug>"
title: "<Type>: <Title>"
type: "Domain" | "Module" | "Sub-Module" | "Specification"
status: "Draft"
summary: "One-sentence purpose."
summary_exec: "<150–300 words>"
interfaces:
  inputs: []
  outputs: []
  invariants: []
parent: "<parent_numeric_chain>_<parent_slug>"   # omit for top-level Domains
dependencies: []                                  # upstream ids if any
tags: ["doc-gdd"|"doc-tdd", ...]
---
```

**Path rules**

* **Domain (GDD):** `01_Knowledge/02_CANON/<Family>/<Domain>/<file>.md`
* **Module/Sub-Module (GDD):** nested within the owning Domain folder.
* **Specification (TDD):** `01_Knowledge/03_IMPLEMENTATION/02_Systems/<file>.md`

---

# Taxonomy (tech-fluent; where things live)

## 01\_Simulation\_Systems — data & dynamics (“what runs”)

01\_Spatial\_Timebase • 02\_Planet\_Atmosphere\_Sim • 03\_Ecosystem\_Sim • 04\_Resources\_Energy • 05\_Production\_Crafting • 06\_Settlements\_Logistics • 07\_Economy\_Governance • 08\_AgentAI\_Social • 09\_Risk\_Conflict

## 02\_Player\_Systems — input, views, UX (“how it’s perceived”)

01\_Modes\_Cameras • 02\_Rendering\_LOD • 03\_UI\_Framework\_HUD • 04\_Narrative\_Events • 05\_Accessibility\_Localization

## 03\_Platform\_Tooling — runtime, persistence, extensibility (“how it stays alive”)

01\_Runtime\_Scheduler • 02\_Persistence\_Versioning • 03\_Modding\_API • 04\_Networking\_Sync

**Canonical CANON tree**

```
/01_Knowledge/02_CANON/
├── 01_Simulation_Systems/
│   ├── 01_Spatial_Timebase/
│   ├── 02_Planet_Atmosphere_Sim/
│   ├── 03_Ecosystem_Sim/
│   ├── 04_Resources_Energy/
│   ├── 05_Production_Crafting/
│   ├── 06_Settlements_Logistics/
│   ├── 07_Economy_Governance/
│   ├── 08_AgentAI_Social/
│   └── 09_Risk_Conflict/
├── 02_Player_Systems/
│   ├── 01_Modes_Cameras/
│   ├── 02_Rendering_LOD/
│   ├── 03_UI_Framework_HUD/
│   ├── 04_Narrative_Events/
│   └── 05_Accessibility_Localization/
└── 03_Platform_Tooling/
    ├── 01_Runtime_Scheduler/
    ├── 02_Persistence_Versioning/
    ├── 03_Modding_API/
    └── 04_Networking_Sync/
```

---

# Core Pillars (Executive Summaries)

**Vision (why):** 50-year solo, modular, data-driven universe; emergent play with curated content; unified experience across game/writing/cinematics.
**Technical Foundations (how):** ECS purity; engine-agnostic core; persistence as database; concurrency-first; custom tooling.
**Knowledge System (working rules):** Docs are the source of truth; Tiering (Domain→Module→Sub-Module→Spec); Lifecycle (Init→Expand→Distill→Graduate); Manifest-driven context; Quality Gates.

```
```
,m 