Awesome—locking this down now. I’m giving you **two Markdown deliverables**:

1. `7200_document_control_policy.md` — the permanent policy for your repo (goes under **7000 Operations**).
2. **Implementation Guide (DO NOT COMMIT)** — a detailed, copy-paste setup you can take to a new chat to do all the work.

---

## 1) `7200_document_control_policy.md`

```md
---
id: OPS-7200
title: Document Control Policy (Repository Governance)
code: 7200
domain: operations
slug: document_control_policy
status: active           # draft | active | deprecated | superseded
owner: project_owner     # change to your name/role
created: 2025-08-31
revised: 2025-08-31
schema_version: 1
---

# Document Control Policy (Repository Governance)

## 1. Purpose
This policy establishes how we **create, name, organize, track, review, and archive** project documentation over multiple decades using **Git + Markdown** with a **numeric sorting code**. It ensures stability, clarity, and auditability without putting version numbers in filenames.

## 2. Scope
Applies to **all Markdown docs** in this repository. Exceptions (binary files, diagrams, spreadsheets) are covered by §12.

## 3. Core Principles
- **Single source of truth:** This repository and `meta/CATALOG.md`.
- **Stable ordering:** Four-digit codes sort documents without dates.
- **Descriptive slugs:** snake_case in filenames for human readability.
- **Git is the history:** No version numbers in filenames; use commits/tags.
- **Lightweight metadata:** YAML front-matter at top of each doc.
- **Insert without renumbering:** Reserve gaps to grow cleanly.
- **Supersede, don’t delete:** Preserve history and leave redirect stubs.

## 4. Top-Level Domains (baskets)
- `0000` Project Charter (exactly one document)
- `1000` Gameplay
- `2000` Simulation
- `3000` Narrative
- `4000` Audio/Video
- `5000` Graphics
- `6000` Engineering
- `7000` Operations

> Cross-cutting work primarily lives in `6000` (Engineering) and `7000` (Operations); `5000` (Graphics) may span multiple areas.

## 5. Numbering Rules
- **Format:** `XXXX` (four digits).
- **Domain root:** `X000` (e.g., `1000` Gameplay).
- **First doc in a domain:** `X100`, then `X200`, `X300`, … (reserve gaps).
- **Optional subsections:** add tens within a hundred block:
  - Example: children of `1200` can be `1210`, `1220`, `1230`, …
- **Project Charter:** only `0000_project_charter.md` lives under `0000`.

**Examples**
- `1100_master_concept_document.md` (first Gameplay doc)
- `2200_agent_behavior.md` (Simulation)
- `4200_cinematics_pipeline.md` (Audio/Video)

## 6. Filenames
```

<code>\_<slug>.md

```
- `code` = four digits (§5).
- `slug` = snake_case, short and specific.
- **No function prefixes** (e.g., no `PLAN_`, `SPEC_`).
- **No version numbers** in filenames (Git is the system of record).

## 7. Directory Layout
```

docs/
0000\_project\_charter.md

1000\_gameplay/
1100\_master\_concept\_document.md
1200\_core\_mechanics.md

2000\_simulation/
2100\_biosphere.md
2200\_agent\_behavior.md

3000\_narrative/
4000\_audio\_video/
5000\_graphics/
6000\_engineering/
7000\_operations/
7100\_release\_process.md
7200\_document\_control\_policy.md  <-- this file

````

> Use a subfolder per domain (`1000_gameplay/`, `2000_simulation/`, …).

## 8. Front-Matter (required)
Every doc starts with a YAML block:

```yaml
---
id: <DOMAIN>-<code>       # e.g., GPL-1100, SIM-2200, OPS-7200
title: <Human title>
code: <four-digit code>
domain: <domain name>     # gameplay|simulation|narrative|audio_video|graphics|engineering|operations|charter
slug: <snake_case_slug>
status: draft             # draft|active|deprecated|superseded
owner: <name or role>
created: YYYY-MM-DD
revised: YYYY-MM-DD
supersedes: []            # list of ids this doc replaces
superseded_by: null
tags: []
schema_version: 1
---
````

## 9. Catalog of Records

* `meta/CATALOG.md` lists **every** doc (id, code, title, status, path).
* Add a row when creating/renaming/superseding.
* A script may auto-generate/validate the catalog (§13).

## 10. Linking & References

* Reference documents by **ID** in prose, e.g., *See SIM-2200*.
* Use relative links to files, e.g., `[Agent Behavior](../2000_simulation/2200_agent_behavior.md)`.

## 11. Git Workflow

* **Branches:** `docs/<code>-<slug>` (e.g., `docs/2200-agent_behavior`)
* **Commits (Conventional Commits):**

  * `docs(sim): add SIM-2200 agent behavior baseline`
  * `docs(ops): update OPS-7200 policy: add catalog rules`
* **Tags:** create descriptive tags for major documentation milestones (e.g., `docs-v1.0`, `docs-2025.09`).
* **PRs/Reviews:** at least one review before merging to `main` (even if self-review with checklist).

## 12. Non-Markdown Artifacts

* Prefer Markdown. If binary/diagram assets are necessary:

  * Place under the **closest domain folder** with clear names.
  * Keep source + exported formats together (e.g., `diagram.drawio` + `diagram.svg`).
  * Do not assign codes to assets; reference them from the owning doc.

## 13. Quality Gates

* **Pre-commit** checks (scripted):

  * Filenames match `^\d{4}_[a-z0-9_]+\.md$`
  * Front-matter present and valid (`code`, `id`, `title`, `status`)
  * `code` matches path and filename
* Optional: run Markdown lint and link checkers.

## 14. Lifecycle States

* `draft` → working; `active` → approved baseline; `deprecated` → retained for history; `superseded` → replaced by another doc.
* When superseding:

  1. Update old doc’s front-matter (`status: superseded`, `superseded_by: <ID>`).
  2. Leave a one-line pointer at the top of the old doc to the new doc.
  3. Update `meta/CATALOG.md`.

## 15. Backups & Mirrors

* The Git repo is primary. Maintain:

  * Remote mirror (e.g., GitHub/GitLab).
  * Periodic offline archive (encrypted, quarterly).

## 16. Amendments

Changes to this policy follow the same process: propose (PR), review, and tag a policy release (e.g., `policy-ops-7200-v1`).

---

````

---

## 2) Implementation Guide (DO NOT COMMIT)

```md
# Documentation System — Implementation Guide (DO NOT COMMIT)

> Use this as a runbook to stand up the repo. **Do not add this file to the repo.**

## A. Prerequisites
- Git installed (`git --version`)
- Python 3.x (for a small catalog script)
- Optional: Node.js (for markdownlint) and `pre-commit` (Python) if you want easy linting

## B. Initialize the Repository
```bash
mkdir my_project_docs && cd my_project_docs
git init -b main
git config user.name "Your Name"
git config user.email "you@example.com"
````

## C. Base Structure

```bash
mkdir -p docs/{1000_gameplay,2000_simulation,3000_narrative,4000_audio_video,5000_graphics,6000_engineering,7000_operations} meta scripts
```

Create `.gitignore`:

```bash
cat > .gitignore << 'EOF'
# OS
.DS_Store
Thumbs.db

# Editors
.vscode/
.idea/

# Python
__pycache__/
*.pyc

# Generated
meta/CATALOG.generated.md
EOF
```

Create `.gitattributes` (better diffs for Markdown):

```bash
cat > .gitattributes << 'EOF'
*.md text diff=markdown
EOF
```

(Optionally enable a markdown diff driver globally:

````bash
git config --global diff.markdown.xfuncname "^(#{1,6} .*|\\s*\\* .*)"
```)

## D. Seed the First Files
**Project Charter**
```bash
cat > docs/0000_project_charter.md << 'EOF'
---
id: CHA-0000
title: Project Charter
code: 0000
domain: charter
slug: project_charter
status: active
owner: project_owner
created: 2025-08-31
revised: 2025-08-31
schema_version: 1
---
# Project Charter

(Describe purpose, scope, success criteria, stakeholders, constraints.)
EOF
````

**Document Control Policy (this is 7200)**

```bash
# Paste the full contents of 7200_document_control_policy.md here:
mkdir -p docs/7000_operations
cat > docs/7000_operations/7200_document_control_policy.md << 'EOF'
(PASTE POLICY CONTENT HERE)
EOF
```

**Catalog scaffold**

```bash
cat > meta/CATALOG.md << 'EOF'
# Document Catalog

| ID   | Code | Title | Status | Path |
|------|------|-------|--------|------|
| CHA-0000 | 0000 | Project Charter | active | docs/0000_project_charter.md |
| OPS-7200 | 7200 | Document Control Policy (Repository Governance) | active | docs/7000_operations/7200_document_control_policy.md |
EOF
```

## E. Pre-Commit Hook (lightweight checks)

```bash
mkdir -p .git/hooks
cat > .git/hooks/pre-commit << 'EOF'
#!/usr/bin/env bash
set -euo pipefail

fail=0

# Check filenames
changed=$(git diff --cached --name-only --diff-filter=ACMR | grep -E '\.md$' || true)
for f in $changed; do
  base="$(basename "$f")"
  if [[ "$base" =~ ^[0-9]{4}_[a-z0-9_]+\.md$ || "$base" == "CATALOG.md" || "$base" == "README.md" || "$base" == "CHANGELOG.md" ]]; then
    :
  else
    echo "✖ Filename does not match pattern: $f"
    fail=1
  fi
done

# Validate front-matter presence and required fields (code, id, title, status)
for f in $changed; do
  [[ "$f" =~ \.md$ ]] || continue
  if ! awk 'NR==1,/^---$/{next} /^---$/{exit} {print}' "$f" | grep -q . ; then
    # first line should be ---
    if [[ "$(head -1 "$f")" != "---" ]]; then
      echo "✖ Missing YAML front-matter: $f"; fail=1; continue
    fi
  fi

  fm=$(awk 'NR==1{if($0!="---"){exit 1}} NR>1{print} /^---$/{exit}' "$f" || true)
  for key in code id title status; do
    echo "$fm" | grep -q "^$key:" || { echo "✖ Missing '$key' in front-matter: $f"; fail=1; }
  done
done

if [[ $fail -ne 0 ]]; then
  echo "Pre-commit checks failed."; exit 1
fi
echo "✓ Pre-commit checks passed."
EOF
chmod +x .git/hooks/pre-commit
```

## F. Optional: Markdown Lint (recommended)

```bash
npm init -y
npm install --save-dev markdownlint-cli
cat > .markdownlint.json << 'EOF'
{
  "default": true,
  "MD013": false,   // line length off
  "MD033": false    // allow inline HTML if needed
}
EOF
```

Add to pre-commit (append before the final “passed” echo):

```bash
npx markdownlint **/*.md
```

## G. Auto-Generate Catalog (optional helper)

Create a tiny Python script to scan docs and update a generated table (you’ll still curate `meta/CATALOG.md`):

```bash
cat > scripts/gen_catalog.py << 'EOF'
#!/usr/bin/env python3
import os, re, yaml, pathlib

ROOT = pathlib.Path(__file__).resolve().parents[1]
DOCS = ROOT / "docs"
OUT  = ROOT / "meta" / "CATALOG.generated.md"

def read_front_matter(path):
    txt = path.read_text(encoding="utf-8")
    if not txt.startswith("---"):
        return None
    parts = txt.split("\n---", 2)
    if len(parts) < 2:
        return None
    fm = parts[0].lstrip("-\n")  # strip leading ---
    return yaml.safe_load(fm)

rows = []
for p in DOCS.rglob("*.md"):
    fm = read_front_matter(p)
    if not fm: 
        continue
    rows.append({
        "id": fm.get("id",""),
        "code": fm.get("code",""),
        "title": fm.get("title",""),
        "status": fm.get("status",""),
        "path": str(p).replace(str(ROOT)+"/","")
    })

rows.sort(key=lambda r: (str(r["code"]).zfill(4), r["title"]))

with OUT.open("w", encoding="utf-8") as f:
    f.write("# Document Catalog (Generated)\n\n")
    f.write("| ID | Code | Title | Status | Path |\n")
    f.write("|----|------|-------|--------|------|\n")
    for r in rows:
        f.write(f"| {r['id']} | {r['code']} | {r['title']} | {r['status']} | {r['path']} |\n")
print(f"Wrote {OUT}")
EOF
chmod +x scripts/gen_catalog.py
```

Run it:

```bash
python3 scripts/gen_catalog.py
```

## H. Commit Baseline

```bash
git add .
git commit -m "docs(ops): bootstrap charter, policy, catalog, hooks"
git tag docs-v0.1
```

## I. Conventional Commits (quality of history)

Set a simple commit template:

```bash
cat > .gitmessage.txt << 'EOF'
<type>(<scope>): <summary>

Refs: <ids or issue links>
Body: Explain the what/why briefly.

# type: docs|feat|fix|refactor|chore
# scope: ops|sim|gameplay|narrative|audio_video|graphics|engineering
EOF

git config commit.template "$(pwd)/.gitmessage.txt"
```

## J. GitHub/GitLab Hardening (optional but ideal)

* Create remote repo and push:

  ```bash
  git remote add origin <your-remote-url>
  git push -u origin main --tags
  ```
* Enable **branch protection** on `main`: require PRs and 1 approval.
* Require **status checks** (pre-commit CI) before merge.

## K. Working Cycle (checklist)

1. Choose a domain (e.g., `2000_simulation`).
2. Pick next free code (`2100`, `2200`, reserve gaps).
3. Create file `docs/2000_simulation/2200_<slug>.md` with front-matter.
4. Update `meta/CATALOG.md`.
5. `git checkout -b docs/2200-<slug>`
6. Commit with Conventional Commit format referencing the ID.
7. Open PR, review (self-review if solo), merge to `main`.
8. Tag a docs milestone periodically (e.g., `docs-2025.09`).

## L. Superseding a Doc

* In old doc: set `status: superseded`, fill `superseded_by`.
* In new doc: set `supersedes: [<old-id>]`.
* Add a top note in old doc: “Superseded by <ID>”.
* Update catalog.

## M. Exceptions & Edge Cases

* If a doc truly belongs in two domains, place it where **primary ownership** is clearest; cross-link from the other domain’s docs.
* If you ever must move a doc across domains, **keep the code** (identity) and update links/citations. If changing the code is unavoidable, mark the old file as superseded and create a new file with a new code.

---

```

If you want, I can also generate your **initial folder tree and empty files (with front-matter already filled)** to paste directly into your repo.
```
