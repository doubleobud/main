---
id: "0-10-101"
title: "System — Start Here"
status: draft
created: 2025-09-15
updated: 2025-09-15
tags: [guide, database]
summary: "Central orientation page for the System domain—what lives here, how to navigate, and where to start."
---

## Table of Contents
- [System Start Here (All-in-One Database Guide)](#system-start-here-all-in-one-database-guide)
  - [1. Quick Links (Core Hubs)](#1-quick-links-core-hubs)
  - [2. Data Dictionary (Sub-Sections A-G)](#2-data-dictionary-sub-sections-a-g)
    - [A. Data Dictionary Purpose](#a-data-dictionary-purpose)
    - [B. Directory Architecture](#b-directory-architecture)
    - [C. Folder Naming Convention](#c-folder-naming-convention)
    - [D. File Naming Convention](#d-file-naming-convention)
    - [E. File/Folder Numbering System](#e-filefolder-numbering-system)
      - [a. Hundreds-Level](#a-hundreds-level)
      - [b. Tens-Level](#b-tens-level)
      - [Reserved Blocks](#reserved-blocks)
    - [F. The Folder Planning Process](#f-the-folder-planning-process)
    - [G. Notes](#g-notes)
  - [3. Front Matter Standards](#3-front-matter-standards)
    - [A. Front Matter Template (YAML)](#a-front-matter-template-yaml)
    - [B. Front Matter Summary Instructions](#b-front-matter-summary-instructions)
      - [a. Length \& Style](#a-length--style)
      - [b. Content](#b-content)
      - [c. Constraints](#c-constraints)
      - [d. Example](#d-example)
    - [C. Front Matter Tagging Instructions](#c-front-matter-tagging-instructions)
      - [a. Generate Candidate Tags](#a-generate-candidate-tags)
      - [b. Match and Propose Tags](#b-match-and-propose-tags)
      - [c. Refine and Finalize](#c-refine-and-finalize)

---

# System Start Here (All-in-One Database Guide)

> **What this is:** The authoritative index for humans and LLMs to understand the database system: concepts, schemas, pipelines, conventions, governance, and how to contribute.  
> **Audience:** Engineers, analysts, PMs, and automation/LLMs.  
> **How to use:** Skim the TOC and jump to a section. Each section is self-contained and links to deeper references.

---

## 1. Quick Links (Core Hubs)
- **Master MOC (Navigation):** [/0-System/00-Database/201_moc_master.md](/0-System/00-Database/201_moc_master.md)
- **Master Index (Index of Indexes):** [/0-System/00-Database/202_master_index.md](/0-System/00-Database/202_master_index.md)
- **File Manifest (living inventory):** [/0-System/00-Database/003_file_manifest.md](/0-System/00-Database/203_file_manifest.md)
- **Tag List:** [/0-System/00-Database/204_tag_list.md](/0-System/00-Database/204_tag_list.md)

---

## 2. Data Dictionary (Sub-Sections A-G)

### A. Data Dictionary Purpose
This document defines the **rules, standards, and conventions** of the file system.  
Unlike the **File Manifest** (which changes often), the Data Dictionary is **updated only when policies evolve**.

### B. Directory Architecture
- **Top Level (Single Digit):** 0–9 folders, each representing a major domain.
- **Second Level (Two Digits, PascalCase):** 00–99 subfolders per top-level, descriptive names in PascalCase.
- **Rule:** Folders should be shallow but durable. Each folder must contain a **`README.md`** explaining its scope and the specific design of its internal three-digit numbering system.

### C. Folder Naming Convention
- **Format (Top Level):** `N_Label`  
- **`N`:** A single digit (`0–9`) representing the major domain.  
- **`Label`:** PascalCase descriptor of the domain.  
  - **Example:** `1-Philosophy`

- **Format (Second Level):** `NN-PascalCase`  
- **`NN`:** Two digits (`00–99`) unique within the parent folder.  
- **`PascalCase`:** Clear, descriptive name.  
  - **Example:** `03-WorkflowDesign`

- **Format (Optional Third Level):** See Hundred-Level instructions

### D. File Naming Convention
- **Format:** `XXX_snake_case_title.ext`
- **`XXX`:** A three-digit number (`000–999`) for permanent position within a folder.
- **`snake_case_title`:** Short lowercase description of contents.

**Example:** `031_wireframe_for_homepage.svg`

---

### E. File/Folder Numbering System

#### a. Hundreds-Level
- The **hundreds digit (`X00–X99`)** represents high-level categories within a folder.  
- These categories may be implemented in two ways:
  1. **Direct numbering** — files use the hundreds band without extra folders.  
     - Example: `101_training_log.md`, `205_meal_plan.xlsx`  
  2. **Hundreds-level subfolder** — a folder named for the category, inside which files still follow the numbering convention.  
     - Example: `/200-Nutrition/210_meal_plan.xlsx`  
- Each folder defines its own hundreds-level scheme in its local `README.md`. There is **no global taxonomy**.  

**Examples:**
- In `/Health`:  
  - `100s Fitness` (could be direct files like `101_run_log.md` or a folder `100-Fitness/`)  
  - `200s Nutrition`  
  - `300s Medical Records`  
- In `/Projects`:  
  - `100s Research`  
  - `200s Drafts`  
  - `300s Deliverables`

#### b. Tens-Level
- The **tens digit (`xX0–xX9`)** is for custom sub-categories.  
- Defined within the folder's local **`README.md`**.  
- Example: `210-Mockups`, `220-DesignSystems`.

#### Reserved Blocks
- **700s — Workshop & Logs**: Meeting notes, email dumps, brainstorming.  
- **800s — Reference & Support**: Manuals, tutorials, external resources.  
- **900s — Archive & Meta**: Deprecated files and old versions.

---

### F. The Folder Planning Process
1. **Every folder begins with its `README.md` file.** 2. The folder’s **`README.md`** defines:
   - Its scope and purpose
   - Hundreds-level categories
   - Tens-level custom sub-categories
   - File assignments
3. Files are numbered **before creation** to enforce planning.

---

### G. Notes
- The **File Manifest** = A global inventory of the system's current state (changes frequently).
- The **Data Dictionary** = The universal rules of the game (changes slowly).
- A **Folder's README** = The local rules and inventory for that specific folder.

---

## 3. Front Matter Standards

### A. Front Matter Template (YAML)

---
id: "0-00-000"            # Use folder-position ID (Domain-Subdomain-FileNo). Stable, never changes even if title changes.
title: "Document Template"         # Human title
status: draft     # draft | review | approved | archived
created: 2025-09-15
tags: []          # e.g., [start-up, templates]
summary: "Document summary here."       # 1–2 sentence abstract for search/index

---

### B. Front Matter Summary Instructions

#### a. Length & Style
- Keep it 1–2 sentences, ≤50 words.
- Use plain English with no hype or marketing tone.

#### b. Content
- Explain what the document is and why it exists (its purpose).
- Identify the document type if obvious (e.g., “ADR,” “guide,” “retro”).
- Do not copy long sentences from the document body; rephrase concisely.

#### c. Constraints
- Avoid promises, speculation, or future tense.
- Do not introduce new information not present in the document.
- Ensure the summary will remain valid even if minor details in the doc change.

#### d. Example
- Summary: "Guide defining standards for tagging and summarization to ensure consistent metadata across Markdown documents."

---

### C. Front Matter Tagging Instructions

#### a. Generate Candidate Tags
-Read the document and generate a broad internal list of 10-15 potential tags. These "candidate tags" should identify:

  Core Concepts: The main ideas or subjects (e.g., system-rules, file-naming, metadata).
  Document Type: The document's structural purpose (e.g., guide, index, list, policy, template).Domain: The high-level area the document belongs to (e.g., governance, projects, health).Guiding Principle: Aim for concepts that can group this document with others. Avoid tags that are hyper-specific and would only apply to this single document.

#### b. Match and Propose Tags
- Using the `MASTER_TAG_LIST` as a reference, categorize your candidate tags:
- Place any **exact matches** between the generated tag list and the master tag list into the `matched` array.
- If a concept is not covered, create a new tag and place it in the `proposed_new` array. You may propose up to 5 new tags, which must be in **kebab-case**. List the tags in the order of applicability from first to last.

#### c. Refine and Finalize

- Ensure the total number of tags (both matched and proposed) is between **3 and 7**. Choose the most specific and descriptive tags if you have too many.
- Construct the final YAML block exactly as shown above, adding brief notes to explain your choices and a confidence score.

---

