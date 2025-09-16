---
id: "0-00-004"   # Use folder-position ID (Domain-Subdomain-FileNo). Stable, never changes even if title changes.
title: "Document Tagging & Summarization Instructions"   # Human title; may evolve.
status: draft        # draft | review | approved | archived
created: 2025-09-15
updated: 2025-09-15
tags: [type/guide, domain/system, metadata]   # Freeform now; you can normalize later.
summary: "Operational guidance and strict output schema for LLM-generated summaries and tags using a hybrid match+propose flow."

# ========= Optional Frontmatter (uncomment if needed) =========
# owner: "Role: Archivist"
# doc_type: guide
# relations: ["0-00-LLM-002"]
# permissions: internal
# license: CC-BY-4.0
# version: "0.1.0"
---

# LLM Tagging & Summarization Instructions

> **Summary:** This guide tells an LLM exactly how to read a Markdown document, propose a short summary, and generate tags by first matching against a master tag list and then optionally proposing new tags.  
> **Status:** {{ status }} • **Created:** {{ created }} • **Updated:** {{ updated }}  
> **Tags:** {{ tags | join(", ") }}

---

## 1. Purpose & Scope
- **Purpose:** Standardize LLM outputs for `summary` and `tags` fields in frontmatter.
- **Scope:** Any Markdown doc with or without existing frontmatter; hybrid tag workflow (match + propose).

## 2. Inputs Expected by the LLM
Provide these three blocks (verbatim headers help parsers):
1) **DOCUMENT_MARKDOWN** — The full Markdown, including frontmatter if present.  
2) **MASTER_TAG_LIST** — The current contents of `tag_inventory.md` (see template).  
3) **INSTRUCTIONS** — The prompt template below.

## 3. Output Required from the LLM (Strict)
Return **only** the following YAML fragment (no prose):

```yaml
summary: "<1–2 sentences, ≤50 words, plain English; what it is + why it exists>"
tags:
  matched: [tag-a, tag-b, tag-c]            # exact matches from MASTER_TAG_LIST
  proposed_new: [tag-x, tag-y]              # new candidates not found in MASTER_TAG_LIST
notes:
  - "1–3 bullets: rationale for chosen tags; mention ambiguities or tradeoffs"
confidence: 0.0-1.0                         # model’s self-estimated confidence
````

## 4. Rules & Constraints

* **Summary:** 1–2 sentences, ≤50 words, no hype, no future promises. Identify doc type if obvious (e.g., “ADR,” “checklist,” “retro”).
* **Tags (matched):** Prefer **exact** matches from MASTER\_TAG\_LIST; respect case and separators as listed.
* **Tags (new proposals):** 0–3 concise, **kebab-case** suggestions when no existing tag fits. Avoid near-duplicate synonyms.
* **Quantity:** Aim for **3–7 total** tags (matched + proposed). If many apply, choose the **most discriminative**.
* **No invention of IDs or metadata** beyond what’s requested.
* **PII/Safety:** Do not introduce sensitive information that isn’t present in the document.
* **Determinism:** If multiple equally valid tags exist, select those most consistent with prior choices in MASTER\_TAG\_LIST.

## 5. Procedure (What the LLM Should Do)

1. **Parse** frontmatter (if present) and body. Note any existing tags/summary.
2. **Draft summary** (≤50 words), reflecting purpose + contents. Do not copy sentences verbatim unless short.
3. **Generate candidate tags** (concepts, domains, doc-type, lifecycle, key entities/technologies).
4. **Cross-reference** candidates against MASTER\_TAG\_LIST → split into `matched` vs `proposed_new`.
5. **De-duplicate** and prune to the most informative 3–7.
6. **Emit YAML** exactly as specified above.

## 6. Edge Cases

* **Very short or empty docs:** Return `summary: "insufficient content for summary"` and `tags: { matched: [], proposed_new: [] }`, `confidence: 0.2`.
* **Index/MOC pages:** Prefer `type/index` or `type/moc` if present in tag list; otherwise propose them.
* **Highly technical docs:** Prefer domain/tech tags already in MASTER\_TAG\_LIST; only propose new if truly necessary.

## 7. Prompt Template (Copy/Paste)

Use this exact structure when calling an LLM:

```
You are an expert document classifier and summarizer.

=== MASTER_TAG_LIST (verbatim) ===
{{MASTER_TAG_LIST}}

=== DOCUMENT_MARKDOWN (verbatim) ===
{{DOCUMENT_MARKDOWN}}

=== TASK ===
1) Produce a 1–2 sentence summary (≤50 words) describing what this document is and why it exists.
2) Suggest 3–7 tags by first matching candidate tags against MASTER_TAG_LIST, then proposing up to 3 new tags only if needed.
3) Return only the YAML fragment in the exact schema below.

=== OUTPUT YAML SCHEMA (return exactly this shape) ===
summary: "<short summary>"
tags:
  matched: [tag-a, tag-b]
  proposed_new: [tag-x]
notes:
  - "why tag-a over synonym tag-a2"
confidence: 0.0-1.0
```

## 8. References

* Internal: `tag_inventory.md` (master tag list).
* Internal: `document template` (frontmatter fields consuming these outputs).

---

## Changelog

* **2025-09-15** • v0.1.0 • Initial guide drafted.

````

