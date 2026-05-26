**Git Branch commands** and understand **every word of every command** like an interviewer expects.

Think:

```text
Command = Action + Object + Option
```

---

# 1. `git branch`

Command:

```bash
git branch
```

Breakdown:

```text
git      → Version control tool
branch   → Work with branches
```

Purpose:

```text
Show all local branches
```

Example:

```bash
git branch
```

Output:

```text
* main
feature/login
feature/payment
```

Meaning:

```text
* → Current branch
```

You are currently inside:

```text
main
```

---

# 2. `git branch <branch-name>`

Command:

```bash
git branch feature/login
```

Breakdown:

```text
git      → Git tool

branch   → Create branch

feature/login
         ↓
Branch Name
```

Purpose:

```text
Create branch only
(No switching)
```

Before:

```text
main
```

After:

```text
main
feature/login
```

Current:

```text
main
```

Still same.

---

# 3. `git checkout <branch>`

Command:

```bash
git checkout feature/login
```

Breakdown:

```text
git       → Tool

checkout  → Move to another branch

feature/login
          ↓
Target branch
```

Purpose:

```text
Switch branch
```

Before:

```text
main
```

After:

```text
feature/login
```

---

# 4. `git checkout -b`

Command:

```bash
git checkout -b feature/login
```

Breakdown:

```text
git

checkout
      ↓
Switch branch

-b
↓
Create branch before switching

feature/login
↓
Branch Name
```

Meaning:

```text
Create + Switch
```

Equivalent:

```bash
git branch feature/login

git checkout feature/login
```

Two commands combined.

---

Example:

Before:

```text
main
```

Run:

```bash
git checkout -b feature/login
```

After:

```text
main
feature/login
          ↑
Current
```

---

# 5. `git switch`

Modern alternative.

Command:

```bash
git switch feature/login
```

Breakdown:

```text
git

switch
↓
Move branch

feature/login
↓
Target
```

Purpose:

```text
Switch only
```

---

# 6. `git switch -c`

Command:

```bash
git switch -c feature/api
```

Breakdown:

```text
switch
↓
Move

-c
↓
Create

feature/api
↓
Branch
```

Meaning:

```text
Create + Switch
```

Equivalent:

```bash
git checkout -b feature/api
```

---

# 7. `git branch -a`

Command:

```bash
git branch -a
```

Breakdown:

```text
branch

-a
↓
all
```

Purpose:

Show:

```text
Local + Remote branches
```

Output:

```text
main
feature/login

origin/main
origin/develop
```

---

# 8. `git branch -r`

Command:

```bash
git branch -r
```

Breakdown:

```text
branch

-r
↓
remote
```

Purpose:

Show:

```text
Only remote branches
```

Output:

```text
origin/main
origin/develop
```

---

# 9. `git branch -m`

Command:

```bash
git branch -m main
```

Breakdown:

```text
branch

-m
↓
move(rename)

main
↓
New name
```

Purpose:

Rename current branch.

Example:

Before:

```text
master
```

Run:

```bash
git branch -m main
```

After:

```text
main
```

---

# 10. `git branch -M`

Command:

```bash
git branch -M main
```

Breakdown:

```text
-M
↓
Force Rename
```

Purpose:

Rename even if target exists.

Example:

```bash
git branch -M main
```

---

# 11. `git branch -d`

Command:

```bash
git branch -d feature/login
```

Breakdown:

```text
branch

-d
↓
delete safely

feature/login
↓
Delete branch
```

Purpose:

Delete merged branch.

Example:

Before:

```text
main
feature/login
```

After:

```text
main
```

---

# 12. `git branch -D`

Command:

```bash
git branch -D feature/login
```

Breakdown:

```text
-D
↓
Force Delete
```

Deletes even if unmerged.

Dangerous.

---

# 13. `git merge`

Command:

```bash
git merge feature/login
```

Breakdown:

```text
merge
↓
Combine

feature/login
↓
Source branch
```

Meaning:

Take changes from:

```text
feature/login
```

into current branch.

Example:

Current:

```text
main
```

Run:

```bash
git merge feature/login
```

Result:

```text
main ← feature/login
```

---

# 14. `git push origin <branch>`

Command:

```bash
git push origin feature/login
```

Breakdown:

```text
push
↓
Upload

origin
↓
Remote repo

feature/login
↓
Branch
```

Meaning:

Upload branch to GitHub.

---

# 15. `git push -u origin`

Command:

```bash
git push -u origin feature/login
```

Breakdown:

```text
-u
↓
upstream
```

Meaning:

Remember connection.

Next time:

Instead of:

```bash
git push origin feature/login
```

Use:

```bash
git push
```

---

# 16. `git pull origin <branch>`

Command:

```bash
git pull origin main
```

Breakdown:

```text
pull
↓
Download + Merge

origin
↓
Remote

main
↓
Branch
```

Meaning:

Get latest changes.

---

# 17. `git fetch`

Command:

```bash
git fetch
```

Breakdown:

```text
fetch
↓
Download only
```

Difference:

```text
fetch → Download

pull → Download + Merge
```

---

# 18. `git rebase`

Command:

```bash
git rebase main
```

Breakdown:

```text
rebase
↓
Move commits
```

Purpose:

Clean history.

---

# Complete Branch Workflow

```bash
git checkout main

git pull

git checkout -b feature/login

git add .

git commit -m "added login"

git push -u origin feature/login

git checkout main

git merge feature/login

git branch -d feature/login
```

---

# Interview Memory Trick

```text
branch → create
checkout/switch → move
merge → combine
push → upload
pull → download
delete → remove
rename → rename
```
