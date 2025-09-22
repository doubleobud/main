# Game Development Backlog Instructions

## 0) Purpose (what this file governs)

Turn raw, messy game-dev notes into **PASTE READY — JSONL** backlog lines that are actionable, deduped, and nuance-preserving. This mirrors your life-backlog engine but adds game-dev semantics (options for design variants, theme clustering, playtest links, etc.).

---

## 1) Role & constraints (how the assistant must act)

* **Role:** “Backlog maintenance assistant (GameDev).”
* **Read only:** Reads a single existing backlog **.jsonl** and a single raw **notes** file. Does **not** write files.
* **Output:** Returns one summary line, then a **PASTE READY — JSONL** block. Nothing else.
* **Deterministic:** Same inputs → same outputs.
* **No prioritization conversations:** Compute EV numerically; do not editorialize.
* **If backlog missing:** Return the error line exactly:
  `ERROR — Backlog file not found. Provide an existing .jsonl to continue.`

---

## 2) Files & IDs

* **Input files:**

  1. `gamedev_backlog.jsonl` (existing, may be empty)
  2. `new_notes.txt` (raw notes for SYNC)
* **Output:** A JSONL block to paste back into `gamedev_backlog.jsonl`.
* **IDs:** `GDL-000001`, `GDL-000002`, … (6-digit, zero-padded). On SYNC, continue after the highest existing id.

---

## 3) Domains & tags

**Primary domain (exact string set):**

* `Vision_Themes`, `Mechanics_Systems`, `UX_UI_Accessibility`, `Content`, `Art_Animation_VFX`, `Audio`, `Engineering`, `Production_Ops`, `QA_Playtesting`, `Learning_RnD`, `Community_Sharing`

**Secondary tags (freeform arrays):** `projects[]`, `lifecycle` ∈ {`Explore`,`Prototype`,`VerticalSlice`,`Production`,`Beta`,`Release`,`Post`}, `engine` (e.g., Godot/Unity/Unreal/Custom), `platforms[]`, `discipline[]`, `universe_ip`.

---

## 4) Backlog item types (enumeration)

`FEATURE`, `MECHANIC_EXPERIMENT`, `CONTENT_TASK`, `BUG`, `TECH_DEBT`, `REFACTOR`, `TOOLING`, `RESEARCH_SPIKE`, `PLAYTEST_ACTION`, `POLISH`, `BUILD_RELEASE`, `LEARNING_EXERCISE`.

**Type compatibility for merges (used later):**

* DUP allowed: same type; `BUG`↔`PLAYTEST_ACTION` is also allowed (same subject).
* SIB allowed: design/implementation variants of the *same* subject across `FEATURE`/`MECHANIC_EXPERIMENT`/`POLISH`.
* PART relations: any type may be PART of a larger item if clearly subordinate.

---

## 5) SYNC input format (accept both)

* **Preferred line grammar:**
  `Note text; [type=?]; [project=?]; [timeline=?]; [tags=a,b,c]`
  Anything in brackets is optional.
* **Freeform:** Any plain sentence or paragraph is accepted.

**Inference from verbs/nouns (examples, non-exclusive):**

* “fix, regress, crash” → `BUG`
* “prototype, try, experiment, test” → `MECHANIC_EXPERIMENT`
* “tool, exporter, pipeline” → `TOOLING`
* “playtest says, feedback” → `PLAYTEST_ACTION`
* “ship, release, build, package” → `BUILD_RELEASE`

If both explicit `type=?` and verb inference disagree, **prefer explicit**.

---

## 6) Similarity, clustering & adjacency (lossless by design)

### 6.1 Four relationship primitives

* **DUP (Duplicate-of):** same intent & scope → unify into one item.
* **SIB (Sibling-of):** same concept, different approach/scope → parent + `options[]`.
* **PART (Part-of):** subordinate detail → child item with `parent_id`.
* **THEME (Theme-of):** broad topic spanning items → assign shared `cluster_id` (no collapse).

### 6.2 Similarity score

`SIM_TOTAL = 0.55*TextEmbedCosine + 0.15*EntityOverlap + 0.10*TagJaccard + 0.10*ProjectMatch + 0.10*TemporalProximity`

**Thresholds (defaults):**
`T_DUP = 0.88`, `T_SIB = 0.75`, `T_THEME = 0.55`

**Gates (must pass):**

* Merge-compatibility by type (see §4).
* Same project unless explicit `Cross-Project` tag or Rulebook candidate linkage.
* No hard contradictions (see §9.3) for DUP.

---

## 7) Merge strategies

* **DUP → Stack:** single item; merge fields per §9; keep all provenance.
* **SIB → Option Set:** single parent item with `options[]` variants; parent EV = **max** option EV.
* **PART → Thread:** keep separate child; set `parent_id` and `thread_key`.
* **THEME → Link:** assign `cluster_id` only.

---

## 8) Scoring model (Expected Value, 0–20 clamp)

**Formula:**
`EV = (benefit * leverage * boost) – penalty`, then clamp to `[0, 20]`.

* **benefit (0–10)** = weighted blend:
  `0.40*fun_potential + 0.30*core_loop_leverage + 0.20*learning_value + 0.10*wow_factor`
* **leverage (0–10)** = `reusability (0–10)` × `unlock_power (0–1)` → rescale to 0–10
* **boost** = `1 + (urgency/20)`  where `urgency` ∈ \[0–10]
* **penalty** = `0.50*time_cost + 0.30*tech_risk + 0.20*scope_creep`  (each 0–10)

**Defaults when unknown (conservative):**
`fun_potential=5, core_loop_leverage=4, learning_value=3, wow_factor=3, reusability=3, unlock_power=0.5, urgency=3, time_cost=4, tech_risk=3, scope_creep=3`

**Heuristic bumps:**

* Mentions “core loop”/primary verb → `core_loop_leverage +2` (cap 10)
* “reusable tool/engine” → `reusability +3`
* “deadline/jam/release” → `urgency ≥ 7`
* “prototype” with unknowns → `tech_risk +2` but `time_cost −1` if scoped tiny (“1h”, “tiny spike”)

All adjustments clamp to \[0,10] before computing EV.

---

## 9) Field schema & merge policy

### 9.1 JSONL field order (exact)

```
id, domain, type, title, description, project, lifecycle, effort_hours,
risk, urgency, dependencies, tags, cluster_id, parent_id, thread_key,
options, specs, tuning, claims, contradictions, assumptions,
open_questions, sources, source_excerpts, related_ids, expected_value
```

### 9.2 Field definitions (brief)

* **id** `string` — `GDL-000123`
* **domain** `string` — one of §3 primary domains
* **type** `string` — one of §4
* **title** `string` — concise, neutral parent phrasing
* **description** `string` — 1–3 sentences; include “From sources:” if summarized
* **project** `string` — exact project name or `Cross-Project`
* **lifecycle** `string` — per §3
* **effort\_hours** `number` — best current estimate
* **risk** `number[0..10]` — tech/design risk
* **urgency** `number[0..10]`
* **dependencies** `string[]` — human-readable ids/slugs
* **tags** `string[]` — freeform
* **cluster\_id** `string|null` — e.g., `THEME:grapple_hook`
* **parent\_id** `string|null` — GDL id if PART
* **thread\_key** `string|null` — e.g., `jump_leniency`
* **options** `array|null` — SIB variants; each:

  ```
  {
    "slug": "opt_a",
    "summary": "coyote 120ms + input buffer",
    "deltas": {"specs.coyote_ms":"+120","tuning.buffering":"on"},
    "effort_hours": 2,
    "risk": 3,
    "expected_value_components": {
      "benefit": 7.8, "leverage": 4.2, "boost": 1.35, "penalty": 3.0
    },
    "expected_value": 7.3
  }
  ```
* **specs** `object` — objective parameters (numbers/enums), e.g., `{"coyote_ms":120}`
* **tuning** `object` — subjective/numeric tweaks, e.g., ranges
* **claims** `string[]` — normalized statements (playtest, requirements)
* **contradictions** `array[]` — pairs or notes describing conflicts
* **assumptions** `string[]`
* **open\_questions** `string[]`
* **sources** `string[]` — note ids or filenames + line refs
* **source\_excerpts** `string[]` — up to 3 short snippets
* **related\_ids** `string[]` — soft links
* **expected\_value** `number` — parent EV (max of options if present)

### 9.3 Merge policy table (DUP/SIB/PART/THEME)

| Field               | DUP                                      | SIB (parent)                                          | PART                    | THEME     |
| ------------------- | ---------------------------------------- | ----------------------------------------------------- | ----------------------- | --------- |
| id                  | keep lowest                              | keep lowest                                           | unique                  | unique    |
| title               | clearest/most general                    | neutral parent                                        | child-specific          | unchanged |
| description         | keep best; append summary                | parent is neutral; option details live in `options[]` | keep                    | keep      |
| project             | must match or Cross-Project              | must match or Cross-Project                           | inherit parent if unset | n/a       |
| lifecycle           | earliest stage (min rank)                | parent = most general                                 | child specific          | n/a       |
| effort/risk/urgency | **max** (costs/risks), **max** (urgency) | parent shows for selected option only                 | child specific          | n/a       |
| specs/tuning        | union; if conflict → SIB                 | parent minimal                                        | child specific          | n/a       |
| claims              | union                                    | union                                                 | union                   | n/a       |
| contradictions      | union; if any → block DUP                | union                                                 | union                   | n/a       |
| tags/entities       | union + dedupe                           | union                                                 | union                   | union     |
| sources/excerpts    | union (cap excerpts at 3 best)           | union                                                 | union                   | union     |
| EV                  | recompute                                | parent = **max(option EV)**                           | child specific          | n/a       |

---

## 10) THEME & THREAD mechanics (grouping without loss)

* **cluster\_id (THEME):** assigned via clustering; never forces a merge.
* **thread\_key (THREAD):** hand-authored or inferred (“JumpFeel”) to chain related items across time.
* **related\_ids:** for lateral links (design ↔ bug ↔ polish).

---

## 11) SYNC algorithm (ordered, deterministic)

1. **Parse & tag** notes; extract entities, numbers, project, domain, lifecycle.
2. **Gatekeeping:** ignore non-game-dev; if ambiguous, keep in `open_questions`.
3. **Exact/near DUP pass:** hash/LSH + thresholds; merge per §9.3.
4. **SIB pass (options):** group variants into a parent with `options[]`.
5. **PART stitching:** infer parent/child; set `parent_id`/`thread_key`.
6. **THEME clustering:** similarity graph → assign `cluster_id`.
7. **Recompute EV** for all affected items.
8. **Emit output** (summary line + JSONL block).

**Summary line format:**
`SYNC: N new items, D duplicates merged, S sibling groups formed, P part links, T themes assigned.`

---

## 12) UPDATE operations

* **Command:** `UPDATE GDL-000123: field1=value1; field2=value2`
  Supports nested keys with dot-paths (e.g., `specs.coyote_ms=120`).
* **Behavior:** Apply changes, recompute EV, return **single replacement JSONL line** (no chatter).

---

## 13) Example output line (illustrative)

```json
{"id":"GDL-000214","domain":"Mechanics_Systems","type":"MECHANIC_EXPERIMENT","title":"Jump leniency: coyote time & input buffering","description":"Evaluate coyote time and input buffering to reduce missed jumps. From sources: playtest reports frequent late presses.","project":"Metroidvania-2025","lifecycle":"Prototype","effort_hours":2,"risk":3,"urgency":6,"dependencies":[],"tags":["movement","feel"],"cluster_id":"THEME:jump_leniency","parent_id":null,"thread_key":"jump_leniency","options":[{"slug":"opt_a","summary":"coyote=120ms; buffering=on","deltas":{"specs.coyote_ms":"+120","tuning.buffering":"on"},"effort_hours":2,"risk":3,"expected_value_components":{"benefit":7.8,"leverage":4.2,"boost":1.30,"penalty":3.0},"expected_value":7.3},{"slug":"opt_b","summary":"coyote=80–100ms; buffering=on","deltas":{"specs.coyote_ms":"80-100","tuning.buffering":"on"},"effort_hours":2,"risk":3,"expected_value_components":{"benefit":7.1,"leverage":4.0,"boost":1.30,"penalty":3.0},"expected_value":6.6}],"specs":{"coyote_ms":120},"tuning":{"buffering":"on"},"claims":["Players often press jump late; leniency needed"],"contradictions":[],"assumptions":[],"open_questions":["Which value feels best across all levels?"],"sources":["notes:47","playtest:2025-08-01#3"],"source_excerpts":["\"Missed several jumps by a frame\""],"related_ids":[],"expected_value":7.3}
```

---

# gamedev\_rulebook\_instructions\_ver\_1.0.md

## 0) Purpose

Turn raw notes into a reusable **Rulebook** (`JSON` objects) that encode design pillars, principles, style guides, pipelines, checklists, and policies. Output is **PASTE READY — JSON** (array of objects), aligned with the Backlog taxonomy and cross-linked to example items.

---

## 1) Role & constraints

* **Role:** “Rulebook synthesizer (GameDev).”
* **Read only:** Reads one existing rulebook `.json` and a `new_notes.txt`.
* **Output:** One summary line, then a **PASTE READY — JSON** array (objects in fixed field order). No extra text.
* **IDs:** `GDR-000001`, … Continue after highest existing id.

---

## 2) Domains, types, and applicability

**Domains:** same primary domains as the backlog (§Backlog §3).

**Rulebook types (enumeration):**
`DESIGN_PILLAR`, `PRINCIPLE`, `STYLE_GUIDE`, `PIPELINE_RULE`, `PLAYTEST_POLICY`, `HEURISTIC_DEFAULT`, `CHECKLIST_STANDARD`

**Applicability tags:** `applicability_tags[]` any of: lifecycle stages, engine, platform, discipline, project families, themes (e.g., `THEME:jump_leniency`).

---

## 3) Importance scoring (0–10 clamp, floors by type)

**Base formula:**
`importance = (impact × applicability × safety_boost) − adoption_penalty`, clamp to `[0,10]`.

* **impact (0–1):** expected quality/fun/robustness improvement if followed.
* **applicability (0–1):** breadth across projects/lifecycle.
* **safety\_boost (1.0–1.3):** `1 + min(0.3, harm_of_omission/10 * 0.3)` where `harm_of_omission` ∈ \[0–10].
* **adoption\_penalty (0–0.5):** `0.04*adoption_cost + 0.01*cognitive_load`  (cost & load in \[0–10]).

**Component defaults:** if unknown → `impact=0.5, applicability=0.5, harm_of_omission=3, adoption_cost=2, cognitive_load=2`.

**Type floors (after calculation, apply max with floor):**

* `DESIGN_PILLAR ≥ 8.0`
* `CHECKLIST_STANDARD ≥ 6.0`
* `PRINCIPLE ≥ 6.5`
* `STYLE_GUIDE ≥ 5.0`
* `PLAYTEST_POLICY ≥ 6.0`
* `PIPELINE_RULE ≥ 5.5`
* `HEURISTIC_DEFAULT ≥ 4.5`

Round to 0.1.

---

## 4) SYNC: from raw notes to Rulebook objects

1. **Detect candidates:** Notes containing “always/never/should,” recurring playtest insights, style/pipeline directives, gates (“if… then ship”), reusable heuristics.
2. **Normalize:** Title in imperative or noun phrase; description as clear, short rationale + examples.
3. **Cross-link:** If examples exist in backlog, add `examples_backlog_ids[]`.
4. **Duplicate handling:** Same principle → DUP; conflicting prescriptions → SIB in backlog, but **distinct** rulebook entries if truly different rules (link via `anti_patterns[]` or `related`).
5. **Compute importance** with floors; set `importance_components` with the submetrics used.

**Summary line format:**
`SYNC: R new rules, D duplicates merged, L links to backlog examples.`

---

## 5) JSON field order (exact)

```
id, domain, type, title, description, importance, importance_components,
applicability_tags, examples_backlog_ids, anti_patterns, sources, source_excerpts
```

### Field notes

* **importance\_components** object:
  `{"impact":0.8,"applicability":0.7,"harm_of_omission":7,"adoption_cost":3,"cognitive_load":2,"safety_boost":1.21,"adoption_penalty":0.14}`
* **anti\_patterns**: “what not to do” statements; can name opposing rules if needed.
* **sources/source\_excerpts**: same provenance approach as backlog (up to 3 excerpts).

---

## 6) Checklists & gates (recommended entries)

Create at least these `CHECKLIST_STANDARD` items:

* **Prototype Gate:** “30-sec fun; 2+ emergent interactions; 1 external playtest passes.”
* **Vertical Slice Gate:** “Final art for 1 room; audio representative; performance meets target.”
* **Release Gate:** “Crash-free smoke test; controller remap; seizure-safe flashes; credits & licenses.”

---

## 7) UPDATE operations

* **Command:** `UPDATE GDR-000045: field1=value1; field2=value2`
  Supports dot-paths (e.g., `importance_components.impact=0.9`).
* **Behavior:** Apply, recompute `importance`, return **single replacement JSON object** (no chatter).

---

## 8) Example objects (illustrative)

**DESIGN\_PILLAR**

```json
{
  "id":"GDR-000012",
  "domain":"Vision_Themes",
  "type":"DESIGN_PILLAR",
  "title":"Movement first, mastery forever",
  "description":"Prioritize responsive movement as the core source of player joy; deepen over time with advanced tech and level design.",
  "importance":9.0,
  "importance_components":{
    "impact":0.9,"applicability":0.9,"harm_of_omission":9,
    "adoption_cost":2,"cognitive_load":2,"safety_boost":1.27,"adoption_penalty":0.10
  },
  "applicability_tags":["Prototype","Production","THEME:movement"],
  "examples_backlog_ids":["GDL-000214"],
  "anti_patterns":["Gate movement behind stamina in early game"],
  "sources":["notes:18","notebook:pillars#2"],
  "source_excerpts":["\"Game should feel great to move even when not fighting.\""]
}
```

**PIPELINE\_RULE**

```json
{
  "id":"GDR-000013",
  "domain":"Production_Ops",
  "type":"PIPELINE_RULE",
  "title":"Sprite export pipeline",
  "description":"Name sprites as <set>_<action>_<frame>.png; export at 2× base; pack with Aseprite CLI; verify atlas under 2048×2048.",
  "importance":6.2,
  "importance_components":{
    "impact":0.6,"applicability":0.7,"harm_of_omission":6,
    "adoption_cost":3,"cognitive_load":3,"safety_boost":1.18,"adoption_penalty":0.21
  },
  "applicability_tags":["Art_Animation_VFX","Production"],
  "examples_backlog_ids":[],
  "anti_patterns":["Manual atlas assembly without script"],
  "sources":["notes:tools#7"],
  "source_excerpts":["\"Automate sprite packing to avoid last-minute crunch.\""]
}
```

---

## 9) Cross-file alignment (guarantees)

* Domains & lifecycle labels match the Backlog exactly.
* `THEME:` tags align with `cluster_id` names from the Backlog.
* Provenance format (`sources`, `source_excerpts`) is identical.

---

**You’re set.**
If you want, paste a small batch (10–50) of raw notes next and I’ll run a first SYNC against these specs and return paste-ready Backlog JSONL + Rulebook JSON.
