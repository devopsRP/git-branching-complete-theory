# The Story of Conflicts in Git

## Understanding Every Type of Conflict in Git — Why They Happen, How Git Thinks, and How Developers Resolve Them

Munna Bhaiya felt confident.

One day he opened a PR.

Pressed Merge.

Suddenly.

Git showed:

```text
CONFLICT
```

Munna Bhaiya froze.

Inside his mind:

```text
What broke?

Did I lose code?

Should I delete repo?
```

Senior smiled and said:

> “Relax. Conflict means Git became confused—not broken.”

This chapter is the complete story.

---

# Scene 1 — What is a Conflict?

Git works by comparing changes.

Most of the time Git combines automatically.

Example:

Munna Bhaiya edits:

```text
login.js
```

Guddu edits:

```text
payment.js
```

Git says:

```text
Easy.
No conflict.
```

But if both edit same thing—

Git gets confused.

Conflict happens.

Definition:

> Conflict happens when Git cannot automatically decide which change should survive.

Conflict means:

```text
Multiple valid possibilities
+
No safe automatic decision
```

---

# Scene 2 — How Git Normally Merges

Original:

```js
function greet() {
 return "Hello";
}
```

Munna Bhaiya changes:

```js
function greet() {
 return "Hello Munna";
}
```

Guddu changes another file.

Git merges automatically.

No conflict.

---

# Scene 3 — The First Real Conflict (Content Conflict)

Original:

```js
function greet() {
 return "Hello";
}
```

Munna Bhaiya:

```js
function greet() {
 return "Hello Munna";
}
```

Guddu:

```js
function greet() {
 return "Hello Guddu";
}
```

Now Git thinks:

```text
Both changed same line.
Which one should I keep?
```

Conflict.

Output:

```text
CONFLICT (content)
```

File becomes:

```text
<<<<<<< HEAD
return "Hello Munna";
=======
return "Hello Guddu";
>>>>>>> feature
```

---

# Scene 4 — Understanding Conflict Markers

Munna Bhaiya opens file.

Sees:

```text
<<<<<<< HEAD
```

Meaning:

Current branch.

---

```text
=======
```

Divider.

---

```text
>>>>>>> feature
```

Incoming branch.

---

Example:

```text
<<<<<<< HEAD
Current code
=======
Incoming code
>>>>>>> branch
```

You manually choose.

---

# Scene 5 — Resolving Content Conflict

Option 1

Keep current:

```js
return "Hello Munna";
```

---

Option 2

Keep incoming:

```js
return "Hello Guddu";
```

---

Option 3

Combine:

```js
return "Hello Munna & Guddu";
```

Then:

```bash
git add .

git commit
```

Resolved.

---

# Scene 6 — Merge Conflict

Story:

Main:

```text
A—B—C
```

Feature:

```text
A—B—D
```

Merge:

```bash
git merge feature
```

Conflict.

Reason:

Git cannot combine.

Resolve.

Commit.

---

# Scene 7 — Rebase Conflict

Munna Bhaiya runs:

```bash
git rebase main
```

Git starts replaying commits.

Commit D conflicts.

Git stops.

Output:

```text
CONFLICT
```

Flow:

```text
Replay
↓
Conflict
↓
Resolve
↓
Continue
```

Commands:

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

# Scene 8 — Add/Add Conflict

Original:

File doesn't exist.

Munna Bhaiya creates:

```text
config.js
```

Guddu also creates:

```text
config.js
```

Merge.

Git:

```text
Both created same file.
```

Conflict.

Output:

```text
add/add conflict
```

Resolve:

Choose:

```text
One
or
Merge both
```

---

# Scene 9 — Modify/Delete Conflict

Original:

```text
README.md
```

Munna Bhaiya edits.

Guddu deletes.

Merge.

Git asks:

```text
Keep edits?
Delete file?
```

Conflict.

Output:

```text
modify/delete conflict
```

Choices:

```text
Keep file
Delete file
```

---

# Scene 10 — Rename Conflict

Original:

```text
app.js
```

Munna Bhaiya:

```text
auth.js
```

Guddu:

```text
login.js
```

Git:

```text
Two renames.
```

Conflict.

Output:

```text
rename conflict
```

Choose final name.

---

# Scene 11 — Rename + Modify Conflict

Munna Bhaiya:

```text
Rename file
```

Guddu:

```text
Modify old file
```

Git:

```text
Where should modifications go?
```

Conflict.

Resolve manually.

---

# Scene 12 — Delete/Delete Conflict

Original:

```text
old.js
```

Both delete.

Usually automatic.

Sometimes conflict appears depending on context.

Resolve:

```bash
git add
```

Done.

---

# Scene 13 — Binary File Conflict

Munna Bhaiya changes:

```text
logo.png
```

Guddu changes same.

Git:

```text
Cannot merge images.
```

Conflict.

Resolve:

Choose version.

Commands:

```bash
git checkout --ours logo.png
```

or

```bash
git checkout --theirs logo.png
```

---

# Scene 14 — Directory Conflict

Original:

```text
src/
```

Munna Bhaiya:

```text
move → frontend/
```

Guddu:

```text
move → app/
```

Git confused.

Conflict.

Resolve structure manually.

---

# Scene 15 — Cherry-Pick Conflict

Munna Bhaiya:

```bash
git cherry-pick commit
```

Git applies commit.

Conflict.

Commands:

Continue:

```bash
git cherry-pick --continue
```

Abort:

```bash
git cherry-pick --abort
```

---

# Scene 16 — Stash Conflict

Munna Bhaiya:

```bash
git stash
```

Later:

```bash
git stash pop
```

Git tries restoring.

Conflict.

Resolve.

Continue.

---

# Scene 17 — Pull Conflict

Munna Bhaiya:

```bash
git pull
```

Remote changed.

Local changed.

Conflict.

Flow:

```text
Remote
↓
Merge
↓
Conflict
```

Resolve.

Commit.

---

# Scene 18 — Force Push Conflict

Munna Bhaiya:

```bash
git push
```

Git:

```text
Updates rejected
```

Remote newer.

Fix:

```bash
git pull
```

OR carefully:

```bash
git push --force-with-lease
```

---

# Scene 19 — Detached HEAD Confusion (Not Conflict but Feels Like One)

Munna Bhaiya:

```bash
git checkout commit
```

Now:

```text
HEAD detached
```

Not conflict.

But often confused.

Fix:

```bash
git switch branch
```

---

# Scene 20 — Conflict Resolution Workflow

Whenever conflict appears:

Step 1

Check:

```bash
git status
```

Step 2

Open conflicted file.

Step 3

Edit.

Remove markers.

Step 4

Stage.

```bash
git add .
```

Step 5

Complete.

Merge:

```bash
git commit
```

Rebase:

```bash
git rebase --continue
```

---

# Scene 21 — How Teams Avoid Conflicts

Rules:

```text
Small PRs
Frequent pull
Short branches
Communication
Feature branches
Rebase regularly
```

---

# Scene 22 — Complete Conflict Mental Model

```text
Branch A
     ↓

Git Decision Engine

     ↓

Automatic?
   /     \
 Yes     No
  ↓       ↓
Merge   Conflict
```

---

# Final Lesson from Munna Bhaiya

> “Conflict does not mean code is broken.
> Conflict means Git stopped and asked humans to make the decision.”
