# Chapter 14 — Top Git & GitHub Interview Questions

## Story-Based Answers That Impress Interviewers

After learning Git deeply…

Munna Bhaiya started giving interviews.

He noticed something:

Interviewers rarely ask:

```text id="5d0m3s"
What is git add?
```

Instead they ask:

```text id="u2kt4x"
Real scenarios
Production problems
Workflow decisions
Conflict handling
Branching strategies
```

Munna Bhaiya realized:

> “Interviewers don't test commands.
> They test understanding.”

This chapter contains the most important Git & GitHub interview questions with impactful story-based answers.

---

# 1. What is Git?

### Interviewer Asks

> “What is Git?”

---

### Weak Answer

> Git is a version control system.

---

### Strong Story-Based Answer

> Git is a distributed version control system that helps developers track project history, collaborate safely, and manage code evolution over time.
>
> Earlier developers used to create folders like:
>
> ```text
> project-final/
> project-final-final/
> ```
>
> which created chaos in teams.
>
> Git solved this by introducing commits, branches, merging, and distributed repositories.
>
> What makes Git powerful is that every developer gets a complete copy of project history, allowing offline work, fast branching, and reliable collaboration.

---

# 2. Difference Between Git and GitHub?

### Strong Answer

> Git is the actual version control tool that runs locally on a machine.
>
> GitHub is a cloud platform that hosts Git repositories and adds collaboration features like Pull Requests, code reviews, CI/CD, and issue tracking.
>
> I usually explain it like:
>
> ```text id="zuws2g"
> Git
> =
> Engine
>
> GitHub
> =
> Collaboration Platform
> ```

---

# 3. What Happens Internally When You Run `git commit`?

### Strong Answer

> When we run `git commit`, Git takes the staged snapshot from the index and creates a commit object.
>
> Internally Git stores:
>
> ```text id="9sw2wc"
> Blob → file content
> Tree → directory structure
> Commit → metadata + pointers
> ```
>
> The commit stores:
>
> * author
> * timestamp
> * parent commit
> * snapshot reference
>
> Git is snapshot-based rather than file-difference based.

---

# 4. Explain Git Workflow

### Strong Story-Based Answer

> Git workflow starts from the working directory.
>
> The flow is:
>
> ```text id="eq4vzg"
> Working Directory
> ↓
> git add
> ↓
> Staging Area
> ↓
> git commit
> ↓
> Local Repository
> ↓
> git push
> ↓
> Remote Repository
> ```
>
> I usually think of staging area like an editor's desk where we select exactly what should become part of history.

---

# 5. What is the Difference Between Merge and Rebase?

### Strong Answer

> Both combine changes but in different ways.
>
> Merge preserves branch history and creates a merge commit.
>
> Rebase rewrites commit history by replaying commits on a new base.
>
> I usually use:
>
> * merge for preserving collaboration history
> * rebase for keeping local feature history clean
>
> I avoid rebasing public shared branches because it rewrites history.

---

# 6. Explain Cherry-Pick

### Strong Story-Based Answer

> Cherry-pick is used when we want only specific commits instead of an entire branch.
>
> For example:
>
> If a feature branch contains:
>
> ```text id="0z2jwn"
> Feature
> Bug Fix
> Experiment
> ```
>
> and production only needs the bug fix, we can cherry-pick that commit instead of merging the full branch.
>
> Internally Git copies the patch and creates a new commit.

---

# 7. What is HEAD in Git?

### Strong Answer

> HEAD is a pointer to the currently checked-out commit or branch.
>
> Normally:
>
> ```text id="ykel0w"
> HEAD → main
> ```
>
> In detached HEAD state:
>
> ```text id="uhj5ru"
> HEAD → commit hash
> ```
>
> meaning we're directly pointing to a commit instead of a branch.

---

# 8. Difference Between Fetch and Pull?

### Strong Answer

> `git fetch` only downloads remote updates.
>
> `git pull` performs:
>
> ```text id="5rsvlm"
> fetch + merge
> ```
>
> I personally prefer fetch first in production environments because it allows reviewing changes before integrating them.

---

# 9. Explain Git Conflict

### Strong Story-Based Answer

> Conflict happens when Git cannot safely decide how to combine changes automatically.
>
> Example:
>
> Two developers modify the same line differently.
>
> Git stops and asks humans to decide.
>
> Conflict does not mean code is broken.
>
> It means:
>
> ```text id="k4jzmo"
> Multiple valid possibilities exist
> ```

---

# 10. What is Staging Area?

### Strong Answer

> Staging area is an intermediate layer between working directory and commit history.
>
> It allows developers to selectively choose what becomes part of the next commit.
>
> I think of it like preparing files on an editor's table before publishing.

---

# 11. Explain Branching Strategy Used in Your Projects

### Strong Story-Based Answer

> In most projects I use Feature Branch Workflow.
>
> The flow is:
>
> ```text id="cl7wxy"
> main
> ↓
> feature branch
> ↓
> PR
> ↓
> review
> ↓
> merge
> ```
>
> For production releases we usually maintain protected branches and hotfix branches.
>
> In fast-moving projects GitHub Flow works well, while enterprise systems often use Git Flow.

---

# 12. What Happens During `git push`?

### Strong Answer

> `git push` transfers local commits to a remote repository.
>
> Before push, Git verifies:
>
> * authentication
> * remote tracking
> * branch state
>
> Internally Git sends objects that remote repository doesn't already have.

---

# 13. Difference Between Reset, Revert, and Restore?

### Strong Answer

> `reset` moves repository history.
>
> `restore` recovers file content.
>
> `revert` safely undoes changes by creating a new commit.
>
> In teams I prefer revert for already pushed commits because it preserves shared history safely.

---

# 14. Explain Git Reflog

### Strong Story-Based Answer

> Reflog is like Git's hidden safety diary.
>
> Even if commits appear deleted after reset or rebase, reflog still remembers where HEAD pointed earlier.
>
> I've used reflog multiple times to recover accidentally deleted commits.

---

# 15. What is Detached HEAD?

### Strong Answer

> Detached HEAD occurs when HEAD points directly to a commit instead of a branch.
>
> Example:
>
> ```bash id="kibph0"
> git checkout COMMIT_ID
> ```
>
> It's useful for temporary inspection, but commits created there can become orphaned unless attached to a branch.

---

# 16. How Do You Resolve Merge Conflicts?

### Strong Story-Based Answer

> My process is:
>
> ```text id="fjlwmj"
> Understand conflict
> ↓
> Identify intended logic
> ↓
> Resolve manually
> ↓
> Test
> ↓
> Commit resolution
> ```
>
> I avoid blindly accepting incoming/current changes because conflicts are usually business-logic decisions, not just syntax problems.

---

# 17. What is Fast Forward Merge?

### Strong Answer

> Fast forward merge happens when target branch has no new commits.
>
> Git simply moves branch pointer forward without creating merge commit.

---

# 18. Explain Pull Request Workflow

### Strong Story-Based Answer

> Pull Request is not just merging code.
>
> It's a collaboration and quality-control mechanism.
>
> PR workflow usually includes:
>
> ```text id="o1p2gg"
> Review
> Testing
> CI/CD checks
> Security validation
> Discussion
> Approval
> ```
>
> In my view PRs are where team-level engineering quality actually happens.

---

# 19. Why is Git Faster Than Older Systems?

### Strong Answer

> Git is optimized because:
>
> * operations happen locally
> * distributed architecture
> * snapshot-based storage
> * lightweight branching
>
> Most operations don't require server communication.

---

# 20. What is the Most Important Thing You Learned About Git?

### Strong Impact Answer

> Earlier I thought Git was just about commands.
>
> But after working deeply with Git, I realized Git is actually about managing the story of software evolution safely.
>
> Commands are only tools.
>
> The real skill is understanding collaboration, history management, recovery, and controlled delivery of code.

---

# Final Interview Philosophy from Munna Bhaiya

> “Average candidates explain commands.
> Strong candidates explain workflows.
> Exceptional candidates explain why the workflow exists.”
