---
id: "0-00-005"   # Use folder-position ID (Domain-Subdomain-FileNo). Stable even if title changes.
title: "Master Tag List (Tag Inventory)"
status: draft
created: 2025-09-15
updated: 2025-09-15
tags: [type/index, domain/system, metadata]
summary: "Single source of truth for approved tags; includes proposals, deprecations, and conventions."

# Optional
# owner: "Role: Archivist"
# doc_type: index
# relations: ["0-00-LLM-001"]
# permissions: internal
# license: CC-BY-4.0
# version: "0.1.0"
---

# Master Tag List (Tag Inventory)

> **Summary:** Authoritative list the LLM should match against. New tags may be proposed here, reviewed by you, and then moved to **approved**. Keep structure simple and machine-parsable.

---

## 1. Conventions (read once; keep short)
- **Case & separators:** use **kebab-case** (`disaster-recovery`), namespaces via `/` if desired (`type/adr`, `domain/system`).
- **Semantics:** tags should be **discriminative** (help retrieval), not generic (`misc`, `general`).
- **No duplicates:** prefer one canonical term; record synonyms under **aliases**.
- **Lifecycle:** if you replace a tag, record it under **deprecated** with `merged_into`.

## 2. Approved Tags (authoritative list)
> **This block is the list the LLM matches against.** Keep it alphabetized. One tag per line for easy diffing.

```yaml
approved_tags:
  - archive
  - backup
  - cadence
  - decision
  - disaster-recovery
  - domain/health
  - domain/projects
  - domain/system
  - governance
  - index
  - link-hygiene
  - metadata
  - phase/1
  - phase/2
  - security
  - type/adr
  - type/guide
  - type/index
  - type/moc
  - type/note
  - type/spec
````

> Add/remove tags **only** here; the LLM uses this exact list for matching.

## 3. Aliases (optional helpers for search; not for LLM matching)

> Use to document near-synonyms; keep this small. Scripts may consult aliases to recommend canonical tags.

```yaml
aliases:
  backup-and-restore: backup
  dr: disaster-recovery
  info-architecture: metadata
  toc: index
```

## 4. Proposed New Tags (staging area)

> LLM or you add proposals here. You triage monthly, then promote to **approved\_tags** or reject with rationale.

```yaml
proposed:
  - tag: redundancy
    rationale: "Frequent theme distinct from backup in X docs"
    proposed_by: "LLM"
    source_docs: ["0-05-123", "3-02-044"]
    date: 2025-09-15
    status: pending   # pending | accepted | rejected
```

## 5. Deprecated / Merged Tags

> Preserve history and redirects for clarity.

```yaml
deprecated:
  - tag: redundancy
    decision: "Merged into backup"
    date: 2025-10-01
    merged_into: backup
```

## 6. Notes

* Keep this file short and structured. Long explanations belong in a separate guide.
* If you introduce namespaces (e.g., `type/*`, `domain/*`, `phase/*`), add them organically; consolidate later.

---

## Changelog

* **2025-09-15** • v0.1.0 • Initial outline created with starter tags, proposals, and deprecation patterns.

```

---

If you want, I can also generate a **tiny Python script** later that:
- reads a document + this tag inventory,
- calls an LLM with the included prompt,
- and patches the doc’s frontmatter with the `summary` and `tags.matched` (while appending any `proposed_new` to the `proposed` section here).
```
