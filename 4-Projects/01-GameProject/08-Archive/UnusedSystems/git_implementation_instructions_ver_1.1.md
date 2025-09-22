Of course. Here are the complete, consolidated instructions, incorporating the original guide with the recommended improvements for robustness and automation. You can copy and paste this entire block into your new Markdown file.

````md
# Documentation System — Implementation Guide (DO NOT COMMIT)

> Use this as a runbook to stand up the repo. **Do not add this file to the repo.**

## A. Prerequisites
- **Git** (`git --version`)
- **Python 3.x** and Pip (`python3 --version`, `pip --version`)
- **Node.js** and npm (`node --version`, `npm --version`)
- **The `pre-commit` package** (install via Pip: `pip install pre-commit`)

## B. Initialize the Repository
```bash
mkdir my_project_docs && cd my_project_docs
git init -b main
git config user.name "Your Name"
git config user.email "you@example.com"
````

## C. Create the Base Structure

This sets up the directories and essential configuration files for the repository.

1.  **Create Directories:**

    ```bash
    mkdir -p docs/{1000_gameplay,2000_simulation,3000_narrative,4000_audio_video,5000_graphics,6000_engineering,7000_operations} meta scripts
    ```

2.  **Create `.gitignore`:** This file tells Git what to ignore.

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
    venv/
    *.env

    # Node
    node_modules/
    EOF
    ```

3.  **Create `.gitattributes`:** This helps Git create better diffs for Markdown files.

    ```bash
    cat > .gitattributes << 'EOF'
    *.md text diff=markdown
    EOF
    ```

    *(Optional: To enable a markdown diff driver globally for all your projects, run `git config --global diff.markdown.xfuncname "^(#{1,6} .*|\\s*\\* .*)")`*

## D. Seed Initial Files

Create the foundational documents and configuration files.

1.  **Project Charter (`0000_project_charter.md`):**

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

    (Describe project purpose, scope, success criteria, stakeholders, and constraints.)
    EOF
    ```

2.  **Document Control Policy (`7200_document_control_policy.md`):**

    ```bash
    cat > docs/7000_operations/7200_document_control_policy.md << 'EOF'
    ---
    id: OPS-7200
    title: Document Control Policy (Repository Governance)
    code: 7200
    domain: operations
    slug: document_control_policy
    status: active
    owner: project_lead
    created: 2025-08-31
    revised: 2025-08-31
    schema_version: 1
    ---
    # Document Control Policy

    (Describe the rules for creating, reviewing, approving, and superseding documents.)
    EOF
    ```

3.  **Document Catalog (`CATALOG.md`):** This file will be automatically updated by a script.

    ```bash
    cat > meta/CATALOG.md << 'EOF'
    # Document Catalog

    | ID   | Code | Title | Status | Path |
    |------|------|-------|--------|------|
    | CHA-0000 | 0000 | Project Charter | active | docs/0000_project_charter.md |
    | OPS-7200 | 7200 | Document Control Policy (Repository Governance) | active | docs/7000_operations/7200_document_control_policy.md |
    EOF
    ```

4.  **Root `README.md`:** This is the entry point for repository visitors.

    ```bash
    cat > README.md << 'EOF'
    # My Project Documentation

    Welcome to the central documentation repository for My Project.

    ## 📖 How to Use This Repository

    All technical and procedural documents are located in the `docs/` directory.

    - **[Browse the Full Document Catalog](./meta/CATALOG.md)** to find a specific document by its ID, title, or domain.
    - **Start with the [Project Charter](./docs/0000_project_charter.md)** to understand the project's goals and scope.

    ## ✍️ Contribution Guidelines

    Please follow the established workflow for creating or updating documents. See the [Document Control Policy](./docs/7000_operations/7200_document_control_policy.md) for more details.
    EOF
    ```

## E. Setup Automated Pre-Commit Checks

Instead of manual hook scripts, we use the `pre-commit` framework to manage version-controlled, automated checks that run before each commit. This ensures consistency and quality for all contributors.

1.  **Create Python Dependencies File (`requirements.txt`):**

    ```bash
    cat > requirements.txt << 'EOF'
    PyYAML==6.0.1
    EOF
    ```

2.  **Create Markdown Linter Config (`.markdownlint.json`):**

    ```bash
    cat > .markdownlint.json << 'EOF'
    {
      "default": true,
      "MD013": false,
      "MD033": false
    }
    EOF
    ```

3.  **Create `pre-commit` Configuration (`.pre-commit-config.yaml`):** This file orchestrates all the checks.

    ```bash
    cat > .pre-commit-config.yaml << 'EOF'
    repos:
    -   repo: [https://github.com/pre-commit/pre-commit-hooks](https://github.com/pre-commit/pre-commit-hooks)
        rev: v4.6.0
        hooks:
        -   id: check-yaml
        -   id: end-of-file-fixer
        -   id: trailing-whitespace
    -   repo: [https://github.com/igorshubovych/markdownlint-cli](https://github.com/igorshubovych/markdownlint-cli)
        rev: v0.41.0
        hooks:
        -   id: markdownlint
            args: [--config, .markdownlint.json]
    -   repo: local
        hooks:
        -   id: front-matter-check
            name: Check for required front-matter keys
            entry: python3 scripts/check_frontmatter.py
            language: python
            types: [markdown]
            additional_dependencies: [pyyaml]
        -   id: filename-check
            name: Check markdown filename conventions
            # This regex enforces the `NNNN_slug_name.md` pattern inside the domain folders.
            entry: ^docs/[0-9]{4}_[a-z0-9_]+/([0-9]{4}_[a-z0-9_]+\.md)$
            language: pygrep
            types: [markdown]
    EOF
    ```

4.  **Create Front-Matter Validation Script (`scripts/check_frontmatter.py`):** This is a robust Python script to validate the YAML front-matter.

    ```bash
    cat > scripts/check_frontmatter.py << 'EOF'
    #!/usr/bin/env python3
    import sys, yaml, pathlib

    def read_front_matter(path):
        try:
            content = pathlib.Path(path).read_text(encoding="utf-8")
            if not content.startswith("---"):
                return None, "File does not start with YAML front-matter."
            parts = content.split("---", 2)
            if len(parts) < 3:
                return None, "Invalid front-matter structure (missing closing '---')."
            return yaml.safe_load(parts[1]), None
        except yaml.YAMLError as e:
            return None, f"YAML parsing error: {e}"
        except Exception as e:
            return None, f"Could not read file: {e}"

    errors = 0
    # The first argument is the script name, so we slice from the second.
    for filename in sys.argv[1:]:
        fm, err = read_front_matter(filename)
        if err:
            print(f"✖ Error in {filename}: {err}")
            errors += 1
            continue
        
        required_keys = {"id", "code", "title", "status"}
        missing_keys = required_keys - set(fm.keys())
        if missing_keys:
            print(f"✖ Missing keys in {filename}: {', '.join(sorted(missing_keys))}")
            errors += 1

    if errors > 0:
        sys.exit(1)
    EOF
    chmod +x scripts/check_frontmatter.py
    ```

5.  **Install Dependencies and Hooks:**

    ```bash
    pip install -r requirements.txt
    npm init -y
    npm install --save-dev markdownlint-cli
    pre-commit install
    ```

## F. Auto-Generate the Document Catalog

This script scans the `docs` directory and automatically updates `meta/CATALOG.md`.

1.  **Create Catalog Generator Script (`scripts/gen_catalog.py`):**

    ```bash
    cat > scripts/gen_catalog.py << 'EOF'
    #!/usr/bin/env python3
    import os, re, yaml, pathlib

    ROOT = pathlib.Path(__file__).resolve().parents[1]
    DOCS = ROOT / "docs"
    OUT  = ROOT / "meta" / "CATALOG.md" # This now points to the main catalog file

    def read_front_matter(path):
        txt = path.read_text(encoding="utf-8")
        if not txt.startswith("---"): return None
        parts = txt.split("\n---", 2)
        if len(parts) < 2: return None
        fm_text = parts[0].lstrip("-\n")
        try:
            return yaml.safe_load(fm_text)
        except yaml.YAMLError:
            return None

    rows = []
    for p in sorted(DOCS.rglob("*.md")):
        fm = read_front_matter(p)
        if not fm: 
            continue
        rows.append({
            "id": fm.get("id",""),
            "code": fm.get("code",""),
            "title": fm.get("title",""),
            "status": fm.get("status",""),
            "path": str(p.relative_to(ROOT)).replace("\\", "/") # Use relative paths
        })

    rows.sort(key=lambda r: (str(r["code"]).zfill(4), r["title"]))

    with OUT.open("w", encoding="utf-8") as f:
        f.write("# Document Catalog\n\n")
        f.write("> This catalog is auto-generated. Do not edit it manually. Run `python3 scripts/gen_catalog.py` to update.\n\n")
        f.write("| ID | Code | Title | Status | Path |\n")
        f.write("|----|------|-------|--------|------|\n")
        for r in rows:
            f.write(f"| {r['id']} | {r['code']} | {r['title']} | {r['status']} | [{r['path']}](./../{r['path']}) |\n")
    print(f"✅ Catalog updated successfully at {OUT}")
    EOF
    chmod +x scripts/gen_catalog.py
    ```

2.  **Run the script to generate the initial catalog:**

    ```bash
    python3 scripts/gen_catalog.py
    ```

## G. Set Up Commit Message Template

Using a template encourages consistent and high-quality commit messages.

1.  **Create the template file `.gitmessage.txt`:**

    ```bash
    cat > .gitmessage.txt << 'EOF'
    <type>(<scope>): <summary>

    Refs: <ids or issue links>
    Body: Explain the what/why briefly.

    # type: docs|feat|fix|refactor|chore
    # scope: ops|sim|gameplay|narrative|audio_video|graphics|engineering
    EOF
    ```

2.  **Configure Git to use the template:**

    ```bash
    git config commit.template "$(pwd)/.gitmessage.txt"
    ```

## H. Commit the Baseline

Make the first commit with all the foundational files.

```bash
git add .
git commit -m "docs(ops): bootstrap charter, policy, catalog, and tooling"
git tag docs-v0.1
```

## I. Harden the Remote Repository

After pushing to your remote (GitHub, GitLab, etc.), configure branch protection rules to safeguard the `main` branch.

1.  **Create remote repo and push:**
    ```bash
    # Get the URL from your provider (e.g., GitHub)
    git remote add origin <your-remote-url>
    git push -u origin main --tags
    ```
2.  **Enable branch protection on `main`:**
      - Require pull requests before merging.
      - Require at least one approval.
      - Require status checks (your CI/CD pipeline) to pass before merging.

## J. The Standard Working Cycle

Follow these steps to add or update a document.

1.  Pull the latest changes: `git checkout main && git pull origin main`.
2.  Create a new branch: `git checkout -b docs/NNNN-brief-description`.
3.  Choose a domain (e.g., `2000_simulation`).
4.  Pick the next available code (e.g., `2100`).
5.  Create the file `docs/2000_simulation/2100_new_feature_design.md` with complete front-matter.
6.  Write the document content.
7.  **Run the catalog script** to add your new document to `meta/CATALOG.md`:
    ```bash
    python3 scripts/gen_catalog.py
    ```
8.  Stage your changes: `git add .`
9.  Commit your work. The pre-commit hooks will run automatically. If they fail, fix the issues and commit again.
    ```bash
    git commit # Your editor will open with the template
    ```
10. Push your branch and open a Pull Request for review.
11. Once approved and merged, delete your branch.

## K. Superseding a Document

When a document becomes obsolete and is replaced by a new one:

1.  In the **old document's** front-matter, set `status: superseded` and add a new key `superseded_by: <new-doc-id>`.
2.  Add a note to the top of the old document: `> **This document is superseded.** Please see the new document: [New Document Title](path/to/new/doc.md) (ID: <new-doc-id>).`
3.  In the **new document's** front-matter, add a key `supersedes: [<old-doc-id>]`.
4.  Run the catalog generator script to update the status.

## L. Exceptions and Edge Cases

  - If a doc belongs in two domains, place it where **primary ownership** is clearest and cross-link from the other.
  - If you must move a doc across domains, **keep its unique code** and update all links. If changing the code is unavoidable, you must supersede the old document (as in Section K) and create a new one with a new code. The code is the document's permanent identity.

<!-- end list -->

```
```