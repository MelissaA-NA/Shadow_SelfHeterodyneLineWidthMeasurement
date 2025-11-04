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

### Branches

* **main** → Base branch (tracks `origin/main`)
* **testing01** → Your feature/development branch (tracks `origin/testing01`)

List branches:

```bash
git branch          # local branches
git branch -a       # all (including remote)
```

Switch branches:

```bash
git switch testing01     # move to your work branch
git switch main          # back to main
```

Create a new branch from main:

```bash
git switch main
git pull origin main
git switch -c new-branch-name
```

---

## 2. Daily Workflow

```bash
# Check branch and repo
git branch
git remote -v

# Stage and commit changes
git add .
git commit -m "descriptive message"
git push
```

First push for a new branch:

```bash
git push -u origin new-branch-name
```

---

## 3. Keeping Your Branch Updated

Sync with upstream changes:

```bash
git fetch origin
git merge origin/main     # or: git rebase origin/main
```

Pull the latest Nomad changes into your local main:

```bash
git switch main
git fetch origin
git pull origin main
```

---

## 4. Debugging & Info Commands

```bash
git status                  # check modifications
git diff                    # view unstaged changes
git diff --staged           # view staged changes
git log --oneline -10 --graph --decorate  # short log
git fetch --all             # fetch all remotes
git rev-parse --show-toplevel  # confirm repo root
```

---

## 5. Handling Common Issues

### File not showing changes

Make sure file is saved (Ctrl+S) and not ignored by `.gitignore`.

Force-track notebook:

```bash
git rm --cached SHD_script.ipynb
git add -f SHD_script.ipynb
git commit -m "Force track notebook"
git push
```

To ensure `.ipynb` always tracked, add this to `.gitignore`:

```
!SHD_script.ipynb
```

### Undo / Reset mistakes

```bash
git restore <file>              # discard local edits
git restore --staged <file>     # unstage
git commit --amend              # change last commit message
git reset --soft HEAD~1         # undo last commit, keep changes staged
```

### Line Ending Warning

If you see:

```
LF will be replaced by CRLF
```

It’s safe to ignore (Windows uses CRLF). To standardize:

```bash
git config core.autocrlf true
```

---

## 6. Quick Reference Commands

```bash
git status
git add .
git commit -m "message"
git push

git fetch origin
git merge origin/main
```

---

## 7. VS Code Tips

* Click bottom-left branch name to switch branches.
* Use the Source Control tab to stage & commit.
* Enable **Auto Save**: File → Auto Save → After Delay.

---

### ✅ Summary:

* Work on **testing01** (personal dev branch).
* Push to **origin/testing01**.
* Keep **main** updated from **origin/main**.
* Fetch from **upstream** to get Nomad’s latest changes.
* Always `git status` before commit.

---

**End of Notes**
