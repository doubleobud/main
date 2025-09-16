---
id: "0-00-008"   # Adjust to this file’s folder position; stable once set.
title: "Database Decision Log (MVP)"
status: draft
created: 2025-09-15
updated: 2025-09-15
tags: [type/index, governance, domain/system]
summary: "Append-only, one-line records of key project decisions with terse rationale."
---

# Decision Log (MVP)

> **Pattern:** `YYYY-MM-DD • CODE — Title — status — note`  
> **Rules:** Append-only. Don’t edit history; supersede via a new line if reversed.

- 2025-09-07 • ADR-000 — Adopt phased roadmap (Zero Draft) — approved — phases 1–11 anchor.
- 2025-09-15 • ADR-001 — Choose Git for version control — approved — durable history & tooling.
- 2025-09-15 • ADR-002 — Use Markdown as primary format — approved — portable, diffable, low-friction.
- 2025-09-15 • ADR-003 — Numbered directory architecture — approved — predictable navigation & planning.
- 2025-09-15 • ADR-004 — Minimal website via GitHub Pages — approved — single `index.html` approach.
- 2025-09-15 • ADR-005 — Frontmatter v0 + doc template — approved — machine-readable metadata baseline.
- 2025-09-15 • ADR-006 — IDs derive from hierarchy — approved — title mutable; id immutable.
- 2025-09-15 • ADR-007 — Dual navigation: MOCs + Indexes — approved — curated hubs + exhaustive lists.
- 2025-09-15 • ADR-008 — Tagging strategy: LLM match+propose — approved — human review; master list later.
---

## How to add a new decision (one line)
- **Template:** `YYYY-MM-DD • ADR-### — Short title — status — <≤12-word note>`

## Optional: expand later
- If a decision needs detail, create a separate ADR file and link it here.
