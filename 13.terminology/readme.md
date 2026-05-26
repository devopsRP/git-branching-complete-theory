# Git Terminology Dictionary

## The Complete Story of Git Vocabulary (From Zero to Expert)

After learning Git for some time…

Munna Bhaiya noticed something.

People were speaking strange words:

```text
Repo
Commit
Branch
Checkout
Rebase
Merge
HEAD
Origin
Upstream
Stash
Remote
Tag
Detached HEAD
```

He thought:

> “I know commands… but I don't know the language.”

That day he decided:

> “First understand the words. Then Git becomes easy.”


---

# 1. Version Control

### Definition

A system that tracks changes over time.

Think:

```text
Google Docs History
```

Instead of:

```text
File overwrite
```

You get:

```text
Version 1
↓
Version 2
↓
Version 3
```

Purpose:

```text
Track
Restore
Compare
Collaborate
```

---

# 2. Repository (Repo)

### Definition

A project plus its complete history.

Structure:

```text
Project
+
History
+
Metadata
```

Example:

```text
my-app/
├── src
├── README
└── .git
```

Repository = folder managed by Git.

Create:

```bash
git init
```

---

# 3. Local Repository

### Definition

Repository stored on your machine.

Visualization:

```text
Laptop
↓
Repository
```

Contains:

```text
Files
Commits
Branches
History
```

---

# 4. Remote Repository

### Definition

Repository stored somewhere else.

Example:

```text
GitHub
GitLab
Bitbucket
```

Purpose:

```text
Backup
Share
Collaborate
```

---

# 5. Working Directory

### Definition

Area where you actively edit files.

Example:

```text
project/

app.js
```

Change code here.

Visualization:

```text
Code
↓
Working Directory
```

---

# 6. Staging Area (Index)

### Definition

Temporary area before commit.

Think:

```text
Selected changes
```

Command:

```bash
git add
```

Flow:

```text
Working Directory
↓
Staging Area
```

---

# 7. Commit

### Definition

Permanent snapshot of project.

Command:

```bash
git commit
```

Visualization:

```text
Commit

Files
History
Message
```

Example:

```text
Add login
```

---

# 8. Commit Hash

### Definition

Unique commit identifier.

Example:

```text
a82d91c
```

Purpose:

```text
Identify commit
```

Commands:

```bash
git log
```

---

# 9. Branch

### Definition

Movable pointer to commits.

Example:

```text
main
 │
 └── login
```

Create:

```bash
git branch login
```

Purpose:

```text
Isolation
```

---

# 10. Main Branch

### Definition

Primary development branch.

Examples:

```text
main
master
```

Usually:

```text
Production ready
```

---

# 11. HEAD

### Definition

Pointer to current location.

Example:

```text
HEAD
↓
main
```

Meaning:

```text
Current commit
```

---

# 12. Detached HEAD

### Definition

HEAD points directly to commit.

Example:

```text
HEAD
↓
commit
```

Not branch.

---

# 13. Checkout

### Definition

Move to another branch or commit.

Command:

```bash
git checkout branch
```

Modern:

```bash
git switch
```

---

# 14. Clone

### Definition

Create local copy.

Command:

```bash
git clone URL
```

Downloads:

```text
Files
Branches
History
```

---

# 15. Fetch

### Definition

Download updates.

No merge.

Command:

```bash
git fetch
```

---

# 16. Pull

### Definition

Fetch + Merge.

Command:

```bash
git pull
```

Flow:

```text
Download
+
Integrate
```

---

# 17. Push

### Definition

Upload commits.

Command:

```bash
git push
```

Flow:

```text
Local
↓
Remote
```

---

# 18. Merge

### Definition

Combine histories.

Command:

```bash
git merge
```

Result:

```text
Branch A
+
Branch B
```

---

# 19. Rebase

### Definition

Replay commits onto another base.

Command:

```bash
git rebase
```

Creates:

```text
Clean history
```

---

# 20. Cherry-Pick

### Definition

Copy selected commit.

Command:

```bash
git cherry-pick
```

Purpose:

```text
Bring only one commit
```

---

# 21. Conflict

### Definition

Git cannot decide automatically.

Example:

```text
Same line changed
```

Resolve manually.

---

# 22. Merge Commit

### Definition

Special commit created during merge.

Example:

```text
Parent A
Parent B
```

---

# 23. Reflog

### Definition

Local movement history.

Command:

```bash
git reflog
```

Purpose:

```text
Recover lost work
```

---

# 24. Stash

### Definition

Temporary hidden storage.

Command:

```bash
git stash
```

Use:

```text
Pause work
```

---

# 25. Reset

### Definition

Move repository state.

Command:

```bash
git reset
```

Types:

```text
soft
mixed
hard
```

---

# 26. Restore

### Definition

Restore file content.

Command:

```bash
git restore
```

---

# 27. Revert

### Definition

Undo using new commit.

Command:

```bash
git revert
```

Safe undo.

---

# 28. Tag

### Definition

Named reference to commit.

Example:

```text
v1.0
```

---

# 29. Remote

### Definition

Named connection.

Example:

```text
origin
```

View:

```bash
git remote -v
```

---

# 30. Origin

### Definition

Default remote nickname.

Example:

```text
origin
↓
github
```

---

# 31. Upstream

### Definition

Default tracking branch.

Example:

```text
main
↓
origin/main
```

---

# 32. Fork

### Definition

Personal copy of repository.

Example:

```text
Original
↓
Your Copy
```

---

# 33. Pull Request (PR)

### Definition

Request to merge changes.

Flow:

```text
Branch
↓
Review
↓
Merge
```

---

# 34. Fast Forward

### Definition

Move pointer without merge commit.

---

# 35. Squash

### Definition

Combine commits.

Before:

```text
A
B
C
```

After:

```text
ABC
```

---

# 36. Rebase Interactive

### Definition

Edit history manually.

Command:

```bash
git rebase -i
```

---

# 37. Hook

### Definition

Automatic scripts.

Example:

```text
pre-commit
post-merge
```

---

# 38. Tagging

### Definition

Mark release points.

Example:

```text
v2.1
```

---

# 39. Object

### Definition

Internal Git storage unit.

Types:

```text
Blob
Tree
Commit
Tag
```

---

# 40. Blob

### Definition

Stores file content.

---

# 41. Tree

### Definition

Stores folder structure.

---

# 42. DAG

### Definition

Directed Acyclic Graph.

Git's history structure.

---

# 43. Index

### Definition

Another name for staging area.

---

# 44. Clean Working Tree

### Definition

No pending changes.

Check:

```bash
git status
```

Output:

```text
nothing to commit
```

---

# 45. Tracking Branch

### Definition

Branch connected to remote.

Example:

```text
main
↔
origin/main
```

---

# 46. Workspace

### Definition

Entire active environment.

Includes:

```text
Files
Git
Branches
```

---

# Final Lesson from Munna Bhaiya

> “Git commands become easy when Git vocabulary becomes natural.
> Learn the language first—then the workflow becomes obvious.”
