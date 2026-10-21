# My First Project

A small Python project I built to learn **Git** and **GitHub** step by step — from setting up Git to working with branches, Pull Requests, and Issues like a real development team.

**Author:** Ali Adel ([@JoAli21](https://github.com/JoAli21))

---

## 📁 Project Files

| File | Description |
|---|---|
| `main.py` | Prints a greeting and uses an `add` function |
| `calculator.py` | Calculator functions: `multiply`, `subtract`, `divide` (handles division by zero) |

## ▶️ How to Run

```bash
python main.py
python calculator.py
```

---

## 🧭 What I Learned — Step by Step

### 1. Setting up Git (one time only)

```bash
git --version
git config --global user.name "Ali Adel"
git config --global user.email "my-email@example.com"
```

Tells Git who I am, so every commit is saved under my name.

### 2. Creating the repository

- Created a new repository on GitHub: `my-first-project`
- Created the project folder and opened it in **VS Code**
- Wrote `main.py` and ran it from the VS Code terminal

### 3. First commit and first push

```bash
git init                     # start tracking the folder
git status                   # see what changed
git add .                    # stage all changed files
git commit -m "First commit" # save a snapshot locally
git branch -M main           # rename branch to main
git remote add origin https://github.com/JoAli21/my-first-project.git
git remote -v                # confirm the connection
git push -u origin main      # upload to GitHub
```

### 4. The daily cycle (edit → save → upload)

```bash
git status
git add .
git commit -m "Describe what I changed"
git push
```

After the first `push -u`, only `git push` is needed.

### 5. Working with branches and Pull Requests

```bash
git checkout -b feature-calculator     # create a new branch and switch to it
# write calculator.py
git add .
git commit -m "Add calculator functions"
git push -u origin feature-calculator
```

Then on GitHub:
- Opened a **Pull Request** (`base: main ← compare: feature-calculator`)
- Reviewed **Files changed** (green `+` = added lines, red `-` = removed lines)
- **Merged** the Pull Request and deleted the branch

Back in VS Code:

```bash
git checkout main
git pull                              # download the merge to my computer
git branch -d feature-calculator      # delete the finished branch
git branch                            # list branches (* = current branch)
```

### 6. Team workflow simulation: Manager 👔 and Employee 👷

| Role | Step |
|---|---|
| 👔 Manager | Created **Issue #2**: "Add divide function to calculator" |
| 👷 Employee | `git checkout main` → `git pull` → `git checkout -b issue-2-divide` |
| 👷 Employee | Wrote the `divide` function → tested it → `git add calculator.py` → `git commit` → `git push -u origin issue-2-divide` |
| 👷 Employee | Opened **Pull Request #3** with `Closes #2` in the description |
| 👔 Manager | Reviewed **Files changed**, left a comment on a line, submitted the review, then **merged** |
| 🪄 GitHub | Closed **Issue #2** automatically because of `Closes #2` |
| 👷 Employee | `git checkout main` → `git pull` → `git branch -d issue-2-divide` |

**Branch naming convention:** `issue-<number>-<short-description>`, e.g. `issue-3-login`. No spaces, use `-`.

**Commit only specific files:** `git add calculator.py` instead of `git add .` — so each commit contains one task only.

---

## 🛠️ Problems I Faced and How I Fixed Them

| Error | Cause | Fix |
|---|---|---|
| `git: 'add.' is not a git command` | Missing space | `git add .` |
| `Permission ... denied to <another account>` (403) | Windows had another GitHub account saved | `cmdkey /delete:git:https://github.com` then push again and sign in with the right account |
| `src refspec ... does not match any` | Typo in branch name | Check names with `git branch` |
| `unknown switch 'U'` | Git is case-sensitive | Use `-u` (lowercase) |
| `cannot delete branch ... used by worktree` | Tried to delete the branch I was on | `git checkout main` first, then delete |
| File disappeared after switching to `main` | Local `main` was behind GitHub | `git pull` |

---

## 🧠 Golden Rules

1. Before starting any new work: `git checkout main` then `git pull`
2. One task = one branch = one Pull Request
3. Always check the current branch name (bottom-left in VS Code)
4. Write clear commit messages in English that describe *what* changed
5. Test the code before committing
