# Data Dictionary

## Purpose
This document defines the **rules, standards, and conventions** of the file system.  
Unlike the **File Manifest** (which changes often), the Data Dictionary is **updated only when policies evolve**.

---

## Directory Architecture
- **Top Level (Single Digit):** 0–9 folders, each representing a major domain.
- **Second Level (Two Digits, PascalCase):** 00–99 subfolders per top-level, descriptive names in PascalCase.
- **Rule:** Folders should be shallow but durable. Each folder must contain a **`README.md`** explaining its scope and the specific design of its internal three-digit numbering system.

---

## Folder Naming Convention
- **Format (Top Level):** `N_Label`  
- **`N`:** A single digit (`0–9`) representing the major domain.  
- **`Label`:** PascalCase descriptor of the domain.  
  - **Example:** `1-Philosophy`

- **Format (Second Level):** `NN-PascalCase`  
- **`NN`:** Two digits (`00–99`) unique within the parent folder.  
- **`PascalCase`:** Clear, descriptive name.  
  - **Example:** `03-WorkflowDesign`

- **Format (Optional Third Level):** `PascalCase` only (no numeric prefix).  
  - Used sparingly for sub-organization.  
  - **Example:** `Assets` or `Logs`

---

## File Naming Convention
- **Format:** `XXX_snake_case_title.ext`
- **`XXX`:** A three-digit number (`000–999`) for permanent position within a folder.
- **`snake_case_title`:** Short lowercase description of contents.

**Example:** `031_wireframe_for_homepage.svg`

---

## Numbering System

### Hundreds-Level
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

### Tens-Level
- The **tens digit (`xX0–xX9`)** is for custom sub-categories.  
- Defined within the folder's local **`README.md`**.  
- Example: `210-Mockups`, `220-DesignSystems`.

### Reserved Blocks
- **700s — Workshop & Logs**: Meeting notes, email dumps, brainstorming.  
- **800s — Reference & Support**: Manuals, tutorials, external resources.  
- **900s — Archive & Meta**: Deprecated files and old versions.

---

## The Folder Planning Process
1. **Every folder begins with its `README.md` file.** 2. The folder’s **`README.md`** defines:
   - Its scope and purpose
   - Hundreds-level categories
   - Tens-level custom sub-categories
   - File assignments
3. Files are numbered **before creation** to enforce planning.

---

## General Standards
- **Front Matter (YAML):** Each file may include metadata (`title`, `id`, `tags`, `status`, etc.).  
- **Style:** Concise, declarative, structured with headings/lists.  
- **Cross-Linking:** Use IDs or permanent slugs; avoid duplication.  
- **Archival:** Old files move to `900s` block or `/Archive`.

---

## Templates
Every folder may use the following starter templates:
- **README.md** — Defines the folder's scope, categories, and file numbering.
- **Log.md** — Ongoing notes or reflections.
- **Changelog.md** — Structural changes to the folder.

---

## Notes
- The **File Manifest** = A global inventory of the system's current state (changes frequently).
- The **Data Dictionary** = The universal rules of the game (changes slowly).
- A **Folder's README** = The local rules and inventory for that specific folder.