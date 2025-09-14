---
id: 0201001
title: Phase 1 Outline
date: 2025-09-10
---

# Executive Summary

Phase 1 establishes **foundational concepts and topic areas** for a durable content and governance system. This outline is **concept-first** and keeps implementation choices **open**. It **defers to canon**:

* **002 Data Dictionary** — rules & conventions (naming, numbering, folder planning, reserved blocks).
* **003 File Manifest** — living inventory of the actual tree (0–9 domains).

All specifics that would constrain future options are left to **ADRs** created under `0-System` when/if we choose to narrow. Deviations from 002/003 require an ADR.

---

# 1. Posture & Principles (Conceptual)

* **Canon-respecting:** 002 and 003 are authoritative. This document **inherits** their constraints.
* **Topic-first:** Organize Phase‑1 by **topics** (conceptual surfaces) rather than immediate tooling or policy picks.
* **Decide-by-ADR:** Record consequential choices; avoid premature lock‑in.
* **Local-first, open formats:** Markdown as primary; portability and preservation matter.
* **Progressive disclosure:** Private depth now; later public summaries.

---

# 2. Canonical Constraints (Imported from 002 & 003)

**002 Data Dictionary (rules)**

* Top-level directories are **`0–9`** with `N_Label` naming; second level `NN-PascalCase`; optional third level PascalCase only.
* **File naming:** `XXX_snake_case_title.ext` with **reserved blocks** (`700s` logs/workshop, `800s` reference/support, `900s` archive/meta).
* **Folder planning process:** every folder starts with a **`README.md`** defining scope and numbering; files are pre‑numbered.
* **General standards:** front matter allowed; cross‑link by stable IDs or slugs; archived content moves to `900s` or `/9-Archive`.

**003 File Manifest (inventory)**

* Root domains: `0-System`, `1-Philosophy`, `2-Health`, `3-Work`, `4-Projects`, `5-Maintenance`, `6-Relationships`, `7-Recreation`, `8-Knowledge`, `9-Archive`.
* Manifest is a **living index** that must mirror reality and stay concise.

> **Implication for this doc:** 001 **does not invent alternate naming/numbering**. It references and uses the above. Any variance must be justified via ADR.

---

# 3. Topic Map for Phase 1 (Concept Surfaces)

Each topic lists **What/Why**, **Interfaces** (where it touches canon and other topics), **Open Questions**, and **Signals of Done** (conceptual, not tool‑specific).

## 3.1 Governance & Roles

**What/Why:** Minimal structures to ensure accountability, provenance, and safe change.
**Interfaces:** 003 `0-System`; 002 folder READMEs; ADR repository.
**Open Questions:** scope of roles (combined vs. separate), cadence intensity, review gates.
**Signals of Done:** role cards drafted, cadence calendar sketched, ADR process defined (template + states).

## 3.2 Information Architecture & Taxonomy

**What/Why:** Make information retrievable and evolvable without lock‑in.
**Interfaces:** 003 domain tree; 002 numbering rules; MOCs; tag schema.
**Open Questions:** tag schema minimal set; cross‑domain MOCs; ZK vs. MOC balance.
**Signals of Done:** top‑level MOCs per domain; tag schema v0; linking rules; folder README pattern.

## 3.3 Documentation Standards & Templates

**What/Why:** Consistency and speed of authoring.
**Interfaces:** 002 front matter and template expectations.
**Open Questions:** mandatory fields by type; minimal template pack.
**Signals of Done:** template pack v0 (ADR, README, Daily Log, Project Page, Retro, Changelog, Risk Register).

## 3.4 Search & Retrieval

**What/Why:** Find in <60s; reduce re‑work.
**Interfaces:** indexes (ADR Index, Project Index, Glossary, Tag Index, MOC Directory).
**Open Questions:** baseline search approach; index ownership; broken‑link policy.
**Signals of Done:** core indexes outlined; link‑check expectation documented.

## 3.5 Versioning & Change Management

**What/Why:** Trust history; enable experimentation.
**Interfaces:** ADRs; CHANGELOG conventions; folder‑level Changelogs.
**Open Questions:** canonical VCS vs. file‑only flow for media; release semantics for docs.
**Signals of Done:** change hygiene principles documented; example changelog entries.

## 3.6 Archiving & Digital Preservation

**What/Why:** Keep history available, safe, and lightweight.
**Interfaces:** 002 reserved `900s`; 003 `/9-Archive` domain; retention concepts.
**Open Questions:** retention bands by type; cold storage expectations; catalog granularity.
**Signals of Done:** archive decision rubric drafted; catalog skeleton defined.

## 3.7 Logging & Rhythm

**What/Why:** Narrative + operational trace (daily logs, project journals, retros).
**Interfaces:** 002 reserved `700s` for logs; 003 domain placement by context.
**Open Questions:** daily vs. weekly granularity; mood/valence inclusion; roll‑up method.
**Signals of Done:** daily log pattern; project journal outline; retro prompts.

## 3.8 Security, Privacy, Legal

**What/Why:** Reduce risk; protect provenance; respect licensing.
**Interfaces:** classification labels (`public/internal/private/secret`); license defaults.
**Open Questions:** minimal threat model; key custody norms; redaction workflow for public.
**Signals of Done:** classification labels documented; redaction notes captured; default license set.

## 3.9 AI Readiness (Structure Only)

**What/Why:** Prepare content for future AI usage without building the AI yet.
**Interfaces:** front‑matter fields; canonical link/ID usage; provenance notes.
**Open Questions:** minimum fields for ingestion; supersede relationships; eval seed philosophy.
**Signals of Done:** ingestion contract sketch; list of must‑have fields; eval idea bank started.

## 3.10 Public‑Facing Scaffold

**What/Why:** Enable later publishing without committing to content now.
**Interfaces:** internal → public mapping via MOCs; editorial gates; accessibility intent.
**Open Questions:** which internal MOCs map 1:1; redaction thresholds.
**Signals of Done:** publishing checklist outline; editorial roles acknowledged.

## 3.11 Operations & Reliability (DocsOps)

**What/Why:** Keep the documentation system healthy.
**Interfaces:** backup expectations; restore drills; monitoring ideas.
**Open Questions:** RTO/RPO targets; drill cadence; metrics collection.
**Signals of Done:** backup expectations written; restore drill description drafted.

## 3.12 Data & Media Management

**What/Why:** Tame assets; guarantee openability.
**Interfaces:** formats guidance; alt‑text/captions; checksum habits.
**Open Questions:** LFS vs. bucket pointer files; derivative generation policy.
**Signals of Done:** asset directory pattern; alt‑text guidance; checksum note.

## 3.13 Measurement & Telemetry

**What/Why:** See if it works; steer improvements.
**Interfaces:** findability; coverage; cadence health; change hygiene; resilience.
**Open Questions:** baseline metrics; feasible collection without heavy tooling.
**Signals of Done:** metric definitions written; baseline plan described.

---

# 4. Non‑Decisions (Intentionally Open in 001)

To avoid premature narrowing, **001 does not**:

* Select specific tools/vendors (e.g., search engine, SSG, note app, PM tool).
* Finalize semantic search, embedding strategies, or KG schemas.
* Fix retention durations, backup technologies, or encryption products.
* Choose public site stack or analytics provider.

All such choices are deferred to ADRs as needed.

---

# 5. Definition of Done (Conceptual, Phase 1)

* **Topics mapped:** Each topic in §3 has (a) a short rationale, (b) interfaces noted, (c) open questions, and (d) conceptual signals of done.
* **Canon alignment:** This doc references 002/003; no conflicts introduced.
* **ADR pathway:** A numbered list of potential ADRs is identified (titles only), with a template available.
* **Template pack v0:** Minimal authoring kit exists (even as stubs) aligned with 002.
* **Indexes sketched:** ADR Index, Project Index, Glossary, Tag Index, MOC Directory have placeholders.

---

# 6. ADR Hooks (Titles Only; to be created in `0-System/decisions/`)

1. ADR‑001: **Adoption of 002/003 as Canon and Variance Policy**
2. ADR‑002: **Top‑Level MOC Strategy (per 003 domains)**
3. ADR‑003: **Tag Schema v0 and Governance**
4. ADR‑004: **Linking Rules (IDs, backlinks, See‑also)**
5. ADR‑005: **Change Hygiene & Changelog Conventions**
6. ADR‑006: **Archive Catalog & Retention Rubric**
7. ADR‑007: **Security Classification & Redaction Flow**
8. ADR‑008: **Template Pack v0 (types, required sections)**
9. ADR‑009: **Index Ownership & Broken‑Link Policy**
10. ADR‑010: **Backups & Restore Drill Expectations**

> Note: Numbers here are placeholders for clarity; actual file numbers follow 002’s `XXX_` scheme within the `decisions` area.

---

# 7. Risks & Tensions (to watch conceptually)

* **Over‑engineering vs. drift:** Keep topic surfaces small but durable; iterate inside them.
* **Vocabulary sprawl:** Own the tag schema and MOC directory early.
* **Lock‑in:** Prefer patterns over products; document export tests later.
* **Bit‑rot:** Make restoration a habit, not an emergency.

---

# 8. Working Practices & Cadence (Lightweight)

* **Weekly:** quick tactical sweep (backlog/notes), triage open questions, pick ADRs to draft.
* **Monthly:** maintenance sweep and retro; update 003 manifest if structure changed.
* **Quarterly:** small audit of IA/tagging and risk list.

> Times and tools are **intentionally unspecified**; only the rhythm pattern is noted.

---

# 9. Interfaces & Pointers

* **002 Data Dictionary:** authoritative rules for naming/numbering, reserved blocks, folder planning.
* **003 File Manifest:** authoritative, living tree of what exists.
* **000 Zero Draft:** high‑level mission & principles.

---

# Appendix A — Minimal Template Stubs (Conceptual)

> These are stubs; implement as real files following 002 conventions.

**`README.md` (folder)**

* Purpose & scope
* Numbering plan (hundreds/tens bands)
* Local vocabulary and cross‑links
* Change notes (link to folder `Changelog.md`)

**ADR**

* Context
* Options
* Decision
* Consequences
* Status (Proposed/Accepted/Superseded)

**Daily Log**

* bullets for actions/insights/blockers (optionally mood/valence)
* links to touched artifacts

**Retro**

* Went well / Pain points / Lessons / Changes

**Project Page**

* Goal, scope, milestones
* Links to logs/specs/ADRs

**Changelog**

* Date — change summary — author — links

---

# Change Log (this document)

* **2025‑09‑11 v2.0.0** — Recast 001 as **conceptual & topical**; removed prescriptive naming/versioning that conflicted with 002; anchored to 003’s domain map; left tool choices open; added ADR hooks and conceptual signals of done.

---

# Appendix B — Prospective Ideas Backlog (from former Phase 1 Outline v1.x)

> Purpose: preserve **every notable idea** from the earlier, more prescriptive Phase‑1 outline as **prospects** to explore. Nothing here is a commitment. Items marked **\[Narrow v1]** reflect choices that would intentionally narrow scope if adopted. **Canon note:** all implementations must comply with **002 Data Dictionary** (naming/numbering, reserved blocks, folder planning) and **003 File Manifest** (0–9 domains).

## B.1 Governance & Roles

* Draft a **Constitution** (mission/values, scope, authority, amendment process). \[Narrow v1]
* **Content lifecycle policy** with states `draft/review/approved/deprecated/archived`, owners, SLAs, review intervals. \[Narrow v1]
* **Definition of Publish** (internal vs public thresholds; redaction rules). \[Narrow v1]
* **Compliance/Ethics** policy (IP, privacy, attribution, provenance, acceptable use). \[Narrow v1]
* **Minimum Viable Roles**: Strategist, Steward of Knowledge, Archivist, Maintainer, Editor, Security Custodian, Reviewer. \[Narrow v1]
* **RACI** for add/edit/publish/archive; taxonomy changes; ADR process. \[Narrow v1]
* Cadences: **Weekly** tactical; **Monthly** maintenance + retro; **Quarterly** audit; **Annual** restoration test. \[Narrow v1]
* **ADR discipline**: template (Context/Options/Decision/Consequences/Status), immutability, supersede chain. \[Narrow v1]

## B.2 Information Architecture & Taxonomy

* Hybrid IA **P.A.R.A. + Johnny.Decimal + Zettelkasten** with **MOCs** as curated entry points. \[Narrow v1]
* **Top‑level scaffolding**: `/Projects`, `/Areas`, `/Resources`, `/Archive` mapped onto 003 domains. \[Narrow v1]
* **Naming conventions**: stable slugs; abbreviation registry; reserved words; case/spacing rules. \[Narrow v1]
* **Controlled vocabulary**: tag schema `domain/topic/process/status/audience/privacy`; synonyms table; merge/deprecate rules; owner & change flow. \[Narrow v1]
* **Ontology scaffold**: glossary; entities (People/Orgs/Projects/Artifacts/Events/Places); relations (created\_by, supersedes, depends\_on, relates\_to). \[Narrow v1]
* **Cross‑linking rules**: Related ADRs, Related MOCs, Next actions; inline/backlinks/see‑also blocks. \[Narrow v1]

## B.3 Documentation Standards & Templates

* **Template pack**: Charter, Role Card, ADR, SOP/Runbook, Spec/Design Doc, Meeting Notes, Daily Log, Project Page, Retro, Changelog, Risk Register, Decision Log Index, Publishing Checklist. \[Narrow v1]
* **YAML front matter (Personal Dublin Core)** with fields: `title,id,owner,created,modified,status,type,tags,relates_to,version,privacy,license`. \[Narrow v1]
* **Style**: concise, declarative; 1‑paragraph summary; headings; lists; diagrams via Mermaid as needed. \[Narrow v1]
* **Mandatory sections by type** (e.g., Specs include Goals/Non‑goals/Interfaces/Risks/Eval). \[Narrow v1]

## B.4 Search, Indexing & Retrieval

* **Baseline**: full‑text across vault; index front matter; curated **Indexes** (ADR, Project, Glossary, Tag, MOC Directory). \[Narrow v1]
* **Advanced**: semantic/embedding search; per‑domain re‑ranking; synonym maps; “did you mean”; scoped queries by type/status/tag/date/owner/privacy. \[Option]
* **Offline index for archives** with separate shard to reduce active clutter. \[Option]
* **Findability metrics**: time‑to‑find < 30s; **zero broken links** in CI; query analytics → taxonomy improvements. \[Narrow v1]

## B.5 Version Control & Change Management

* **Git canonical for text**; main + short‑lived branches; squash merges; **signed tags** for releases. \[Narrow v1]
* **Large media** via Git LFS or external bucket with pointer files + metadata. \[Narrow v1]
* **Non‑Git artifacts**: filename versioning + revision tables. \[Narrow v1]
* **Conventional commits** (e.g., `feat(doc):`, `chore(taxonomy):`, `docs(adr):`). \[Narrow v1]
* Root **CHANGELOG.md** for system‑level IA/taxonomy/review changes. \[Narrow v1]
* **CI checks**: front‑matter present, link integrity, filename policy, forbidden terms. \[Narrow v1]

## B.6 Archiving & Digital Preservation

* **Archive criteria**: deprecated > N months; completed projects; superseded specs; stale logs beyond retention. \[Narrow v1]
* **Retention matrix** by artifact type; privacy‑aware deletions as needed. \[Narrow v1]
* Storage model: separate **read‑only** archive tree; duplicate to **offsite cold storage**. \[Narrow v1]
* **Preferred formats**: Markdown primary; PDF/A for finalized; PNG/TIFF images; MP4 (H.264/H.265) video; FLAC/WAV audio. \[Narrow v1]
* **Integrity**: checksums; annual media refresh; openability tests. \[Narrow v1]
* **Archive Catalog** with summaries/owners/retention/location; optional offline semantic index; retrieval SOP. \[Narrow v1]

## B.7 Logging & Rhythm

* **Daily logs** (3–7 bullets: actions, blockers, insights, mood/valence optional) with links to touched artifacts; tag `daily-log`. \[Narrow v1]
* **Project journals** (weekly entries, milestones). \[Narrow v1]
* **Retrospectives** using standard template. \[Narrow v1]

## B.8 Backlog & Workflow

* **Plain‑text Kanban** (To Do / Doing / Done) or chosen PM tool, with **cross‑links** between tasks and artifacts. \[Narrow v1]
* **Recurring tasks**: reviews, backups, linting, restores, link sweeps. \[Narrow v1]

## B.9 Tooling & Integration

* **File‑based canonical** (Markdown + Git). \[Narrow v1]
* **Optional mirrors/adapters**: Obsidian (graph/backlinks), Notion/Confluence (team wiki), static site generator. \[Option]
* **Productivity/PM**: Trello/Asana/Jira or plaintext; exportability required. \[Option]
* **Capture & automation hooks**: quick capture note; email‑to‑note; web clipper; meeting → auto‑note shell; calendar → meeting‑note template; “TODO:” harvest script → backlog. \[Option]

## B.10 Docs CI/CD

* **Pre‑commit hooks**: front‑matter, filenames, link‑check, lint/spellcheck, diagram render; SSG staging if used. \[Narrow v1]
* **Sitemap** generation if publishing pipeline exists. \[Option]

## B.11 Diagrams & Media

* **Mermaid** for quick diagrams; draw\.io/Excalidraw for richer visuals. \[Option]
* **Asset pipeline**: alt text, captions, credits, licenses recorded. \[Narrow v1]

## B.12 Security, Privacy, Legal

* **Threat model** & baseline controls. \[Narrow v1]
* **Device hardening**; encrypted disks; password manager; 2FA/U2F keys. \[Narrow v1]
* **Access controls**: repo permissions; secret scanning; least privilege. \[Narrow v1]
* **Data classification**: `public/internal/private/secret`; storage/sharing rules per class. \[Narrow v1]
* **PII handling & redaction workflows**; audit logs. \[Narrow v1]
* **Licensing & provenance**: default license; third‑party license registry; attribution fields; optional watermarking for public releases. \[Narrow v1]

## B.13 AI Readiness (Structure Only)

* **Ingestion contract**: fields/IDs/links AIs rely on; `superseded_by` relationships. \[Narrow v1]
* **Eval seed sets**: retrieval QA; doc coverage tests; hallucination traps. \[Option]
* **PII filters/redaction** prior to embedding. \[Narrow v1]
* **Ontology scaffold** for future KG export. \[Option]
* **Prompt libraries & SOPs** (draft); **RAG architecture sketch** (later). \[Option]

## B.14 Public‑Facing & Communications

* Public site IA mirrors **internal MOCs**; content gating. \[Narrow v1]
* **Editorial board**, style guide, inclusive language, accessibility baseline. \[Narrow v1]
* **SEO basics** (titles/meta/sitemap); **analytics policy**; privacy/cookie notice. \[Narrow v1]
* **Release workflow** (internal doc → public post) with legal checks & review gates. \[Narrow v1]

## B.15 Operations & Reliability (DocsOps)

* **SLOs**: RTO/RPO for vault; site uptime (later). \[Option]
* **Monitoring**: backup success, CI health, broken link count, index freshness. \[Narrow v1]
* **Restore drills**: quarterly; measure time‑to‑restore; log outcomes. \[Narrow v1]
* **Runbooks**: incident response for content loss/security events. \[Narrow v1]

## B.16 Data & Media Management

* **Asset directories**; naming & versioning; alt‑text policy; captions & transcripts. \[Narrow v1]
* **Large‑file strategy**: LFS/buckets; checksum tables; derivative generation (thumbnails, compressed). \[Narrow v1]

## B.17 Measurement & Telemetry

* Metrics: **Findability**, **Coverage** (metadata/template compliance), **Cadence health**, **Change hygiene** (ADR coverage; supersede chain intact), **Resilience** (backup success; restore time). \[Narrow v1]

## B.18 Milestones & Roadmap (Illustrative)

* **M0 (Week 0)**: Ratify Charter + roles + cadence calendar; create ADR‑000 index. \[Narrow v1]
* **M1 (Weeks 1–2)**: IA skeleton; naming/tag v1; template pack; YAML schema. \[Narrow v1]
* **M2 (Weeks 3–4)**: ADR repo live; daily/project logs; search index + indexes/MOCs. \[Narrow v1]
* **M3 (Weeks 5–6)**: Versioning policy; archive policy; backup jobs; first restore drill. \[Narrow v1]
* **M4 (Weeks 7–8)**: Docs CI checks; security baseline; vocabulary audit #1. \[Narrow v1]
* **M5 (Weeks 9–10)**: Quarterly governance/IA review; first full retro; metrics baseline. \[Narrow v1]

## B.19 Risks & Mitigations (Watchlist)

* **Over‑engineering** ↔ MVP gates + cadence iteration. \[Narrow v1]
* **Vocabulary drift** ↔ owner + audits; synonyms table; deprecations. \[Narrow v1]
* **Lock‑in** ↔ open formats; export tests; mirrors secondary. \[Narrow v1]
* **Bit rot/data loss** ↔ 3‑2‑1+, checksums, restores; media refresh. \[Narrow v1]
* **Permission mishaps** ↔ classification labels; PR reviews; pre‑publish checklist. \[Narrow v1]
* **Decision amnesia** ↔ ADR discipline; index; immutable history. \[Narrow v1]

## B.20 Initial ADR Set (Titles)

1. Canonical knowledge repo (Markdown+Git vs wiki‑first). \[Narrow v1]
2. Top‑level IA (P.A.R.A.+JD+MOC) & naming standard v1. \[Narrow v1]
3. Review cadence & maintenance scope. \[Narrow v1]
4. Versioning strategy (Git flow, LFS policy). \[Narrow v1]
5. Archive & preservation policy (formats, retention, catalog). \[Narrow v1]
6. Security baseline (encryption, access, keys, secret scanning). \[Narrow v1]
7. Front‑matter schema v1 (fields & requiredness). \[Narrow v1]
8. Publishing policy (internal ↔ public, redaction, licensing). \[Narrow v1]
9. Search/indexing approach (baseline + future semantic). \[Narrow v1]
10. Tag/vocabulary governance (owners, change flow, audits). \[Narrow v1]

## B.21 Open Questions (Q‑Log, to revisit)

* Minimal viable metadata set vs deferred fields? \[Narrow v1]
* PARA boundaries (Projects vs Areas edge cases)? \[Narrow v1]
* Johnny.Decimal ranges: how many to start; when to split? \[Narrow v1]
* Frequency/scope of maintenance sweeps; who approves deprecations? \[Narrow v1]
* Which automations remove the most friction on day one? \[Narrow v1]
* Public‑facing path: which internal MOCs map 1:1 to public nav? \[Narrow v1]

## B.22 Starter Backlog (Next Actions Candidates)

* Draft **Charter** + role cards + cadence calendar. \[Narrow v1]
* Ship **IA skeleton** (root tree, folder READMEs); **naming/tag standard v1**. \[Narrow v1]
* Initialize **ADR repo** (`/0-System/decisions`), index file; adopt ADR template. \[Narrow v1]
* Publish **templates** + **front‑matter schema**; enable pre‑commit checks. \[Narrow v1]
* Stand up **search** + core **indexes** (ADR/Project/Glossary/MOCs). \[Narrow v1]
* Configure **backups** (3‑2‑1+), set up **Git** (+LFS if needed); run **restore drill**. \[Narrow v1]
* Start **daily logs** and **weekly review**; create **metrics** scaffold. \[Narrow v1]

## B.23 Appendix Skeletons (for later expansion)

* **A. Templates** (ADR, SOP, Spec, Meeting, Retro, Daily Log, Project Page, Changelog). \[Narrow v1]
* **B. Front‑matter schema** (YAML), enums. \[Narrow v1]
* **C. Tag vocabulary v1** + synonyms table. \[Narrow v1]
* **D. Naming standard** cheatsheet. \[Narrow v1]
* **E. Backups & Restore** runbook. \[Narrow v1]
* **F. CI policy** (linters, link‑check, front‑matter, filename). \[Narrow v1]
* **G. Risk register** fields + starter risks. \[Narrow v1]
* **H. Publishing checklist** (internal→public). \[Narrow v1]
* **I. Tool evaluation matrix** (portability, export, cost, collab, automation). \[Narrow v1]

# Change Log (this document)

* **2025‑09‑11 v2.0.0** — Recast 001 as **conceptual & topical**; removed prescriptive naming/versioning that conflicted with 002; anchored to 003’s domain map; left tool choices open; added ADR hooks and conceptual signals of done.

