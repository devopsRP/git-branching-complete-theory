# The Story of Pull Request (PR)

## Understanding Git PR From Zero to Expert — Why It Exists, How It Works, and What Actually Happens


Munna Bhaiya joined a software company.

First day.

Manager said:

> “Create a PR.”

Munna Bhaiya nodded confidently.

Inside his mind:

```text
What is PR?
```

He thought:

> “Maybe PR means Push Request?”

Wrong.

That day he discovered one of the most important concepts in modern development.

This is that story.

---

# Scene 1 — The World Without Pull Requests

Company project:

```text
main
```

Everyone works on it.

Team:

```text
Munna Bhaiya
Guddu
Bablu
Golu
```

Munna Bhaiya changes login.

Guddu changes payment.

Bablu changes dashboard.

Everyone directly pushes:

```text
main
```

Result:

```text
Chaos
```

Problems:

```text
Broken code
Unexpected bugs
No review
No approval
Production failures
```

Manager gets angry.

Team creates a rule:

> Nobody pushes directly to main.

That rule introduces—

# Pull Request (PR)

---

# Scene 2 — What is Pull Request?

Munna Bhaiya asks:

> “What exactly is PR?”

Definition:

> Pull Request (PR) is a request to merge one branch into another after review.

Simple language:

> “Please review my work and pull it into your branch.”

Visualization:

```text
Feature Branch
      ↓
Pull Request
      ↓
Review
      ↓
Merge
      ↓
Main
```

PR is:

```text
Request
Not merge
```

---

# Scene 3 — Why Is It Called Pull Request?

Munna Bhaiya got confused.

He said:

> “But I pushed code… why pull request?”

Because conceptually:

You are saying:

> “Please pull my changes.”

Meaning:

```text
My Branch
↓
Request
↓
Your Branch pulls changes
```

---

# Scene 4 — The First Real PR Workflow

Company project:

```text
main
```

Manager says:

> Never work directly on main.

Munna Bhaiya creates:

```bash
git checkout -b login-feature
```

Now:

```text
main
 │
 └── login-feature
```

Work starts.

---

# Scene 5 — Development Happens

Munna Bhaiya writes code.

Stage:

```bash
git add .
```

Commit:

```bash
git commit -m "Add login page"
```

Push:

```bash
git push origin login-feature
```

Now:

```text
GitHub

main
login-feature
```

But nothing merged.

---

# Scene 6 — Creating the PR

Munna Bhaiya opens GitHub.

GitHub shows:

```text
Compare & Pull Request
```

Click.

Form appears:

---

Title:

```text
Add Login System
```

---

Description:

```text
Implemented:
- Login page
- Validation
- Session handling
```

---

Select:

```text
Base Branch:
main

Compare Branch:
login-feature
```

Create.

PR opens.

Visualization:

```text
login-feature
      ↓
Create PR
      ↓
Open Review
```

---

# Scene 7 — Anatomy of a Pull Request

Munna Bhaiya sees PR contains:

---

Title

Example:

```text
Add login functionality
```

---

Description

Explains:

```text
What changed
Why changed
How tested
```

---

Commits

Example:

```text
Commit A
Commit B
Commit C
```

---

Files Changed

Example:

```text
+150
-30
```

---

Reviewers

Example:

```text
Manager
Senior Developer
```

---

Checks

Example:

```text
Build
Tests
Security
```

---

Conversation

Comments.

---

Approvals.

---

Merge Button.

---

# Scene 8 — What Happens Internally?

Munna Bhaiya thought:

> “Does PR move files?”

No.

PR compares commits.

Example:

Before:

```text
main

Commit1
Commit2
```

Feature:

```text
Commit1
Commit2
Commit3
Commit4
```

PR computes:

```text
Difference:
Commit3
Commit4
```

Only differences shown.

---

# Scene 9 — Code Review (Heart of PR)

Senior opens PR.

Comments:

```text
Line 45:
Rename variable

Line 82:
Handle null case
```

Munna Bhaiya updates.

Commit:

```bash
git commit
```

Push again:

```bash
git push
```

Magic happens.

PR updates automatically.

---

# Scene 10 — Why Teams Love PR

Without PR:

```text
Push
Done
```

With PR:

```text
Write
Review
Improve
Approve
Merge
```

Benefits:

```text
Code quality
Knowledge sharing
Bug detection
Discussion
Audit trail
```

---

# Scene 11 — CI/CD in PR

Company adds automation.

When PR opens:

```text
Run Tests
Build App
Security Scan
Lint
```

If fail:

```text
❌ Cannot Merge
```

Visualization:

```text
PR
↓
Automation
↓
Pass
↓
Merge
```

---

# Scene 12 — Approval Workflow

Rules:

```text
1 Approval
Build Success
No Conflicts
```

Only then:

```text
Merge Enabled
```

---

# Scene 13 — Merge Conflict (The Famous Battle)

Munna Bhaiya edits:

```text
app.js line 10
```

Guddu edits same line.

PR:

```text
Conflict
```

Git cannot decide.

Manual resolution needed.

Example:

```text
<<<<<<<
Munna Code
=======
Guddu Code
>>>>>>>
```

Developer chooses.

Commit.

Push.

PR updates.

---

# Scene 14 — Merge Strategies

GitHub offers:

---

## Merge Commit

Creates extra merge commit.

```text
main
 └─ Merge
```

---

## Squash Merge

Combines commits.

Before:

```text
A
B
C
```

After:

```text
Single Commit
```

---

## Rebase Merge

Keeps linear history.

Before:

```text
main
feature
```

After:

```text
Straight Line
```

---

# Scene 15 — Draft PR

Munna Bhaiya isn't finished.

Creates:

```text
Draft Pull Request
```

Meaning:

```text
Do not merge yet
```

Purpose:

```text
Early feedback
```

---

# Scene 16 — PR Lifecycle

Complete journey:

```text
Create Branch
↓
Code
↓
Commit
↓
Push
↓
Open PR
↓
Review
↓
Fix
↓
Approve
↓
Merge
↓
Delete Branch
```

---

# Scene 17 — Local Git vs PR

Munna Bhaiya asks:

> “Is PR a Git command?”

Answer:

No.

PR belongs to hosting platforms.

Examples:

* GitHub
* GitLab
* Bitbucket

Git itself only knows:

```text
branch
merge
push
pull
```

PR is platform workflow.

---

# Scene 18 — Daily PR Workflow

Every day:

```bash
git checkout -b feature

code

git add .

git commit -m "work"

git push origin feature
```

Then:

```text
Open PR
Review
Merge
```

---

# Scene 19 — Real Mental Model

```text
Main Branch
     ↑
     │
Pull Request
     │
Feature Branch
```

PR means:

> “I finished my work. Please inspect it before it becomes part of the main project.”

---

# Final Lesson from Munna Bhaiya

> “Commit saves work.
> Push shares work.
> Pull Request earns trust before merging work.”
