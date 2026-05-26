**real beginner confusion: master vs main when initializing Git and pushing to GitHub**.

This is one of the most common Git problems learners face.

---

# Situation

You created a local Git repository:

```bash
git init
```

Now you run:

```bash
git branch
```

and see:

```text
* master
```

But later you do:

```bash
git push origin main
```

and Git gives error:

```text
error: src refspec main does not match any
```

Why?

Because **your local branch is `master` but you're trying to push `main`.**

---

# Step 1 — What happens during `git init`

When you initialize Git:

```bash
git init
```

Git creates:

```text
.git/
```

and creates an initial branch.

Older Git versions create:

```text
master
```

Example:

```bash
git init
git branch
```

Output:

```text
* master
```

Meaning:

```text
Local Repository
     ↓
master
```

At this point:

* No commits exist
* No GitHub exists
* Only local branch exists

---

# Step 2 — Why GitHub shows `main`

When you create repository in GitHub:

```text
my-app
```

GitHub now creates default branch:

```text
main
```

So GitHub side becomes:

```text
GitHub
   ↓
main
```

Now:

```text
LOCAL → master
REMOTE → main
```

Branch names are different.

---

# Step 3 — The Problem

You try:

```bash
git push origin main
```

Git checks:

```text
Do I have local branch called main?
```

Local:

```text
master
```

Git says:

```text
No branch named main found
```

Error:

```text
error: src refspec main does not match any
```

---

# Solution 1 (Recommended) → Rename master → main

If you want modern naming:

### Create commit first

```bash
git add .
git commit -m "Initial commit"
```

Rename:

```bash
git branch -M main
```

Check:

```bash
git branch
```

Output:

```text
* main
```

Now push:

```bash
git push -u origin main
```

Success.

Flow:

```text
LOCAL           REMOTE

master
   ↓ rename
main --------> main
```

---

# Solution 2 → Push master directly

If you don't want rename:

```bash
git push origin master
```

Flow:

```text
LOCAL           REMOTE

master --------> master
```

But modern practice:

```text
Use main
```

---

# Why `git branch -M main`?

Command:

```bash
git branch -M main
```

Meaning:

```text
-M
force rename branch
```

Convert:

```text
master → main
```

---

# Real Beginner Example

You do:

```bash
mkdir app

cd app

git init

git add .

git commit -m "first"

git remote add origin repo-url

git push origin main
```

Fails ❌

Because:

```text
Current branch = master
```

Fix:

```bash
git branch -M main

git push -u origin main
```

Success ✅

---

# How to check current branch before push

Always run:

```bash
git branch
```

Output:

```text
* master
```

or

```text
* main
```

Push accordingly:

```bash
git push origin <branch-name>
```

---

# One-line memory trick

```text
git init → creates local branch (master/main)
git push → branch name must exist locally
GitHub → usually expects main
```

That’s the exact reason learners get confused between `master` and `main`.
