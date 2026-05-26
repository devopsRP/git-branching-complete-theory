# The Story of Merge vs Rebase

## Understanding Branch Integration From Zero to Expert

Munna Bhaiya joined a team project.

Manager said:

> “Before opening PR, rebase your branch.”

Munna Bhaiya froze.

Inside his mind:

```text
Merge?
Rebase?
Aren't both combining code?
```

Yes.

But also—

No.

This chapter explains the complete story.

---

# Scene 1 — Why Merge/Rebase Even Exist?

Project starts.

Main branch:

```text
main

A
↓
B
↓
C
```

Munna Bhaiya creates feature branch:

```bash
git checkout -b login
```

History becomes:

```text
main

A
↓
B
↓
C


login

A
↓
B
↓
C
```

Now branches become independent.

---

# Scene 2 — Parallel Development Begins

Munna Bhaiya works:

```text
login

A
↓
B
↓
C
↓
D
↓
E
```

Meanwhile Guddu pushes:

```text
main

A
↓
B
↓
C
↓
F
↓
G
```

Now situation:

```text
           D
          /
A—B—C
      \
       F—G
```

Question:

How do we combine?

Answer:

```text
Merge
or
Rebase
```

---

# Part 1 — Merge

---

# Scene 3 — What is Merge?

Munna Bhaiya asks:

> “What does merge mean?”

Definition:

> Merge combines histories while preserving branch structure.

Command:

```bash
git merge login
```

Visualization:

Before:

```text
main

A—B—C—F—G

login

A—B—C—D—E
```

After:

```text
A—B—C—F—G
       \   \
        D—E—M
```

`M`

=

Merge Commit

---

# Scene 4 — Merge Story

Git says:

> “I will combine both histories.”

It creates:

```text
New Commit
```

That commit remembers:

```text
Parent 1 → main
Parent 2 → login
```

Meaning:

```text
Nothing rewritten
```

---

# Scene 5 — Types of Merge

---

## Fast Forward Merge

Condition:

No divergence.

Before:

```text
A—B—C
     \
      D
```

Command:

```bash
git merge login
```

Result:

```text
A—B—C—D
```

No merge commit.

History stays clean.

---

## Three-Way Merge

Both changed.

Before:

```text
A—B—C
 \   \
  D   E
```

After:

```text
A—B—C
 \   \
  D   E
   \ /
    M
```

Merge commit created.

---

# Scene 6 — Internal Merge Algorithm

Git finds:

```text
Common Ancestor
```

Example:

```text
A
```

Compare:

```text
A→main
A→feature
```

Combine changes.

Produce result.

---

# Scene 7 — Merge Conflict

Munna Bhaiya edits:

```js
name="Munna"
```

Guddu edits:

```js
name="Guddu"
```

Merge:

```text
Conflict
```

Git cannot choose.

File becomes:

```text
<<<<<<< HEAD
Munna
=======
Guddu
>>>>>>>
```

Developer resolves.

Then:

```bash
git add .

git commit
```

Done.

---

# Scene 8 — Advantages of Merge

```text
History preserved
Safe
No rewriting
Easy
Good for teams
```

---

# Scene 9 — Disadvantages of Merge

```text
Extra commits
Complex history
Graph becomes messy
```

Example:

```text
A
↓
B
↓
M
↓
N
↓
M
```

---

# Part 2 — Rebase

---

# Scene 10 — What is Rebase?

Munna Bhaiya asks:

> “Then why rebase?”

Definition:

> Rebase moves branch commits onto another base and rewrites history.

Command:

```bash
git rebase main
```

Git says:

> “I'll replay your work as if you started later.”

---

# Scene 11 — Rebase Story

Before:

```text
main

A—B—C—F—G


login

A—B—C—D—E
```

Git removes:

```text
D
E
```

Temporarily.

Moves branch.

Reapplies.

Result:

```text
A—B—C—F—G—D'—E'
```

Notice:

```text
D ≠ D'
E ≠ E'
```

Commits recreated.

---

# Scene 12 — What Rebase Actually Does

Internally:

Step 1

Find common ancestor.

```text
C
```

Step 2

Extract commits.

```text
D
E
```

Step 3

Move branch.

```text
F
G
```

Step 4

Replay.

```text
D'
E'
```

History rewritten.

---

# Scene 13 — Why Rebase Feels Magical

Before:

```text
Messy
```

```text
A
 \
  B
   \
    C
```

After:

```text
Straight Line
```

```text
A—B—C
```

Looks cleaner.

---

# Scene 14 — Rebase Conflict

Conflicts happen during replay.

Example:

```bash
git rebase main
```

Conflict.

Fix.

Continue:

```bash
git rebase --continue
```

Abort:

```bash
git rebase --abort
```

Skip:

```bash
git rebase --skip
```

---

# Scene 15 — Interactive Rebase (Power Tool)

Munna Bhaiya discovers:

```bash
git rebase -i HEAD~5
```

Git opens:

```text
pick
pick
pick
```

Actions:

---

## Reorder

```text
Move commits
```

---

## Squash

Combine.

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

## Drop

Delete commit.

---

## Edit

Modify commit.

---

## Rename

Change message.

---

Interactive rebase edits history.

---

# Scene 16 — Merge vs Rebase Philosophy

Merge says:

> “History happened like this.”

Rebase says:

> “History should look clean.”

---

# Scene 17 — Visual Comparison

Merge:

```text
A—B—C
 \   \
  D   E
   \ /
    M
```

Preserves branches.

---

Rebase:

```text
A—B—C—D'—E'
```

Linear history.

---

# Scene 18 — Golden Rule of Rebase

Manager tells Munna Bhaiya:

> Never rebase public shared branches.

Why?

Because rebase rewrites history.

Bad:

```bash
git rebase main
git push
```

After shared.

Good:

```text
Local Feature Branch
```

Safe.

---

# Scene 19 — Merge + Rebase Together

Modern workflow:

Feature branch:

```bash
git rebase main
```

Then PR:

```text
Squash Merge
```

Clean history.

---

# Scene 20 — Real Team Workflow

Daily:

```bash
git checkout feature

git fetch

git rebase origin/main

git push --force-with-lease
```

PR.

Merge.

Done.

---

# Scene 21 — Command Cheat Sheet

Merge:

```bash
git merge branch
```

Abort:

```bash
git merge --abort
```

---

Rebase:

```bash
git rebase branch
```

Continue:

```bash
git rebase --continue
```

Abort:

```bash
git rebase --abort
```

Interactive:

```bash
git rebase -i HEAD~5
```

---

# Final Lesson from Munna Bhaiya

> “Merge respects history.
> Rebase rewrites history.
> Both combine code—
> but they tell different stories of how the code came to exist.”
