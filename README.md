# Git Commands Cheat Sheet

A practical reference for commonly used Git commands.

---

## Getting & Creating Projects

| Command | Description |
|---|---|
| `git init` | Initialize a local Git repository |
| `git clone ssh://git@github.com/[username]/[repository-name].git` | Create a local copy of a remote repository |

---

## Basic Snapshotting

| Command | Description |
|---|---|
| `git status` | Check the current repository status |
| `git add [file-name.txt]` | Add a specific file to the staging area |
| `git add -A` | Add all new, modified, and deleted files to the staging area |
| `git add *` | Add listed files in the current directory to the staging area |
| `git commit -m "[commit message]"` | Commit staged changes with a message |
| `git rm -r [file-name.txt]` | Remove a file or folder from Git |

> **Recommended:** In most cases, use `git add .` or `git add -A` instead of `git add *`, because shell wildcard behavior can differ.

---

## Branching & Merging

| Command | Description |
|---|---|
| `git branch` | List local branches. The `*` denotes the current branch |
| `git branch -a` | List all branches, including local and remote-tracking branches |
| `git branch [branch-name]` | Create a new local branch |
| `git branch -d [branch-name]` | Delete a local branch safely |
| `git branch -D [branch-name]` | Force-delete a local branch |
| `git push origin --delete [branch-name]` | Delete a remote branch |
| `git checkout -b [branch-name]` | Create a new branch and switch to it |
| `git checkout -b [branch-name] origin/[branch-name]` | Create a local branch from a remote branch and switch to it |
| `git branch -m [old-branch-name] [new-branch-name]` | Rename a local branch |
| `git checkout [branch-name]` | Switch to another branch |
| `git checkout -` | Switch back to the previously checked-out branch |
| `git checkout -- [file-name.txt]` | Discard unstaged changes to a file |
| `git merge [branch-name]` | Merge the specified branch into the currently active branch |
| `git stash` | Temporarily save uncommitted changes |
| `git stash clear` | Delete all stashed entries |

### Modern `git switch` Alternatives

| Command | Description |
|---|---|
| `git switch [branch-name]` | Switch to an existing branch |
| `git switch -c [branch-name]` | Create a new branch and switch to it |
| `git switch -` | Switch back to the previous branch |

---

## Sharing & Updating Projects

| Command | Description |
|---|---|
| `git push origin [branch-name]` | Push a branch to the remote repository |
| `git push -u origin [branch-name]` | Push a branch and set its upstream tracking branch |
| `git push` | Push changes to the configured upstream branch |
| `git push origin --delete [branch-name]` | Delete a remote branch |
| `git pull` | Fetch and integrate changes from the tracked remote branch |
| `git pull origin [branch-name]` | Pull changes from a specific remote branch |
| `git fetch` | Download remote updates without merging them |
| `git fetch --prune` | Fetch updates and remove stale remote-tracking branch references |
| `git remote -v` | Show configured remote repository URLs |
| `git remote add origin ssh://git@github.com/[username]/[repository-name].git` | Add a remote repository named `origin` |
| `git remote set-url origin ssh://git@github.com/[username]/[repository-name].git` | Change the URL of the `origin` remote |

---

## Inspection & Comparison

| Command | Description |
|---|---|
| `git log` | View commit history |
| `git log --summary` | View commit history with additional summary information |
| `git log --oneline` | View commit history in a compact one-line format |
| `git log --oneline --graph --decorate --all` | View a visual graph of branches and commits |
| `git diff` | Show unstaged changes |
| `git diff --staged` | Show staged changes |
| `git diff [source-branch] [target-branch]` | Compare two branches before merging |
| `git branch -vv` | Show local branches with remote tracking information |

---

# Adding a New Repository — Udai Method

Use this workflow when you already have a local project and want to push it to a new GitHub repository.

## Step 1 — Initialize Git

```bash
git init
```

Initializes a local Git repository.

> One-time command for a new project.

## Step 2 — Add Project Files

```bash
git add .
```

You can also use:

```bash
git add -A
```

## Step 3 — Commit the Files

```bash
git commit -m "[commit message]"
```

Example:

```bash
git commit -m "Initial commit"
```

## Step 4 — Set the Main Branch Name

```bash
git branch -M main
```

Renames the current branch to `main`.

> Usually required only once when setting up the repository.

## Step 5 — Add the GitHub Remote

```bash
git remote add origin ssh://git@github.com/[username]/[repository-name].git
```

Example:

```bash
git remote add origin ssh://git@github.com/username/project.git
```

> Usually required only once.

## Step 6 — Push to the Main Branch

```bash
git push -u origin main
```

Pushes the local `main` branch to GitHub and configures it to track `origin/main`.

After this first push, future pushes can normally use:

```bash
git push
```

---

# Complete Udai Method

```bash
git init
git add .
git commit -m "Initial commit"
git branch -M main
git remote add origin ssh://git@github.com/[username]/[repository-name].git
git push -u origin main
```

For future updates:

```bash
git add .
git commit -m "Your commit message"
git push
```

---

# Quick Daily Git Workflow

```bash
git status
git pull
git add .
git commit -m "Describe your changes"
git push
```

---

# Useful Branch Workflow

## Create a New Branch

```bash
git switch -c feature-branch
```

or:

```bash
git checkout -b feature-branch
```

## Push It to GitHub

```bash
git push -u origin feature-branch
```

## Switch Back to Main

```bash
git switch main
```

## Pull Latest Main

```bash
git pull
```

## Merge the Feature Branch

```bash
git merge feature-branch
```

## Delete the Local Feature Branch

```bash
git branch -d feature-branch
```

## Delete the Remote Feature Branch

```bash
git push origin --delete feature-branch
```

---

# Useful Repository Cleanup

If a branch was deleted on GitHub but still appears locally as a remote-tracking branch:

```bash
git fetch --prune
```

Then check all branches:

```bash
git branch -a
```

---

# Important Git Concepts

- **Local branch** — A branch on your computer that you can directly modify and commit to.
- **Remote branch** — A branch stored on GitHub or another Git server.
- **Remote-tracking branch** — Your local Git repository's reference to a remote branch, such as `origin/main`.
- **origin** — The default nickname Git normally gives to the remote repository you cloned or added.
- **HEAD** — A pointer to your currently checked-out branch or commit.
- **Upstream branch** — The remote branch associated with your local branch for `git push` and `git pull`.

---

# Command Summary

| Task | Command |
|---|---|
| Initialize repository | `git init` |
| Clone repository | `git clone <repository-url>` |
| Check status | `git status` |
| Stage everything | `git add .` |
| Commit | `git commit -m "message"` |
| List local branches | `git branch` |
| List all branches | `git branch -a` |
| Create and switch branch | `git switch -c <branch>` |
| Switch branch | `git switch <branch>` |
| Delete local branch | `git branch -d <branch>` |
| Delete remote branch | `git push origin --delete <branch>` |
| Fetch updates | `git fetch` |
| Fetch and prune | `git fetch --prune` |
| Pull changes | `git pull` |
| Push changes | `git push` |
| First push of branch | `git push -u origin <branch>` |
| Show remotes | `git remote -v` |
| Show compact history | `git log --oneline` |
| Show Git graph | `git log --oneline --graph --decorate --all` |
