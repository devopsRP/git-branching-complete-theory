
# 🚀 Git Mastery — From Zero to Production

> Learn Git from fundamentals to production workflows through story-based learning and practical examples.

---

# 📚 Introduction

This repository is designed to teach Git in a way that helps you understand not only **how to use Git**, but also **why each concept exists**.

Instead of memorizing commands, this guide focuses on building intuition.

Inside this repository, you will learn:

* History of Git and why it was created
* What Git and GitHub actually are
* Repository architecture
* Local vs Remote repository
* Complete Git workflow
* Authentication and configuration
* GitHub push requirements
* Branching strategies
* Merge and Rebase
* Pull Requests
* Git conflicts
* Real-world development scenarios

By the end, you should be able to understand:

```text
Code
↓
Repository
↓
Commit
↓
Branch
↓
Review
↓
Merge
↓
Deploy
```

---

# 🎯 What You Will Learn

---

## 1. History of Git

Learn:

* Problems before Git
* Why Git was created
* Evolution of source control
* Why modern teams use Git

---

## 2. Understanding Git

Topics:

* What Git actually is
* Distributed architecture
* Snapshot model
* Commit history
* Internal Git concepts

Core concepts:

```text
Repository
Commit
Branch
Merge
History
```

---

## 3. Understanding GitHub

Topics:

* What GitHub is
* Difference between Git and GitHub
* Remote repositories
* Collaboration
* Pull Requests
* Code reviews

---

## 4. Repository Deep Dive

Learn:

### Repository

```text
Files
+
History
+
Metadata
```

### Local Repository

Required for:

```text
git add
git commit
git push
```

Create:

```bash
git init
```

---

### Remote Repository

Required for:

```text
Push
Sharing
Collaboration
```

---

## 5. Complete Git Workflow

Understand:

```text
Write Code
↓
Working Directory
↓
git add
↓
Staging Area
↓
git commit
↓
Local Repository
↓
git push
↓
Remote Repository
```

Topics:

* Working Directory
* Staging Area
* Commit
* Push
* Pull
* Fetch
* Clone

---

## 6. GitHub Push Requirements

Checklist:

```text
Install Git
↓
Configure Identity
↓
Initialize Repository
↓
Create Commit
↓
Create Remote
↓
Authenticate
↓
Push
```

Commands:

```bash
git config --global user.name "Your Name"

git config --global user.email "your@email.com"

git init

git add .

git commit -m "first commit"

git remote add origin URL

git push -u origin main
```

---

## 7. Git Config & Authentication

Topics:

* Git identity
* Config hierarchy
* Personal Access Token
* SSH Authentication
* Credential management

---

## 8. Branching Strategy

Learn:

* Feature Branch Workflow
* GitHub Flow
* Git Flow
* Trunk-Based Development
* Release Workflow
* Hotfix Workflow

---

## 9. Merge & Rebase

Learn:

### Merge

```text
Preserve History
```

### Rebase

```text
Rewrite History
```

---

## 10. Pull Requests

Topics:

* PR lifecycle
* Reviews
* Approval process
* Merge strategies
* CI/CD

---

## 11. Git Conflicts

Learn:

* Merge conflict
* Rebase conflict
* File conflict
* Conflict resolution

---

# ⚡ Git Commands Cheat Sheet

| Command           | Definition            |
| ----------------- | --------------------- |
| `git init`        | Create repository     |
| `git clone`       | Download repository   |
| `git status`      | Show changes          |
| `git add`         | Stage changes         |
| `git commit`      | Save snapshot         |
| `git push`        | Upload commits        |
| `git pull`        | Download and merge    |
| `git fetch`       | Download only         |
| `git branch`      | Manage branches       |
| `git checkout`    | Switch branch         |
| `git switch`      | Change branch         |
| `git merge`       | Combine histories     |
| `git rebase`      | Replay commits        |
| `git stash`       | Temporarily save work |
| `git restore`     | Restore files         |
| `git reset`       | Move repository state |
| `git revert`      | Undo via commit       |
| `git remote`      | Manage remotes        |
| `git config`      | Configure Git         |
| `git diff`        | Compare changes       |
| `git log`         | Show history          |
| `git cherry-pick` | Apply commit          |
| `git tag`         | Mark release          |
| `git clean`       | Remove untracked      |
| `git rm`          | Remove file           |
| `git mv`          | Rename file           |
| `git show`        | Show details          |
| `git blame`       | Track line owner      |
| `git reflog`      | Show HEAD history     |

---

# 🧠 Goal

Understand Git deeply enough that commands become obvious—not memorized.
