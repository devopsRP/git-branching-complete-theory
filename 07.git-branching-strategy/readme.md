## **Git Branching Strategy** 

Think of this as a **real DevOps project story**.

---

# What is Git Branching Strategy?

A **Git branching strategy is a defined way teams organize branches to develop, test, review, release, and maintain code safely.**

Without strategy:

```text
Developer 1 → Push
Developer 2 → Push
Developer 3 → Push

Production → Broken ❌
```

With strategy:

```text
Feature
 ↓
Review
 ↓
Testing
 ↓
Release
 ↓
Production
```

Everything becomes controlled.

---

# Story — Your IES Project (Insurance System)

Suppose your team develops:

```text
IES (Integrated Eligibility System)
```

Team:

```text
Backend → 4 Developers
Frontend → 3 Developers
DevOps → Ravi
QA → 2 Testers
```

Application:

```text
Production Users:
SNAP
Medicaid
Medicare
CCAP
```

Since production cannot break—

Team follows branching strategy.

---

# Strategy 1 — Main Branch

This branch always contains:

```text
Stable
Tested
Production-ready code
```

Example:

```text
main
```

Rules:

✅ No direct push
✅ PR mandatory
✅ Review required

Think:

```text
main = Gold Version
```

---

# Strategy 2 — Develop Branch

This is the integration branch.

Example:

```text
main
│
└── develop
```

Developers merge completed work here.

Purpose:

```text
Collect all completed features
```

Story:

Developer A finishes SNAP.

Developer B finishes Medicaid.

Both merge into:

```text
develop
```

---

# Strategy 3 — Feature Branch

Every new work gets separate branch.

Example:

```text
develop
│
├── feature/snap
├── feature/payment
└── feature/ui
```

Workflow:

```text
Develop
 ↓
Feature Branch
 ↓
Commit
 ↓
PR
 ↓
Merge
```

---

## Real Example

Business says:

> Add Child Care Plan

Developer creates:

```bash
git checkout develop

git pull

git checkout -b feature/ccap
```

Now:

```text
develop
│
└── feature/ccap
```

Works independently.

---

After completion:

```bash
git push origin feature/ccap
```

Create PR.

Merge:

```text
develop
```

---

# Strategy 4 — Release Branch

Develop branch is ready.

Need deployment.

Create:

```text
release/v1.0
```

Structure:

```text
main
│
develop
│
release/v1
```

Purpose:

* Final testing
* Version tagging
* Small fixes

---

Story:

QA finds:

```text
Wrong eligibility age
```

Fix directly:

```text
release/v1
```

---

Deploy.

Merge:

```text
main
```

---

# Strategy 5 — Hotfix Branch

Production issue.

Users cannot apply.

Create:

```text
hotfix/prod-fix
```

Flow:

```text
main
│
└── hotfix/payment
```

Fix.

Deploy immediately.

Merge:

```text
main
develop
```

---

# Complete Enterprise Flow

```text
main
│
├── develop
│
├── feature/*
│
├── release/*
│
└── hotfix/*
```

Flow:

```text
Feature
 ↓
Develop
 ↓
Release
 ↓
Main
```

---

# Real DevOps Branch Strategy

Suppose Terraform repo.

Structure:

```text
infra-repo

main
develop

feature/vnet

feature/aks

release/prod
```

Flow:

---

Infrastructure Engineer:

```bash
git checkout develop

git checkout -b feature/landing-zone
```

Changes:

```tf
resource_group
vnet
aks
```

Commit:

```bash
git add .

git commit -m "added landing zone"
```

Push:

```bash
git push origin feature/landing-zone
```

PR.

Review.

Merge.

---

# Best Practices (Most Important)

---

## 1. Never Commit Directly to Main

Wrong:

```bash
git push origin main
```

Correct:

```text
Feature
 ↓
PR
 ↓
Review
 ↓
Main
```

---

## 2. Branch Names Must Be Standard

Good:

```text
feature/login

feature/terraform

bugfix/pipeline

release/v1

hotfix/prod
```

Bad:

```text
newbranch

testing123
```

---

## 3. Pull Before Work

Always:

```bash
git pull origin develop
```

Avoid stale code.

---

## 4. Small Commits

Bad:

```bash
git commit -m "all changes"
```

Good:

```bash
git commit -m "created terraform vnet module"
```

---

## 5. Use Pull Requests

Flow:

```text
Push
 ↓
PR
 ↓
Review
 ↓
Approve
 ↓
Merge
```

---

## 6. Protect Main Branch

GitHub settings:

```text
Require PR
Require Review
Block Force Push
Require Status Checks
```

---

## 7. Delete Feature Branch After Merge

Bad:

```text
feature/login
feature/login-old
feature/login-final
```

Good:

```text
Delete merged branch
```

---

## 8. Automate with CI/CD

Example:

```text
PR
 ↓
GitHub Actions
 ↓
Build
 ↓
Test
 ↓
Terraform Validate
 ↓
Approve
 ↓
Merge
```

---

# When Teams Use Which Strategy

### Small Team

```text
main
feature/*
```

---

### Medium Team

```text
main
develop
feature/*
```

---

### Enterprise

```text
main
develop
feature/*
release/*
hotfix/*
```

---

# Interview Answer

> “Git branching strategy defines how teams organize development and releases. Typically, developers create feature branches from develop, merge through pull requests, create release branches for deployment preparation, and maintain production stability through main and hotfix branches. This helps improve collaboration, reduce conflicts, and ensure controlled deployments.”

---

One line to remember:

```text
Branching Strategy = Rules for safe software delivery
```
