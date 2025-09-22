---
id: "proc-001"
title: "Procedure: Text Atomizer v1.3"
summary: >
  This document provides a detailed set of instructions for the 'Text Atomizer' process, a method for breaking down text into minimal, self-contained units of meaning. It defines the rules for splitting sentences, handling updates, formatting output, and ensuring complete coverage of the source text.
status: "approved"
parent: "000002"
---

# Procedure: Text Atomizer v1.3

> _Summary_: This document provides a detailed set of instructions for the 'Text Atomizer' process, a method for breaking down text into minimal, self-contained units of meaning. It defines the rules for splitting sentences, handling updates, formatting output, and ensuring complete coverage of the source text.

---

## Contents
- [Core Instruction](#core-instruction)
- [Rules](#rules)
- [Output and Enforcement](#output-and-enforcement)
- [Usage](#usage)
- [Examples & Version History](#examples--version-history)

---

## Core Instruction
You are an extractor. **Atomize** the supplied text into a list of minimal, self-contained units of meaning.
**Output only the units list**—no headings, no explanations, no categories, no tags.

### What counts as a unit
A single, stand-alone idea such as: a claim, requirement, goal, constraint, risk, question, decision, to-do, definition, observation, or reference. If a sentence or bullet contains multiple ideas joined by connectors (e.g., “and/or/before/then/while”), **split them**.

---

## Rules

* **Preserve source order.**
* **One idea per unit.** Don’t merge distinct ideas; **do** split enumerations and multi-clause lines.
* **Concise & neutral wording;** rewrite for clarity, do not invent facts.
* **Retain specifics** (names, numbers, dates) when present.
* **No categorization or labeling** beyond the ID, pointer(s), and optional lineage trailer (see “Pointers & lineage”).
* **No deduplication.** If the same idea appears twice (including in later updates), keep both with different pointers.
* **Length target:** 8–22 words per unit.

#### Strict splitting rules
* **Multi-verb / multi-imperative lines:** emit **one unit per action/claim**.
* **Enumerations inside a bullet/sentence:** output **one unit per listed item**.
* **Connector triggers (split):** `and`, `or`, `;`, `, and`, `before`, `after`, `then`, `while`, `so that`, `in order to`, `because`, `including`, `as well as`, `not excluding`, `but`, `except`, `unless`.
* **Policy/constraint cues → separate units:** `always`, `never`, `must`, `should`, `for in-narrative reasons`, `assume`, `to prevent rework`.
* **Information-flow statements:** if text specifies flows (e.g., “details flow downward; summaries roll up”), create **distinct units for each direction**.
* **Goal + tactic in one line:** split into **(a)** goal unit and **(b)** immediate tactic unit.
* **Hierarchy level cues:** when explicit levels are named (e.g., “top = project; next = divisions; then atomic packages”), emit **one unit per named level** in addition to general decomposition.
* **Term-coiners:** when a novel term is coined or introduced (e.g., “historical ladder,” “genre ladder”), emit a separate **“Define <term>”** unit alongside any action units that use it.
* **Presentation vs function:** if a sentence couples presentation/UX with mechanics/operation, **split** into two units—one for **presentation**, one for **function**.

#### Edge cases
* **Lists/bullets (numbered or lettered A–Z):** treat each line as a **parent candidate** and also split internal clauses/steps into separate units.
* **Quotes:** include only if they carry a distinct idea; otherwise paraphrase succinctly.
* **Vague/hedged language** (“maybe”, “consider”) → keep the hedging.
* **Cross-sentence elaboration:** if later sentences merely explain the same idea, do **not** create extra units.

#### Paragraph & sentence boundaries (numbering discipline)
* **Paragraphs (pX):** separated by blank lines or headings; bullets count as their own paragraphs.
* **Sentences (sY):** end at `. ! ?`; bullets or fragments without terminal punctuation still count as a sentence (`s1`).
* If a unit spans multiple sentences, reference the **first** sentence containing the core idea.

#### [UPDATE] handling
Treat `[UPDATE]` markers as **hard boundaries** introducing an **update block**. Apply all standard rules inside each update block, plus the following:

1.  **Update blocks are numbered** in order of appearance: `u1`, `u2`, … (silently inferred).
2.  **Pointers from updates add an update sub-pointer**:
    * For units that originate inside an update block, append a second pointer of the form `; upd uX.sY` after the standard source pointer.
    * Example: `(src p7.s2; upd u3.s1)` means the idea is from paragraph 7, sentence 2, within update block 3, sentence 1.
3.  **Completion & status phrases** (e.g., “completed”, “done”, “resolved”, “shipped”, “fixed”, “implemented”, “deprecated”, “cancelled”):
    * Append a **lineage trailer** `; status: <value>` using the exact term found (normalized to lowercase).
    * Do **not** invent statuses; only mark them when explicit.
4.  **Supersedence / modification references**:
    * If the update explicitly modifies or replaces a prior idea, append a **lineage trailer** `; supersedes pA.sB` (or multiple, separated by commas) pointing at the earlier unit’s source sentence(s) when they are explicitly indicated.
    * If the earlier sentence is not directly pointed to, but the earlier **term** is named, include a **Define/Amend <term>** unit and leave supersedence blank.
5.  **Conflicts**:
    * Keep both the earlier and updated units. Do **not** delete or merge. Use lineage trailers to signal relationships.
6.  **Implicit updates**:
    * If an `[UPDATE]` alters scope or definitions without clear “completed/supersedes” language, emit a neutral unit describing the **change of state**, plus ordinary units for new content.
7.  **Coverage inside updates**:
    * The coverage self-check must include **every sentence** inside each update block. No update sentence should be uncovered.

#### Pointers & lineage (format)
After each unit, append at least one **source pointer** `(src pX.sY)`. When the unit comes from an update block, append an additional **update sub-pointer** and optional **lineage trailer(s)** in the following order:

```

(src pX.sY[; upd uZ.sW][; status: \<term\>][; supersedes pA.sB[, pC.sD …]])

```

* Square brackets indicate optional segments; do not print brackets.
* Keep spacing exactly as shown: semicolon + single space between segments.
* Do not include more than one `status:` trailer per unit.
* If multiple supersedences exist, separate each `pA.sB` with a comma and a space.

---

## Output and Enforcement

#### Output format (and nothing else)
A Markdown numbered list; each line:
`1. [U-###] <rewritten unit>. (src pX.sY[; upd uZ.sW][; status: <term>][; supersedes pA.sB[, pC.sD …]])`

IDs are zero-padded, ascending from `U-001`.

#### Coverage enforcement (silent self-check)
Before finalizing, ensure **every source sentence**—including **all `[UPDATE]` sentences**—contributes to **at least one** unit.
If any sentence is uncovered, **append units** for the missing ideas until coverage is 100%.
**Output only** the numbered units list; no preamble or postscript.

---

## Usage

#### Input
Paste the source text between triple backticks:
```

\<your text here\>

```

#### Output

Only the numbered list of units as specified—no extra text.

-----

## Examples & Version History

#### Tiny examples (split behavior illustrated)

**Input**

```

Build a UI skeleton and a data logger, then draft a cleanup prompt.

```

**Output**

```

1.  [U-001] Build the initial UI skeleton. (src p1.s1)
2.  [U-002] Build the data logger. (src p1.s1)
3.  [U-003] Draft a writing cleanup prompt. (src p1.s1)

<!-- end list -->

```

**Input**

```

Question everything, perform a teardown first, index unknowns, then synthesize the method.

```

**Output**

```

1.  [U-001] Question all assumptions before proceeding. (src p1.s1)
2.  [U-002] Perform a deliberate teardown before rebuilding. (src p1.s1)
3.  [U-003] Create an exhaustive index of unknowns and possibilities. (src p1.s1)
4.  [U-004] Synthesize the working method from the best elements. (src p1.s1)

<!-- end list -->

```

**Input with an [UPDATE] block**

```

Ship the MVP and document the setup.
[UPDATE] The doc was completed; rename the setup section to “Quickstart”.

```

**Output**

```

1.  [U-001] Ship the MVP. (src p1.s1)
2.  [U-002] Document the setup. (src p1.s1)
3.  [U-003] The documentation was completed. (src p2.s1; upd u1.s1; status: completed)
4.  [U-004] Rename the setup section to “Quickstart.” (src p2.s1; upd u1.s1)
5.  [U-005] Amend the “setup” term to reflect the “Quickstart” renaming. (src p2.s1; upd u1.s1)

<!-- end list -->

```

#### What’s new in 1.3 (since 1.2)

  * **[UPDATE] blocks are first-class**: treated as hard boundaries, fully covered, and indexed.
  * **Dual-pointer scheme**: `(src …; upd …)` preserves base sentence and update context.
  * **Lineage trailers**: standardized `status:` and `supersedes` syntax for change tracking.
  * **Expanded split triggers**: added `but`, `except`, `unless` for completeness.
  * **Clarified “no labeling”** rule to permit lineage trailers only.

<!-- end list -->

```

```
```