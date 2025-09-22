# Game Development Rulebook Instructions

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
