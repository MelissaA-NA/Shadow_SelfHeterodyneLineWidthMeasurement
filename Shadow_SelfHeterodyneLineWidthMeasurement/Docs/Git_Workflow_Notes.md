# Git Notes for SelfHeterodyne Project

Author: **Melissa Azizul**

This document summarises the essential Git workflow, structure, and debug commands used for the *SelfHeterodyne Linewidth Measurement* repository, including integration with your personal fork and the Nomad upstream repository.

---

## 1. Repository Structure

### Remotes

* **origin** → Your personal GitHub repo (you push here)
* **upstream** → Nomad-Atomics repo (you fetch/pull from here)

Check remotes:

```bash
git remote -v
```

---

## 2. Branches

* **main** → Base branch (tracks `origin/main`)
* **testing01** → Your feature/development branch (tracks `origin/testing01`)

List branches:

```bash
git branch            # local branches
git branch -a          # all (including remote)
```

Switch branches:

```bash
git checkout testing01
```

Create a new branch:

```bash
git checkout -b new-feature
```

---

## 3. Typical Workflow

### 🧠 Local Work

1. Make edits in VS Code
2. Check changes:

   ```bash
   git status
   ```
3. Stage and commit:

   ```bash
   git add <file>
   git commit -m "description of change"
   ```
4. Push to your personal fork:

   ```bash
   git push
   ```

---

## 4. Keeping Upstream in Sync

To fetch Nomad’s latest code without pushing to it:

```bash
git fetch upstream
```

To merge or rebase updates:

```bash
git merge upstream/main
```

---

## 5. Debug & Verification Commands

Check repository root:

```bash
git rev-parse --show-toplevel
```

Check modified files:

```bash
git status
```

Force add ignored files (e.g., notebooks):

```bash
git add -f SHD_script.ipynb
```

View recent commits:

```bash
git log --oneline -5 --decorate
```

---

## 6. Adding an External Folder (like `Docs/`)

When creating new directories (e.g., `Docs/` for notes):

1. Navigate to the correct folder level:

   ```bash
   cd ..   # move up one level if you’re inside a subfolder like SelfHeterodyne
   ```

2. Verify the folder exists:

   ```bash
   ls Docs
   ```

3. Stage, commit, and push:

   ```bash
   git add Docs/Git_Workflow_Notes.md
   git commit -m "Add Git workflow notes for SelfHeterodyne project"
   git push
   ```

💡 *Tip:* Always ensure you’re in the **repo root directory** before adding paths that start with folder names.

---

## 7. VS Code Tips

* Click bottom-left branch name to switch branches.
* Use the Source Control tab to stage & commit.
* Enable **Auto Save**: File → Auto Save → After Delay.

---

### ✅ Summary

* Work on **testing01** (personal dev branch).
* Push to **origin/testing01**.
* Keep **main** updated from **origin/main**.
* Fetch from **upstream** for Nomad’s latest changes.
* Always run `git status` before committing.

---

**End of Notes**

