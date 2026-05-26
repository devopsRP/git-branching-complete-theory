## **Git Merge + Git Rebase + Conflict + Conflict Resolution** 

This explanation will cover:

```text
1. What is Merge
2. Why Merge
3. How Merge Works
4. What is Rebase
5. Why Rebase
6. How Rebase Works
7. Merge vs Rebase
8. Conflict
9. Conflict Resolution
10. Best Practices
```

---

# STORY SETUP

Company:

```text
Mirzapur Software Pvt Ltd
```

Project:

```text
Insurance Application
```

Team:

```text
Munna Bhaiya → Backend Developer
Guddu Pandit → Frontend Developer
Bablu → QA
Ravi → DevOps
Kaleen Bhaiya → Production Owner
```

Branches:

```text
main → Production

dev → Development
```

---

# DAY 1 — Current Situation

Production code:

```text
main

A
```

A = Initial Code

---

Ravi creates DEV.

```bash
git checkout main

git checkout -b dev
```

Now:

```text
main
│
dev
```

---

Munna creates feature.

```bash
git checkout dev

git checkout -b feature/snap
```

Guddu creates feature.

```bash
git checkout dev

git checkout -b feature/payment
```

Now:

```text
main

dev
├── feature/snap
└── feature/payment
```

Everything looks good.

---

# PART 1 — GIT MERGE

---

# What is Merge?

Merge means:

> Combine two branch histories and preserve everything.

Think:

```text
Two roads become one
```

Command:

```bash
git merge branch-name
```

---

# MERGE STORY

Munna works.

Commits:

```text
feature/snap

A → M1 → M2
```

Guddu works.

Commits:

```text
dev

A → D1 → D2
```

Current:

```text
dev

A → D1 → D2


feature/snap

A → M1 → M2
```

Now Munna wants latest DEV.

Run:

```bash
git checkout feature/snap

git merge dev
```

---

Git says:

> Okay Munna…
> I will combine both histories.

Result:

```text
dev

A → D1 → D2

          \
feature

A → M1 → M2 → Merge
```

Notice:

Git created:

```text
Merge Commit
```

---

Meaning:

```text
Both histories remain.
```

---

Think like:

Munna:

> Hum apna rasta nahi chodenge.

Guddu:

> Hum bhi nahi.

Git:

> Theek hai dono rakh deta hoon.

````

---

# Real Command

Switch:

```bash
git checkout feature/snap
````

Merge:

```bash
git merge dev
```

Push:

```bash
git push
```

---

# Merge Advantages

### Keeps history

```text
Who did what
```

---

### Safe

Nothing rewritten.

---

### Best for shared branches

```text
dev
main
release
```

---

# Merge Disadvantage

History becomes:

```text
messy
```

Example:

```text
A
 \
  B
 / \
C   M
```

---

# PART 2 — GIT REBASE

---

# What is Rebase?

Rebase means:

> Move your commits and replay them on latest branch.

Command:

```bash
git rebase branch-name
```

---

# REBASE STORY

Current:

```text
dev

A → D1 → D2


feature

A → M1 → M2
```

Munna says:

> Mujhe latest DEV chahiye but clean history bhi chahiye.

Run:

```bash
git checkout feature/snap

git rebase dev
```

Git says:

> Munna…
>
> Main tumhara kaam uthata hoon…
>
> DEV ke upar dubara laga deta hoon.

---

Result:

Before:

```text
A → M1 → M2
```

After:

```text
A → D1 → D2 → M1 → M2
```

Final:

```text
dev

A → D1 → D2


feature

A → D1 → D2 → M1 → M2
```

Notice:

```text
No Merge Commit
```

Clean history.

---

Think:

Guddu:

> Munna pehle humara code lo.

Munna:

> Theek hai hum upar se fir kaam karenge.

````

---

# Rebase Advantages

### Clean history

```text
Linear commits
````

---

### Easy debugging

---

### Better for feature branches

---

# Rebase Disadvantage

History rewritten.

Danger if already pushed.

---

# PART 3 — MERGE vs REBASE

---

## Merge

```text
Combine

History kept

Extra commit YES

Safe YES
```

Diagram:

```text
A---B---C
 \     /
  D---M
```

---

## Rebase

```text
Move commits

History rewritten

Extra commit NO

Clean YES
```

Diagram:

```text
A---B---C---D
```

---

# PART 4 — CONFLICT

Now story becomes interesting.

---

Munna opens:

```java
age=18;
```

Commit.

---

Guddu edits SAME line:

```java
age=21;
```

Current:

```text
feature/snap

age=18


dev

age=21
```

Merge:

```bash
git merge dev
```

Git:

```text
STOP
```

Error:

```text
CONFLICT
```

---

# Why Conflict Happens?

Git sees:

```text
Same file

Same line

Different changes
```

Git cannot decide.

---

Git shows:

```text
<<<<<<< HEAD

age=18;

=======

age=21;

>>>>>>>
```

Meaning:

```text
HEAD
↓

Current Branch


====

Incoming Branch
```

---

Munna:

> Hum 18 rakhte.

Guddu:

> Hum 21.

Bablu:

> Business requirement 21.

Final:

```java
age=21;
```

Save.

---

Stage:

```bash
git add .
```

Commit:

```bash
git commit
```

Done.

---

# Conflict During Rebase

Run:

```bash
git rebase dev
```

Conflict.

Fix.

Continue:

```bash
git rebase --continue
```

---

Abort:

```bash
git rebase --abort
```

---

Skip:

```bash
git rebase --skip
```

---

# Real DevOps Example

Terraform:

Munna:

```tf
vm_size="B2"
```

Guddu:

```tf
vm_size="D4"
```

Merge.

Conflict.

Resolve.

---

# Best Practices

### Use Merge for:

```text
main
dev
release
```

---

### Use Rebase for:

```text
feature/*
```

---

### Pull before work

```bash
git pull
```

---

### Small commits

```bash
git commit -m "updated terraform"
```

---

### PR before merge

```text
Push
↓

PR
↓

Review
↓

Merge
```

---

# Final Memory Trick

```text
Merge
↓

"Sabko saath leke chalo"


Rebase
↓

"Nayi line me dubara chalo"


Conflict
↓

"Decision lo"
```

Flow:

```text
Feature
↓

Rebase
↓

PR
↓

Merge
↓

Production
```

Now Merge + Rebase + Conflict should feel natural.
