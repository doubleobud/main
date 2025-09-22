Great instinct. You’ll get far better reliability (and fewer hallucinations) by **splitting the pipeline**:

# Idea/To-Do Parser

## 0) Purpose

Convert raw, mixed text sources into **PASTE READY — JSONL** where each line is a single **atomic note** with: the original text, light normalization, extracted entities/numbers/tags, candidate type/project, timeline hints, and **provenance + confidence**.
This stage **never merges, never scores, never invents**—it only segments and extracts. Its output is the input to the Backlog and Rulebook SYNC steps.

---

## 1) Role & Constraints

* **Role:** “First-Pass Parser (GameDev).”
* **Read-only:** Reads one or more raw text files; does **not** write files.
* **Deterministic:** Same input → same output.
* **No inference beyond text:** If it isn’t in the text (or a trivial synonym), don’t assume it.
* **No merging/dedup/scoring:** Leave that to later stages.

---

## 2) Inputs & Outputs

* **Inputs (one or many):** plain-text files (e.g., `notes_discord.txt`, `journal_2025-07.txt`, `playtest_2025-08-01.txt`).
* **Output:** One block labeled **PASTE READY — JSONL (PARSED NOTES)** containing line-delimited JSON objects.

**IDs:** `PN-000001`, `PN-000002`, … (six-digit, zero-padded). Restart from the next highest id if an existing parsed file is provided.

---

## 3) Atomic Segmentation (how to split the text)

Split into **atomic notes** using this order of rules (stop at the first that applies):

1. “Hard” separators: blank line, Markdown list bullet, numbered list, `—`, `•`, `*`, `- ` at line start.
2. Sentence break **only** if punctuation marks a full thought **and** there’s no dangling clause like “e.g.”, code, or URL.
3. Keep code/stack traces/CLI lines intact; never split inside backticks `…` or indented code blocks.
4. Preserve quoted feedback as one unit (lines starting with `>` or surrounded by quotes).

Each atomic note keeps exact original text in `raw`.

---

## 4) Light Normalization & Extraction

For each atomic note, populate these fields (exact order):

```
id, source, position, timestamp_hint, raw, normalized, domain_hint, candidate_type, project_hint,
lifecycle_hint, tags, entities, numbers, timeline_hint, engine_platforms, theme_keys,
confidence, needs_review, rationale, source_excerpts
```

**Field Definitions (concise):**

* **id** `string` — `PN-000123`.
* **source** `string` — file name or human label you provide.
* **position** `string` — line/paragraph indices like `L42` or `P3-L2`.
* **timestamp\_hint** `string|null` — explicit date/time parsed from the note; else `null`.
* **raw** `string` — original text (verbatim).
* **normalized** `string` — cleaned single-line version; keep all meaning.
* **domain\_hint** `string|null` — one of Backlog domains if obvious, else `null`.
* **candidate\_type** `string|null` — one of Backlog types (e.g., `BUG`, `MECHANIC_EXPERIMENT`, …) if obvious, else `null`.
* **project\_hint** `string|null` — explicit project name if present (“Metroidvania-2025”), else `null`.
* **lifecycle\_hint** `string|null` — one of `Explore|Prototype|VerticalSlice|Production|Beta|Release|Post` if present.
* **tags** `string[]` — hashtags/keywords explicitly in text; keep conservative.
* **entities** `object` — extracted nouns: `{"mechanics":["grapple"],"systems":["combat"],"assets":["sprite_idle"],"inputs":["RT"],"levels":["Level_2"],"npcs":[]}`
* **numbers** `object` — any numeric/units: `{"coyote_ms":120,"cooldown_s":1.2}`
* **timeline\_hint** `string|null` — phrases like “this week”, “for jam”, due dates if explicit.
* **engine\_platforms** `object` — `{"engine":"Godot","platforms":["PC","SteamDeck"]}` if found.
* **theme\_keys** `string[]` — candidate theme tokens (e.g., `["jump_leniency","grapple_hook"]`).
* **confidence** `number` — 0–1 extraction confidence (not quality of idea).
* **needs\_review** `boolean` — `true` if ambiguity/contradiction/low confidence (<0.6).
* **rationale** `string` — very short “why” for the key hints (one sentence).
* **source\_excerpts** `string[]` — up to 2 literal substrings supporting the hints.

---

## 5) Heuristics (strict & conservative)

* **Type verbs → candidate\_type:**

  * `fix, crash, broken, regression` → `BUG`
  * `prototype, try, experiment, spike, test` → `MECHANIC_EXPERIMENT`
  * `tool, exporter, pipeline, automation` → `TOOLING`
  * `art, sprite, tileset, rig, shader` → `CONTENT_TASK` or `Art_Animation_VFX` domain
  * `ship, build, package, release` → `BUILD_RELEASE`
  * `playtest, feedback, testers said, confused` → `PLAYTEST_ACTION`
* **Numbers & units:** capture with units (ms, s, px, %, dB, frames), keep as strings if ambiguous.
* **Themes:** noun phrases repeated across notes → add to `theme_keys` (kebab-case).
* **Projects:** recognize patterns like `Project: Name`, `[#Name]`, or folder-like tokens.
* **Lifecycle:** map `“jam”` → `Prototype`, `“vertical slice”` → `VerticalSlice`.
* **Confidence:** start at 0.5; add +0.2 if explicit keyword present; +0.1 if two corroborating signals; −0.2 if contradictory tokens; clamp 0–1.

---

## 6) Hallucination Guards

* Never invent: **If absent, leave `null` or empty.**
* If two interpretations exist, set `needs_review=true`, include both in `rationale`, and keep fields conservative (`candidate_type=null` unless explicit).
* Do not “fix” typos semantically; keep the original in `raw`.

---

## 7) Output helper for downstream steps

Alongside the structured fields, include a convenience **`normalized_line`** that your Backlog SYNC can ingest directly if you want to skip inference:

```
"normalized_line": "«RAW WITHOUT NEWLINES»; type=?«candidate_type or blank»; project=?«project_hint or blank»; timeline=?«timeline_hint or blank»; tags=«comma,separated,tags»"
```

(Leave `?` values empty if unknown; do not guess.)

---

## 8) SYNC procedure (Parser)

1. Read all provided raw files.
2. Segment into atomic notes using §3.
3. Extract fields per §4–5 with guards in §6.
4. Emit a single **PASTE READY — JSONL (PARSED NOTES)** block.
5. **Summary line** before the block (exact format):
   `PARSE: S sources, N notes, R needs_review.`

---

## 9) UPDATE (Parser)

* **Command:** `UPDATE PN-000123: field=value; field2=value2` (dot paths allowed).
* **Behavior:** Return the **single replacement JSONL line** with only that object, no chatter.

---

## 10) Examples

**Example A — clear experiment note**

```json
{"id":"PN-000041","source":"journal_2025-08.txt","position":"P3","timestamp_hint":"2025-08-02","raw":"Prototype coyote time around 120ms and add input buffering for jumps.","normalized":"Prototype coyote time around 120ms and add input buffering for jumps.","domain_hint":"Mechanics_Systems","candidate_type":"MECHANIC_EXPERIMENT","project_hint":"Metroidvania-2025","lifecycle_hint":"Prototype","tags":["movement","feel"],"entities":{"mechanics":["coyote time","input buffering"],"systems":["jump"],"assets":[],"inputs":[],"levels":[]},"numbers":{"coyote_ms":120},"timeline_hint":null,"engine_platforms":{},"theme_keys":["jump_leniency"],"confidence":0.9,"needs_review":false,"rationale":"Keywords prototype/coyote time and 120ms strongly indicate MECHANIC_EXPERIMENT in movement system.","source_excerpts":["\"Prototype coyote time\"","\"120ms\""],"normalized_line":"Prototype coyote time around 120ms and add input buffering for jumps.; type=?MECHANIC_EXPERIMENT; project=?Metroidvania-2025; timeline=?; tags=movement,feel"}
```

**Example B — ambiguous**

```json
{"id":"PN-000042","source":"discord_dump.txt","position":"L118","timestamp_hint":null,"raw":"Jump feels floaty—maybe gravity curve or air control too high?","normalized":"Jump feels floaty—maybe gravity curve or air control too high?","domain_hint":"Mechanics_Systems","candidate_type":null,"project_hint":null,"lifecycle_hint":null,"tags":["feel"],"entities":{"mechanics":["gravity curve","air control"],"systems":["jump"],"assets":[],"inputs":[],"levels":[]},"numbers":{},"timeline_hint":null,"engine_platforms":{},"theme_keys":["jump_leniency"],"confidence":0.55,"needs_review":true,"rationale":"Complaint without directive—cannot classify as BUG or EXPERIMENT with confidence.","source_excerpts":["\"floaty\""],"normalized_line":"Jump feels floaty—maybe gravity curve or air control too high?; type=?; project=?; timeline=?; tags=feel"}
```

---

# Orchestration runbook (recommended)

**Why not “all in one chat”?**
Combining parser + backlog + rulebook in a single giant prompt increases context collisions and silent assumptions. Splitting keeps each step **deterministic** and gives you a clean audit trail.

**Safe, repeatable flow:**

1. **Batch the raw sources** (by file or \~50–300 atomic notes per run).
2. Run **First-Pass Parser SYNC** → get **PASTE READY — JSONL (PARSED NOTES)**.
3. Copy the `normalized_line` strings (or the `raw` texts) into `new_notes.txt` for **GameDev Backlog SYNC**; keep the parsed JSONL as provenance.
4. In parallel, feed the same parsed notes to **GameDev Rulebook SYNC**—it will identify candidates for principles/pipelines/checklists.
5. Commit outputs. Keep anything with `needs_review=true` in a small “Review” batch you can resolve later.

**Batch size guidance:** stay comfortably under a few hundred atomic notes per run; group by source when possible (easier troubleshooting). You can always rerun with another batch—no state is lost.

---

If you want, I can also generate a tiny **router prompt** that ingests multiple files at once and outputs exactly the **PASTE READY — JSONL (PARSED NOTES)** block in the format above.
