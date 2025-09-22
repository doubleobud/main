---
id: "proc-002"
title: "Procedure: Text Sorter v4.0 (Four-Domain Doctrine)"
summary: >
  This document outlines the v4.0 procedure for sorting atomized text units into four distinct domains: Operations, Reference, Ideas, and Backlog. It details the pre-processing steps, domain definitions, classification rules, and final output format.
status: "approved"
parent: "proc-001"
---

# Procedure: Text Sorter v4.0 (Four-Domain Doctrine)

> _Summary_: This document outlines the v4.0 procedure for sorting atomized text units into four distinct domains: Operations, Reference, Ideas, and Backlog. It details the pre-processing steps, domain definitions, classification rules, and final output format.

---

## Contents
- [Overview and I/O](#overview-and-io)
- [Pre-processing Steps](#pre-processing-steps)
- [The Four Domains](#the-four-domains)
- [Classification Rules](#classification-rules)
- [Output Format and Sorting](#output-format-and-sorting)
- [Spot-Check Examples](#spot-check-examples)

---

## Overview and I/O
This procedure converts a raw atom list (`YYYY-MM-DD_atomized_log`) into a compact, consistently categorized file (`YYYY-MM-DD_sorted_atomized_log`) using four Domains: **Operations, Reference, Ideas, Backlog**. `[UPDATE]` markers are for chronology only and are ignored during sorting.

-   **Input file name:** `YYYY-MM-DD_atomized_log` (e.g., `2025-08-05_atomized_log`)
-   **Output file name:** `YYYY-MM-DD_sorted_atomized_log` (same date as input)
-   **Assumptions:** one atom per line (or separable via punctuation); optional IDs like `U-###`.

---

## Pre-processing Steps
1.  Load the file as plain text.
2.  Strip blank lines and trim whitespace.
3.  **Ignore** `[UPDATE]` lines for categorization (they’re time markers).
4.  **Prune NV**: Drop atoms explicitly marked *NV / non-valuable / not useful / delete*.
5.  **De-duplicate**: Remove exact duplicates; if a later duplicate has an ID, append “(see U-###)” to the first kept instance.
6.  **Split multi-idea lines** into separate atoms (use punctuation boundaries: `;`, `—`, or “and then”).
7.  Preserve an **original order index** for each atom (used as a stable secondary sort key).

---

## The Four Domains
#### Domain 1 — **Operations**
*Operational foundations: how we work.*

Includes **values, principles, rules, standards, policies, processes, procedures, methods, algorithms, templates, checklists, workflows**—anything that prescribes *how* the project should be run or provides reusable “how-to”.

-   **Strong cues**: `must`, `shall`, `should`, `policy`, `rule`, `standard`, `convention`, `naming`, `parent/child`, `process`, `procedure`, `method`, `algorithm`, `workflow`, `template`, `checklist`, `playbook`, `always`, `never`.

#### Domain 2 — **Reference**
*Project memory & canon: what is true, defined, or decided.*

Includes **lore/worldbuilding**, **technical documentation**, **definitions/glossary**, **observations**, and **decisions (as historical record)**. Once a choice is made or a fact is established, it belongs here.

-   **Strong cues**: `is/are/was`, `means`, `defined as`, `called`, `observed`, `measured`, `canon`, `history`, `decision was made`, `we will` *(commitment recorded)*.

#### Domain 3 — **Ideas**
*Possibility space: what might be.*

Includes **concepts**, **requirements**, **constraints**, **resources to consider** (papers/tools you may digest later). Not yet adopted or scheduled.

-   **Strong cues**: `could`, `might`, `potential`, `explore`, `consider`, `requirement`, `constraint`, `resource`.

#### Domain 4 — **Backlog**
*Focused and actionable work: what we can do now.*

Includes **questions/assumptions/hypotheses**, **problems/issues/bugs/risks**, **experiments/prototypes/spikes**, **to-dos**, and **research tasks phrased as actions**.

-   **Strong cues**: `need to`, `is needed`, `should be built`, `create`, `implement`, `design`, `define`, `research`, `investigate`, `fix`, `prototype`, `timebox`.

---

## Classification Rules
#### A) Precedence (apply in order; stop at first match)
1.  **Backlog** — if the atom is framed as **action to take now** (task, question to resolve, research to do, problem to fix).
2.  **Operations** — if the atom **prescribes how things must/should be done** or **defines reusable methods/steps**.
3.  **Reference** — if the atom **states truth/definition/observation** or **records a decision/commitment**.
4.  **Ideas** — if the atom is **speculative/desirable** but not yet adopted or scheduled.

#### B) Tie-breakers
-   If the line **records a commitment** (“we will…”, “for now…”, “decision was made”), file to **Reference** (historical record), not Operations.
-   If it **describes steps needed in the future** (“we need a process…”, “build a method to X”), file to **Backlog** (it’s work, not a finished process).
-   If unsure between **Ideas** and **Reference**, ask: *“Is it true now?”* If yes → **Reference**, else → **Ideas**.
-   If unsure between **Operations** and **Reference**:
    -   **Prescriptive/how-to** → **Operations**
    -   **Descriptive/record** → **Reference**

---

## Output Format and Sorting
The final output should only contain these sections in this fixed order, omitting any empty ones.

```

# Operations

  * ...

# Reference

  * ...

# Ideas

  * ...

# Backlog

  * ...

<!-- end list -->

```

#### Sorting & Formatting inside each Domain
1.  **Primary sort:** original order index captured in pre-processing.
2.  **Secondary (optional):** cluster by shared subject prefix (e.g., `UI:`, `Narrative:`, `Simulation:`).
3.  **One-line bullets** per atom:
    -   `- [U-###] text` (or `- text` if no ID).
    -   Keep clarifying notes short, in parentheses.

Finally, save the result as `YYYY-MM-DD_sorted_atomized_log`.

---

## Spot-Check Examples
-   “We will use logs as the foundation.” → **Reference** (commitment recorded)
-   “Adopt file naming rule `YYYY-MM-DD_*`.” → **Operations** (policy/standard)
-   “Define the term ‘historical ladder’.” → **Backlog** (task)
    -   Later: “A concept is being called a ‘historical ladder’.” → **Reference** (definition)
-   “Create a method library with standard prompts.” → **Backlog** (work to build)
    -   Later: “Method library: prompts X/Y/Z.” → **Operations** (reusable method)
-   “I envision an ever-growing universe.” → **Ideas** (concept)
```