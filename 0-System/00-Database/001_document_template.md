---
# ========= Core Frontmatter v0 (keep minimal; expand as needed) =========
id: "0-00-001"            # Use folder-position ID (Domain-Subdomain-FileNo). Stable, never changes even if title changes.
title: "Document Template"         # Human title
status: draft     # draft | review | approved | archived
created: 2025-09-15
updated: 2025-09-15
tags: []          # e.g., [phase/1, type/spec, domain/system]
summary: ""       # 1–2 sentence abstract for search/index cards

# ========= Optional Frontmatter (uncomment if needed) =========
# slug: ""        # URL-safe identifier for publishing. Optional; can differ from id but should stay stable once set.
# owner: ""       # Primary maintainer (person or role). Helps with accountability.
# doc_type: ""    # Standardized type (note/spec/log/adr/index/moc/guide). Enables filtering.
# relations: []   # List of related doc IDs. Use stable ids only, never titles.
# aliases: []     # Alternate titles/labels for search. Use sparingly to avoid clutter.
# keywords: []    # Supplemental indexing hints (machine aid, not human tags).
# permissions: "" # Classification: public/internal/private/secret.
# license: ""     # Default license (e.g., CC-BY-4.0). Helps with publishing/export.
# version: ""     # Optional semantic version. Don’t confuse with id.
# toc: true       # Only include if your site tooling uses it. Optional.
---

<!--
AUTHORING GUIDE (keep or delete):
- Purpose: write for future-you + machines. Favor clarity, structure, and stable metadata.
- Tone: concise, declarative. One idea per paragraph. Prefer lists, tables, and examples.
- Dates: use ISO 8601 (YYYY-MM-DD). Numbers: use thousands separators where relevant.
- Links: use relative repo links or doc IDs; avoid duplicate sources (single source of truth).
- IDs: never change `id`. Use `relations` to cross-link. Use consistent tags (controlled vocab).
- Headings: H1 for title (once), H2 for top sections, H3 for subsections; avoid H4+ unless necessary.
- Reusability: keep “Summary” tight; “Key Takeaways” scannable; “References” link-rich.
- Machine-readability: frontmatter fields, stable headings, consistent section names enable indexing.
- Changelog: append entries at bottom (immutability of history; never rewrite past entries).
-->

# {{ title }}

> **Summary:** {{ summary }}  
> **Status:** {{ status }} • **Created:** {{ created }} • **Updated:** {{ updated }}  
> **Tags:** {{ tags | join(", ") }}

<!-- Optional: collapsible ToC if your renderer doesn't auto-generate -->
<details><summary><strong>Table of contents</strong></summary>

- [{{ title }}](#-title-)
  - [1. Purpose \& Scope](#1-purpose--scope)
  - [2. Background / Context](#2-background--context)
  - [3. Main Content](#3-main-content)
    - [3.1 Topic/Subsection](#31-topicsubsection)
    - [3.2 Topic/Subsection](#32-topicsubsection)
  - [4. Decisions (if any)](#4-decisions-if-any)
  - [5. Actions / Tasks](#5-actions--tasks)
  - [6. Risk \& Assumptions](#6-risk--assumptions)
  - [7. References](#7-references)
  - [8. Appendix (optional)](#8-appendix-optional)
  - [Changelog](#changelog)
</details>

---

## 1. Purpose & Scope
<!-- What this document is for, what it is not for. Define clear boundaries. -->
- **Purpose:**  
- **In/Out of Scope:**  
- **Audience / Consumers:**  

## 2. Background / Context
<!-- Prior work, constraints, definitions, and any relevant history. Keep this crisp and link out to sources. -->
- **Context:**  
- **Definitions / Glossary terms:**  
- **Prior docs:** (use `relations` in frontmatter and inline links here)

## 3. Main Content
<!-- Organize around questions, decisions, or components. Use H3 for subsections. -->
### 3.1 Topic/Subsection
- **Key points:**  
- **Details / Rationale:**  
- **Examples:**  

### 3.2 Topic/Subsection
- **Key points:**  
- **Details / Rationale:**  
- **Examples:**  

> **Note:** Prefer lists and short paragraphs. Use tables for comparisons; use code fences for snippets.

## 4. Decisions (if any)
<!-- For significant choices. If it’s a full ADR, use your ADR template; else summarize here and link. -->
- **Decision:**  
- **Alternatives considered:**  
- **Consequences:**  
- **Links:**  

## 5. Actions / Tasks
<!-- Actionable next steps. Keep each line atomic and verifiable. -->
- [ ] Task 1  
- [ ] Task 2  
- [ ] Task 3

## 6. Risk & Assumptions
- **Risks:**  
- **Mitigations:**  
- **Assumptions:**  

## 7. References
<!-- Prefer canonical sources. Use descriptive link text. -->
- [Title or source name](relative-or-absolute-link) — context
- [ ] Replace placeholders before approval

## 8. Appendix (optional)
<!-- Use for supporting tables, datasets, or extended examples the main flow doesn't need. -->

---

## Changelog
<!-- Append-only; newest at top. Date in ISO format. Keep entries short. -->
- **2025-09-15** • v0.1.0 • Initial draft created.

