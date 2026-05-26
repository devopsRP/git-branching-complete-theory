# The Story of `git config`, Login & Authentication

## Understanding Identity, Configuration, Access Control, and Authentication in Git — From Zero to Expert

After understanding repositories and workflow, Munna Bhaiya thought:

> “Now I understand files, repositories, commits, and push…
> But one thing still confuses me.”

He opened terminal and asked:

> “Who am I inside Git?”

> “How does Git know my name?”

> “How does GitHub know I am allowed to push?”

> “What exactly is `git config`?”


---

# Scene 1 — The Great Confusion

Munna Bhaiya thought these are same:

```text
Git Login
Git Authentication
Git Config
GitHub Account
Git Identity
```

But they are NOT the same.

Git explained:

There are actually **3 separate concepts**.

```text
1. Configuration
2. Identity
3. Authentication
```

---

# Scene 2 — What is `git config`?

Git says:

> "`git config` means configuring Git's behavior."

Think:

Git is a new employee.

Before working, you tell it:

```text
Your name
Your email
Editor
Default branch
Authentication settings
Remote settings
Preferences
```

Those instructions are called:

```text
Git Configuration
```

Command:

```bash
git config
```

---

# Scene 3 — Where Does Git Store Configuration?

Munna Bhaiya asks:

> “If I configure Git… where does it save?”

Git says:

Three levels exist.

```text
System
Global
Local
```

---

# Level 1 — System Config

Applies to entire machine.

Visualization:

```text
Computer
└── All Users
```

Command:

```bash
git config --system
```

Rarely used.

Example:

```bash
git config --system core.editor "vim"
```

---

# Level 2 — Global Config (Most Common)

Applies to current user.

Visualization:

```text
Munna Bhaiya
├── Repo A
├── Repo B
└── Repo C
```

Command:

```bash
git config --global
```

Stored:

Linux/Mac:

```text
~/.gitconfig
```

Windows:

```text
C:\Users\Username\.gitconfig
```

Example:

```bash
git config --global user.name "Munna Bhaiya"
```

Now every repo uses it.

---

# Level 3 — Local Config

Only current repository.

Visualization:

```text
my-project
└── .git/config
```

Command:

```bash
git config
```

Example:

```bash
git config user.name "Munna Bhaiya Dev"
```

Only this repo changes.

---

# Priority Rule

Git checks:

```text
Local
↓
Global
↓
System
```

Closest wins.

Example:

```text
Global → Munna Bhaiya
Local → Munna Senior
```

Git uses:

```text
Munna Senior
```

---

# Scene 4 — Git Identity (Who Created This Commit?)

Munna Bhaiya writes code.

Runs:

```bash
git commit
```

Git asks:

> “Who created this?”

Identity requires:

```text
Name
Email
```

Configure:

```bash
git config --global user.name "Munna Bhaiya"

git config --global user.email "munna@example.com"
```

Verify:

```bash
git config --global --list
```

Output:

```text
user.name=Munna Bhaiya
user.email=munna@example.com
```

---

# Scene 5 — What Identity Actually Does

Munna Bhaiya commits:

```bash
git commit -m "add login"
```

Commit becomes:

```text
Commit:
abc123

Author:
Munna Bhaiya
munna@example.com
```

Identity ONLY labels history.

It does NOT log into GitHub.

---

# Scene 6 — The Biggest Beginner Mistake

Munna Bhaiya thought:

```text
git config user.name
=
GitHub login
```

Wrong.

Git explains:

```text
Identity ≠ Authentication
```

Identity:

```text
Who made commit
```

Authentication:

```text
Who can push
```

---

# Scene 7 — What is Authentication?

Munna Bhaiya runs:

```bash
git push
```

GitHub responds:

> “You want to upload code?”

> “Prove who you are.”

That proof is:

```text
Authentication
```

Purpose:

```text
Allow Push
Allow Pull
Access Private Repositories
```

---

# Scene 8 — Authentication Method 1 (HTTPS)

Remote:

```text
https://github.com/user/project.git
```

Push:

```bash
git push
```

GitHub asks:

```text
Username
Password
```

But modern GitHub removed passwords.

Now use:

```text
Personal Access Token (PAT)
```

---

# Scene 9 — What is Personal Access Token?

Think:

Instead of giving house key—

you give temporary access card.

PAT:

```text
Long Secret String
```

Example:

```text
ghp_xxxxxxxxx
```

Purpose:

```text
Authenticate Git
```

---

# Create Token

GitHub:

```text
Profile
↓
Settings
↓
Developer Settings
↓
Personal Access Tokens
↓
Generate New Token
```

Permissions:

```text
repo
workflow
```

Generate.

Copy once.

---

# Using Token

Push:

```bash
git push
```

Enter:

```text
Username:
GitHub username
```

Password:

```text
PASTE TOKEN
```

Done.

---

# Save Login

Windows:

```bash
git config --global credential.helper manager
```

Mac:

```bash
git config --global credential.helper osxkeychain
```

Linux:

```bash
git config --global credential.helper store
```

Now login persists.

---

# Scene 10 — Authentication Method 2 (SSH) — Professional Way

Munna Bhaiya says:

> “Typing token repeatedly is annoying.”

Git introduces:

```text
SSH
```

SSH means:

```text
Trust through cryptographic keys
```

---

# Generate SSH Keys

Command:

```bash
ssh-keygen -t ed25519 -C "munna@example.com"
```

Created:

```text
~/.ssh/

id_ed25519
id_ed25519.pub
```

---

Files mean:

Private:

```text
id_ed25519
```

Never share.

Public:

```text
id_ed25519.pub
```

Share safely.

---

# Scene 11 — Add SSH to GitHub

Display:

```bash
cat ~/.ssh/id_ed25519.pub
```

Copy.

GitHub:

```text
Settings
↓
SSH and GPG Keys
↓
New SSH Key
```

Paste.

Save.

---

# Scene 12 — Start SSH Agent

Mac/Linux:

```bash
eval "$(ssh-agent -s)"
```

Windows:

```bash
Start-Service ssh-agent
```

Add:

```bash
ssh-add ~/.ssh/id_ed25519
```

---

# Scene 13 — Test Authentication

Run:

```bash
ssh -T git@github.com
```

Success:

```text
Hi username!
Successfully authenticated.
```

---

# Scene 14 — Connect Repository Using SSH

Current:

```bash
git remote -v
```

Output:

```text
https://github.com/user/project.git
```

Switch:

```bash
git remote set-url origin git@github.com:user/project.git
```

Push:

```bash
git push
```

No login.

---

# Scene 15 — Useful `git config` Commands

View all:

```bash
git config --list
```

View global:

```bash
git config --global --list
```

View local:

```bash
git config --local --list
```

Get one value:

```bash
git config user.name
```

Remove:

```bash
git config --unset user.name
```

Edit manually:

```bash
git config --global --edit
```

---

# Scene 16 — Complete Mental Model

```text
Git Config
↓
Configure behavior


Git Identity
↓
Name + Email


Authentication
↓
Token / SSH


Authorization
↓
Permission to push
```

Workflow:

```text
Configure Git
↓
Create Commit
↓
Authenticate
↓
Push
```

---

# Scene 17 — First-Time Developer Setup

Install Git:

```bash
git --version
```

Set identity:

```bash
git config --global user.name "Munna Bhaiya"

git config --global user.email "munna@example.com"
```

Generate SSH:

```bash
ssh-keygen -t ed25519
```

Add remote:

```bash
git remote add origin URL
```

Push:

```bash
git push
```

Done.

---

# Final Lesson from Munna Bhaiya

> “`git config` teaches Git who I am.
> Authentication proves I am allowed.
> And push sends my history to the world.”
