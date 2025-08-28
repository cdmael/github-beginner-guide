
# Git & GitHub Guide

A concise guide for beginners to intermediates to master Git and GitHub with practical examples.

# Table of Contents
* [Terminal Basics](#terminal-basics)
* [Git Setup](#git-setup)
* [Creating a Repository](#creating-a-repository)
* [Checking Status](#checking-status)
* [Staging & Committing](#staging--committing)
* [Viewing History](#viewing-history)
* [Comparing Versions](#comparing-versions)
* [Restoring & Reverting](#restoring--reverting)
* [Branching](#branching)
* [Merging](#merging)
* [Handling Merge Conflicts](#handling-merge-conflicts)
* [Cloning Repositories](#cloning-repositories)
* [Working with Remotes](#working-with-remotes)
* [Pulling from Remote](#pulling-from-remote)
* [Pushing to Remote](#pushing-to-remote)
* [Real-World Scenario](#real-world-scenario)
* [Daily Workflow](#daily-workflow)

# Terminal Basics
Navigate your terminal:

* **Show current directory**: `pwd`
* **List files and folders**: `ls`
* **Change directory**: `cd my-project`

# Git Setup
Verify Git installation:
```bash
git --version
```
Configure identity:
```bash
git config --global user.name "Your Name"
git config --global user.email "your.email@example.com"
```

# Creating a Repository
Initialize a new repository:
```bash
git init my-project
```
* Creates folder `my-project` with Git initialized.

Convert existing folder:
```bash
cd ~/projects/my-project
git init
```

# Checking Status
Check repository status:
```bash
git status
```
* Shows modified files, untracked files, and current branch.

# Staging & Committing
Stage changes:
* Single file: `git add <filename>`
* All files: `git add .`

Commit changes:
```bash
git commit -m "Add feature X"
```
* **Tip**: Use descriptive commit messages.

# Viewing History
View commit history:
```bash
git log
```
* Last 3 commits: `git log -3`
* Specific file: `git log <filename>`
* Date range: `git log --since="2024-04-02" --until="2024-04-11"`
* Specific commit: `git show <commit-hash>`

# Comparing Versions
Compare changes:
* Current vs. last commit: `git diff`
* Staged changes: `git diff --staged`
* Between commits: `git diff <hash1> <hash2>`
* Latest vs. previous: `git diff HEAD~1 HEAD`

# Restoring & Reverting
Revert a commit:
```bash
git revert HEAD
```
* Skip editor: `git revert --no-edit HEAD`
* Revert without committing: `git revert -n HEAD`

Restore a file:
```bash
git checkout HEAD~1 -- <filename>
```
Unstage changes:
* Single file: `git restore --staged <filename>`
* All files: `git restore --staged .`

# Branching
Manage branches:
* List branches: `git branch`
* Switch branches: `git switch <branch>`
* Create branch: `git branch <branch>`
* Create and switch: `git switch -c <branch>`
* Rename branch: `git branch -m <old> <new>`
* Delete branch: `git branch -d <branch>`

# Merging
Merge a branch:
```bash
git switch main
git merge feature-login
```

# Handling Merge Conflicts
Resolve conflicts:
* Open conflicted file: `nano README.md`
* Find conflict markers:
  ```markdown
  <<<<<<< HEAD
  Local changes
  =======
  Remote changes
  >>>>>>> origin/main
  ```
* Edit to resolve, then:
  ```bash
  git add README.md
  git commit -m "Resolve merge conflict"
  ```

# Cloning Repositories
Clone a repository:
```bash
git clone https://github.com/username/repo.git
```
Clone into a folder:
```bash
git clone https://github.com/username/repo.git my-folder
```

# Working with Remotes
Manage remotes:
* List remotes: `git remote`
* Detailed view: `git remote -v`
* Add remote: `git remote add origin https://github.com/username/repo.git`

# Pulling from Remote
Fetch updates:
```bash
git fetch origin
```
Pull and merge:
```bash
git pull origin main
```
* Skip merge editor: `git pull --no-edit origin main`

# Pushing to Remote
Push changes:
```bash
git push origin main
```
Push new branch:
```bash
git push origin feature-login
```

# Real-World Scenario
Resolving a conflict after linking a local repo:
* Initialize and commit:
  ```bash
  git init
  git add .
  git commit -m "Initial commit"
  ```
* Link to GitHub:
  ```bash
  git remote add origin https://github.com/username/my-project.git
  ```
* If push fails due to GitHub’s `README.md`:
  ```bash
  git pull origin main --allow-unrelated-histories
  ```
* Resolve conflicts in `README.md`, then:
  ```bash
  git add README.md
  git commit -m "Resolve README conflict"
  git push origin main
  ```

# Daily Workflow
* Check status: `git status`
* Stage changes: `git add .`
* Commit: `git commit -m "Add feature X"`
* Pull updates: `git pull origin main`
* Push: `git push origin main`
* **Tip**: Pull before pushing to avoid conflicts.
