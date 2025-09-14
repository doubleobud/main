# Git Daily Workflow — _Root (Life OS)

> **Copy‑paste Quick Block (PowerShell):** edit the message on the `$MSG` line, then paste everything at once.

```powershell
# Start here each work session (LOCAL-ONLY)
cd C:\_Root
git status

# Save a snapshot (edit your message below, keep the quotes)
$MSG="2025-09-12: describe what you changed"
git add .
git commit -m $MSG

# Verify
git log --oneline -n 5
git status

# OPTIONAL: If a remote is configured later (origin/main), you can sync:
# git pull --ff-only origin main
# git push origin main
```

---

## Why this exists
You turned `C:\_Root` into a Git repository. Git tracks your changes as **commits** (snapshots) so you can see history, undo mistakes, and—later—sync to GitHub and publish a site. The Archive folder (`9-Archive/`) is ignored so it doesn’t clutter history.

---

## The Daily Flow (simple, reliable)

### 1) Open your project
- Open VS Code.
- Open the integrated terminal (**Ctrl+`**) — ensure the prompt says `PS C:\_Root>`.
- If not, run: `cd C:\_Root`.

### 2) Before you start working
```powershell
git status
```
- **Clean** → you’re good to go.
- **Modified/Untracked files** → that’s fine; just know what changed.

### 3) Work normally
- Edit files as usual in VS Code.

### 4) Save a snapshot (commit) when you finish a chunk
```powershell
git add .           # stage everything that changed (respects .gitignore)
git commit -m "YYYY-MM-DD: short, clear message of what you changed"
```
Tips for good messages:
- Start with the date (helps chronological scanning).
- Keep it short but specific (e.g., “2025‑09‑12: add .gitignore, write daily guide”).

### 5) Verify your history
```powershell
git log --oneline -n 5   # last 5 commits
git status               # should usually be 'working tree clean'
```

> **That’s it.** Repeat steps 3–5 through the day. Many small commits are better than one giant one.

---

## Visual view (no commands)
Use VS Code’s **Source Control** panel (the branch icon on the left):
- It shows changed files.
- Click a file to see the line-by-line diff.
- Type a message and click the ✓ checkmark to commit.

---

## Handy one-liners (only if you need them)

```powershell
git diff                 # see the actual line changes
git diff --name-only     # just the filenames that changed
git restore --staged <file>   # unstage (if you added something by mistake)
git restore <file>            # discard local changes to a file
git log --oneline --graph --decorate -n 15   # prettier recent history
git status --ignored -s     # confirm that 9-Archive/ is ignored (shows '!! 9-Archive/')
```

---

## Gotchas you might run into (and fixes)

- **Accidentally tracked Archive**  
  ```powershell
  git rm -r --cached 9-Archive
  git commit -m "Stop tracking Archive; keep it ignored"
  ```

- **“index.lock exists” error after a crash/close**  
  ```powershell
  del .git\index.lock
  ```

- **Annoying line-ending warnings on Windows (“LF will be replaced by CRLF”)**  
  ```powershell
  git config --global core.autocrlf true
  ```

---

## What’s next (when you’re ready)
- Create a GitHub repo and add a remote so you can `git push` your history online.
- Add a minimal `index.html` and enable GitHub Pages to publish your site.
```

