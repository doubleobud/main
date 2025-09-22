# overall\_project\_narrative\_system\_concept

**Purpose:** a complete, copy-pasteable blueprint you can drop into a fresh chat so another model can help you execute—step by step—without needing clarifying questions.

**Assumptions:** public-by-default (with redaction gates), solo for now but collab-ready, text-first Markdown, Git primary, cadence baseline = *2 narrative posts/week + 1 doc update/week*, licenses = *CC BY 4.0 (docs) + Apache-2.0 (code)*.

---

## Table of Contents

1. [Executive Overview Board (revised)](#executive-overview-board-revised)
2. [Decision Summary (locked)](#decision-summary-locked)
3. [Conceptual Model (text diagram)](#conceptual-model-text-diagram)
4. [Information Architecture & Site Map (Chrono-First)](#information-architecture--site-map-chrono-first)
5. [Narrative Program](#narrative-program)
6. [Governance & Templates](#governance--templates)
7. [Docs-as-Code Stack (Default & Backup)](#docs-as-code-stack-default--backup)
8. [14-Day Starter Plan (revised)](#14-day-starter-plan-revised)
9. [Knowledge Database & Atomization Pipeline](#knowledge-database--atomization-pipeline)
10. [Risks & Reversibility](#risks--reversibility)
11. [“Select Your Path” checklist (for records)](#select-your-path-checklist-for-records)

---

## Executive Overview Board (revised)

Each tile shows options with tradeoffs; the **Default** column is the current pick.

### 1) Audiences & Journeys

| Option                          | When it shines                   | Tradeoffs                     | Default       |
| ------------------------------- | -------------------------------- | ----------------------------- | ------------- |
| A1. Public Reader → story-first | Momentum; progressive disclosure | Less technical depth on entry | ✅             |
| A2. Collaborator → docs/tasks   | Clear onboarding                 | Feels dry to public           |               |
| A3. Future-Me → trail of Q/ADR  | Recall; low rework               | Requires metadata rigor       | ✅ (secondary) |
| A4. Domain Expert → whitepapers | Credibility                      | Slow to produce               |               |

**Criterion:** front-door story + back-door ops.

---

### 2) Narrative Spine

| Option                           | When it shines    | Tradeoffs           | Default |
| -------------------------------- | ----------------- | ------------------- | ------- |
| B1. Diegetic logs (in-universe)  | Unique voice      | Potential confusion |         |
| B2. Meta logs (real build notes) | Trust; repeatable | Less “magic”        | ✅       |
| B3. Editorial series (seasons)   | Habit-forming     | Planning overhead   | ✅       |
| B4. Artifact archaeology         | Long-tail value   | Needs stable IDs    |         |

**Criterion:** lead with **B2+B3**, seasonally mix **B1+B4**.

---

### 3) Information Architecture

> **Changed per your note: choose Chrono-First (C3).** Topic organization will live in a separate knowledge DB; logs will be atomized into it later.

| Option                                | When it shines               | Tradeoffs                             | Default |
| ------------------------------------- | ---------------------------- | ------------------------------------- | ------- |
| C1. Tri-rail: /story /docs /ops       | Clean separation             | Duplication                           |         |
| C2. Topic hubs                        | Task-oriented                | Heavier taxonomy                      |         |
| C3. **Chrono-first stream** + indices | Fast publish; scales by time | Topic discovery moves to knowledge DB | ✅       |

**Criterion:** prioritize shipping and a clean temporal trail.

---

### 4) Content Types & Taxonomy

| Option                                                 | When it shines    | Tradeoffs           | Default |
| ------------------------------------------------------ | ----------------- | ------------------- | ------- |
| D1. Atomic ladder (Atom→Note→Article→Brief→Whitepaper) | Natural growth    | Discipline required | ✅       |
| D2. Operational ladder (Q→ADR→Log→Release)             | Durable decisions | Admin overhead      | ✅       |
| D3. Free-tagging only                                  | Fast start        | Taxonomy rot        |         |

**Criterion:** D1+D2 with controlled tags; IDs are primary keys.

---

### 5) Governance & Workflow

| Option                  | When it shines    | Tradeoffs   | Default |
| ----------------------- | ----------------- | ----------- | ------- |
| F1. Solo roles (“hats”) | Clarity even solo | Ceremony    | ✅       |
| F2. PR-review gate      | Fewer mistakes    | Slower      | ✅       |
| F3. Publish-then-polish | Momentum          | Rough edges |         |

**Criterion:** F1+F2 with small DoP; allow emergency hotfix.

---

### 6) Visual/Brand System

> **Changed per your note: start ultra-minimal text (V0), later upgrade toward magazine.**

| Option                                                                       | When it shines         | Tradeoffs                | Default |
| ---------------------------------------------------------------------------- | ---------------------- | ------------------------ | ------- |
| V0. **Plain text baseline** (system font stack, minimal spacing, no imagery) | Fast, legible, durable | Aesthetic is austere     | ✅       |
| V1. Engineering-editorial (serif+mono, roomy grid)                           | Credible; readable     | More CSS/theming         |         |
| V2. Magazine (cards, photography, feature layouts)                           | Broad appeal           | Higher asset/design load |         |

**Criterion:** launch **V0**, schedule upgrades V1→V2 in slices.

---

### 7) SEO/Analytics & Growth

| Option                                       | When it shines    | Tradeoffs          | Default |
| -------------------------------------------- | ----------------- | ------------------ | ------- |
| H1. Semantic HTML + sitemaps + RSS + JSON-LD | Compounding SEO   | Setup time         | ✅       |
| H2. Privacy analytics (Plausible/Umami)      | No cookies; trust | Fewer GA features  | ✅       |
| H3. Newsletter + RSS                         | Direct channel    | Ongoing commitment |         |

**Criterion:** H1+H2 now; add newsletter once cadence stabilizes.

---

### 8) Legal/Privacy/Risk

| Option                                  | When it shines      | Tradeoffs           | Default |
| --------------------------------------- | ------------------- | ------------------- | ------- |
| I1. CC BY 4.0 (docs), Apache-2.0 (code) | Open yet protective | NOTICE files needed | ✅       |
| I2. Trademark policy                    | Prevents misuse     | Admin               | ✅       |
| I3. Contribution policy (DCO/CLA)       | Future collab       | Friction            |         |

**Criterion:** I1+I2 now; add I3 when PRs open.

---

### 9) Launch Slices

| Option                                                              | When it shines  | Tradeoffs     | Default |
| ------------------------------------------------------------------- | --------------- | ------------- | ------- |
| J1. **MVP**: Stream, Start-Here, indices (Q/ADR/Releases), 1 series | Validates pipes | Tiny scope    | ✅       |
| J2. v0.1: Search, RSS, sitemap, Pagefind, minimal brand             | Daily-usable    | Wiring effort |         |
| J3. v0.2: Comments (giscus), newsletter, contributor guide          | Community loop  | Moderation    |         |

**Criterion:** Ship J1 in week 2, line up J2 next.

---

## Decision Summary (locked)

* **IA:** **Chrono-First (C3)** with strong indices; topic organization handled by a **separate knowledge DB** via atomization.
* **Visual:** **V0 Plain Text Baseline** at launch, with planned upgrades to V1→V2 over time.
* All other defaults remain as previously set.

---

## Conceptual Model (text diagram)

```
Persona --reads--> Story <--narrates-- Log
Log --references--> Artifact
Log --raises--> Question (Q-YYYY-NNN)
Question --resolved_by--> Decision/ADR (ADR-YYYY-NNN)
Decision --affects--> Capability (CAP-xxx)
Capability --bundled_in--> Release (R-YYYY.M.m)
Artifact --included_in--> Release
Policy (POL-xxx) --governs--> {Log, Story, ADR, Artifact, Release}
Persona --contributes_to--> Artifact
Story --crosslinks--> {ADR, Q, Release, Artifact}
```

**Stable IDs:** `ADR-2025-001`, `Q-2025-009`, `R-2025.9.0`, `CAP-SIM-ECO-001`, `POL-PUB-001`, `ART-uuid`.

---

## Information Architecture & Site Map (Chrono-First)

**Top-level nav:** **Start Here** · **Stream** · **Indices** · **Releases** · **About** · **Search**

* **/stream/** (single chronological river of everything publishable)

  * `/<yyyy>/<mm>/<dd>/<slug>/` (all items live here; type is in front-matter + on-page badge)
  * Badges: `Story`, `Log`, `ADR`, `Q`, `Release`, `Artifact`, `Policy`
* **/indices/** (fast finders)

  * `/indices/decisions/` (ADR table w/ status, related Q, supersession)
  * `/indices/questions/`
  * `/indices/releases/`
  * `/indices/series/` (editorial series list)
  * `/indices/capabilities/` (lightweight index; deep topic navigation happens in knowledge DB)
* **/releases/R-YYYY.M.m/** (per-release landing; immutable notes + links)
* **/start/** (orientation, how to read, glossary, badges, IDs)
* **/about/** (project, licenses, contribution intent, contact)
* **URL pattern:**

  * Canonical: `/stream/YYYY/MM/DD/slug/`
  * Aliases for special objects (e.g., `/decisions/ADR-2025-001/` → 301 to canonical)
* **Breadcrumbs:**

  * `/stream/2025/09/06/build-diary-0/` → Start › Stream › 2025 › Sep › Build Diary #0
  * `/decisions/ADR-2025-003/` (alias) → redirects, landing shows ID prominently

**Write-path discipline:** everything is a dated post with type badges; indices are generated views over the stream.

---

## Narrative Program

**Recurring series:**

1. **Build Diaries** — weekly, meta voice; “what shipped/learned/blocked.”
2. **Why This Decision** — per ADR; 600–900 words; alternatives considered.
3. **Failures & Fixes** — post-mortems with template.
4. **Release Notes as Stories** — human narrative + diff.
5. **Artifact Archaeology** — resurface early drafts; lessons.

**Voice guidelines:** candid → concrete → reversible. Lead with the **question**, then the **change**, then **evidence**. Crosslink aggressively to Q/ADR/Release.

**Rhythm:** 1× Build Diary (Fri), 1× Decision/Failure (Wed), rolling doc updates. Seasons of 6–10 posts with intro/finale.

---

## Governance & Templates

**Solo roles (“hats”):** *CEO* (priorities), *Editor-in-Chief* (DoP gate), *Archivist* (IDs/redirects/backups), *Maintainer* (CI/CD/health).

**Definition of Publish (DoP) checklist**

* [ ] Stable ID + front-matter complete (title, date, type, series/tags, links)
* [ ] Crosslinks added (relevant ADR/Q/Release/Artifact)
* [ ] Redaction review (no sensitive personal data; license compliance)
* [ ] Lint: markdown passes; links valid; build green
* [ ] Changelog entry created

**Review cadence:** daily lint; weekly editorial pass; monthly taxonomy/redirect audit; monthly backup verification.

**Templates (copy as-is):**

*ADR-lite*

```markdown
---
id: ADR-2025-001
type: ADR
title: Short, Decision-Oriented Title
status: accepted|proposed|superseded
date: 2025-09-06
related_questions: [Q-2025-002]
impacts_capabilities: [CAP-SIM-ECO-001]
supersedes: []
superseded_by: []
---
## Context
## Decision
## Alternatives Considered
## Consequences (+/−)
## Links
```

*Q-Backlog*

```markdown
---
id: Q-2025-007
type: Q
title: Focused question
status: open|answered|closed
date: 2025-09-06
owner: role:name
related: [ADR-2025-001]
---
## Hypothesis / What changes if answered?
## Current best guess
## Next step / experiment
```

*Log (Meta)*

```markdown
---
id: LOG-2025-09-06-a
type: Log
series: build-diaries
tags: [week-xx, focus-area]
date: 2025-09-06
---
### What happened
### What changed (diffs/PRs)
### What I learned / Next
```

*Release Note*

```markdown
---
id: R-2025.9.0
type: Release
date: 2025-09-20
semver: 0.1.0
components: [site, taxonomy]
---
## Highlights (Story)
## Changes
- ...
## Upgrade Notes
## Links: PRs, ADRs, Issues
```

*Story Card*

```markdown
---
type: Story
series: failures-and-fixes
slug: integration-glitch-01
reading_time: 6
date: 2025-09-10
---
**Thesis:** One sharp lesson.
**Setup → Incident → Fix → Principle → Links**
```

---

## Docs-as-Code Stack (Default & Backup)

**Default (Pattern A):** *Git + Markdown + Astro* (Content Collections, MDX) + **Pagefind** search + **Cloudflare Pages** (or Netlify) + **GitHub Actions** CI + **giscus** (later)

* **Repo layout**

  ```
  /site
    /content/stream/                # all dated posts live here
    /content/indices/               # generated or thin wrappers
    /public
    /src/components
    /src/layouts
    astro.config.mjs
  /ops/templates/                   # raw md templates
  /scripts/                         # id checks, link-validate
  ```
* **Front-matter keys (minimum):** `id`, `type`, `title`, `date`, `series?`, `tags?`, `related?`
* **Environments:** PR → preview; main → prod
* **Backups:** mirror repo to GitLab; weekly tar to S3/Backblaze; monthly analytics export

**Backup (Pattern B):** *Git + Hugo* + **Pagefind** + **Cloudflare Pages**

* **Migration path:** keep content front-matter/IDs identical; port layouts/shortcodes; preserve URL scheme with `aliases`.

**Versioning & redirects:** IDs never change; slugs may—use `aliases` (301). ADR/Release immutable; supersede via `supersedes/superseded_by`.

---

## 14-Day Starter Plan (revised)

| Day | Task                                                                         | Output                    | Effort |
| --- | ---------------------------------------------------------------------------- | ------------------------- | ------ |
| 1   | Create repo; add licenses (CC BY 4.0 docs, Apache-2.0 code)                  | `LICENSE-docs`, `LICENSE` | 1h     |
| 2   | Scaffold Astro; create *Stream-first* routes                                 | Running dev server        | 3h     |
| 3   | Implement `/stream/YYYY/MM/DD/slug/` + type badges                           | Working stream            | 3h     |
| 4   | Minimal theme **V0** (system fonts, generous line-height, 1 column)          | Plain text baseline       | 2h     |
| 5   | Build **Indices** (ADR/Q/Release/Series)                                     | Filterable tables         | 4h     |
| 6   | Add Pagefind + RSS + sitemap + JSON-LD                                       | SEO plumbing              | 3h     |
| 7   | Author: **Start Here**, **Build Diary #0**, **ADR-2025-001**, **Q-2025-001** | 4 MD files                | 4h     |
| 8   | CI/CD via GitHub Actions; Cloudflare Pages deploy                            | Preview + prod            | 2h     |
| 9   | DoP checks (markdownlint, link checker); PR template                         | Quality gates             | 2h     |
| 10  | Write **Failure & Fix #1**; crosslink                                        | Post + links              | 3h     |
| 11  | Releases index; seed `R-2025.9.0` (planned)                                  | Release skeleton          | 2h     |
| 12  | Backups (repo mirror + tar to S3/B2)                                         | Resilience                | 2h     |
| 13  | Ops: `POL-PUB-001` (DoP + redaction), Templates dir                          | Policy + templates        | 3h     |
| 14  | **Hello, World Publish** (J1)                                                | Live site                 | 2h     |

**Hello, World (J1):** Stream live; Start-Here; Build Diary #0; ADR-2025-001; Q-2025-001; Indices (basic).

---

## Knowledge Database & Atomization Pipeline

**Goal:** keep the public site *chrono-first* while a separate **Knowledge DB** organizes concepts by topic for research and planning.

**Where it lives:** separate repo (`/knowledge-db`) using plain Markdown + a lightweight graph (e.g., `links.json`), or a notes system of your choice—tools are swappable; **content format is the contract**.

**Atomization rules**

* Every published post is a source. Extract “atoms” (claims, definitions, decisions, data points, TODOs).
* Atoms receive stable IDs aligned to sources:

  * `ATOM:LOG-2025-09-06-a#3` (3rd atom in that log)
  * `ATOM:ADR-2025-001#C` (Consequence C)
* Atom schema (YAML front-matter):

```markdown
---
id: ATOM:ADR-2025-001#1
source_id: ADR-2025-001
kind: decision|definition|principle|risk|todo|fact
created: 2025-09-06
links_out: [CAP-SIM-ECO-001, Q-2025-007]
status: live|revised|deprecated
---
Concise statement of the atom.
```

**Ingestion cadence:** weekly. Script scans `/site/content/stream/`, parses front-matter/headings, emits atoms into `/knowledge-db/atoms/`.

**Cross-system contract:** public site never depends on the Knowledge DB to build; DB references the site via IDs/URLs. When topic hubs are desired on the site, generate *static* topic pages from DB as *read-only builds* (no coupling).

---

## Risks & Reversibility

Risk | Early warning sign | Reversible move
\---|---|---|---
Chrono-only feels opaque for tasks | Readers can’t find “how-to” | Add task-focused index pages (generated, not authored)
Atomization overhead stalls | Backlog of un-atomized posts | Lower scope: atomize only ADR/Release first
Visual austerity underwhelms | High bounce on long posts | Ship V1 typography slice (serif headings, mono code, spacing)
Publishing stall | >14-day gaps | Switch to publish-then-polish; halve scope per post
ID drift | Broken crosslinks | Pre-commit ID linter; aliases on moves
Privacy/licensing | Takedown/email complaints | Redaction gate in DoP; hold sensitive drafts in PR until reviewed

---

## “Select Your Path” checklist (for records)

* **IA:** **C3 Chrono-First** ✅
* **Visual:** **V0 Plain Text** → V1 → V2 ✅
* **Narrative Spine:** **B2 Meta**, **B3 Editorial**, (periodic B1/B4) ✅
* **Stack:** **Pattern A (Astro)** default; **Hugo** backup ✅
* **SEO/Analytics:** H1 + H2 ✅
* **Licenses:** CC BY 4.0 (docs) + Apache-2.0 (code) ✅
* **Cadence:** 2 narrative + 1 doc/week ✅

---

### Implementation Notes (hand to the next chat)

* Treat this doc as the **source-of-truth brief**.
* Start with the **14-Day Plan** and ask the model to generate: repo tree, Astro content collections, minimal layout, and the four initial posts using the templates above.
* Enforce IDs and URL scheme exactly as written.
* Keep visual scope to **V0** until J1 is live; schedule V1 as a separate slice.
* Only after J1, add Pagefind/RSS/sitemap if not already in place, then proceed to J2/J3.
