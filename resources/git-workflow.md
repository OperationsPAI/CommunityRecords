# Git and Open-Source Workflow Guide

This guide covers the essential Git concepts and the standard open-source contribution workflow used in this repository.

---

## Table of Contents

- [Core Concepts](#core-concepts)
- [Essential Git Commands](#essential-git-commands)
- [The Fork-and-PR Workflow](#the-fork-and-pr-workflow)
- [Branching Strategy](#branching-strategy)
- [Writing Good Commit Messages](#writing-good-commit-messages)
- [Handling Merge Conflicts](#handling-merge-conflicts)
- [Common Mistakes and How to Fix Them](#common-mistakes-and-how-to-fix-them)

---

## Core Concepts

### Repository (repo)
A repository is a directory that Git tracks. It contains all your files and the complete history of every change ever made to them.

### Commit
A commit is a saved snapshot of your changes. Every commit has a unique ID (SHA), an author, a timestamp, and a message describing the change.

### Branch
A branch is an independent line of development. The default branch is usually named `main`. You create a new branch whenever you want to work on something without affecting the main codebase.

### Remote
A remote is a version of the repository hosted on a server (such as GitHub). `origin` refers to your fork. `upstream` refers to the original repository you forked from.

### Fork
A fork is your personal copy of someone else's repository on GitHub. You have full write access to your fork, but not to the original.

### Pull Request (PR)
A pull request is a proposal to merge changes from your branch into another branch (usually `main` in the upstream repo). It is the standard way to contribute to open-source projects.

---

## Essential Git Commands

### Setup (run once)

```bash
# Set your name and email (used in commit history)
git config --global user.name "Your Name"
git config --global user.email "you@example.com"
```

### Starting out

```bash
# Clone a repository to your local machine
git clone <url>

# Check the status of your working directory
git status

# See the full commit history
git log --oneline
```

### Branching

```bash
# List all local branches
git branch

# Create a new branch
git branch <branch-name>

# Switch to a branch
git checkout <branch-name>

# Create and switch in one step (most common)
git checkout -b <branch-name>

# Delete a branch (after it is merged)
git branch -d <branch-name>
```

### Making changes

```bash
# See what changed in your files
git diff

# Stage specific files
git add <file>

# Stage all changed files
git add .

# Commit staged changes
git commit -m "your commit message"

# Stage and commit tracked files in one step
git commit -am "your commit message"
```

### Syncing with remotes

```bash
# Download changes from a remote (does not merge)
git fetch <remote>

# Download and merge changes (fetch + merge)
git pull <remote> <branch>

# Push your branch to a remote
git push <remote> <branch>
```

### Undoing things

```bash
# Discard changes in a file (before staging)
git checkout -- <file>

# Unstage a file (keep the changes in the file)
git reset HEAD <file>

# Undo the last commit but keep the changes staged
git reset --soft HEAD~1

# Amend the last commit message (before pushing)
git commit --amend -m "corrected message"
```

---

## The Fork-and-PR Workflow

This is the standard workflow for contributing to open-source projects.

```
Upstream repo (OperationsPAI/CommunityRecords)
        |
        | fork
        v
Your fork (your-username/CommunityRecords)  <-- you own this
        |
        | clone
        v
Your local machine
        |
        | create branch, make changes, commit
        v
Your fork (push)
        |
        | open Pull Request
        v
Upstream repo (merge)
```

Step-by-step:

1. Fork the upstream repo on GitHub.
2. Clone your fork to your local machine.
3. Add the upstream remote: `git remote add upstream <upstream-url>`
4. Create a branch: `git checkout -b <branch-name>`
5. Make changes and commit them.
6. Push the branch to your fork: `git push origin <branch-name>`
7. Open a Pull Request on GitHub from your branch to `upstream/main`.
8. Address any review comments by pushing more commits to the same branch.
9. Once approved, the maintainer merges your PR.

---

## Branching Strategy

Always keep `main` clean and stable. Work happens on feature branches.

```
main ──────────────────────────────────────────>
        \                       /
         feat/alice-init ──────
                  \                   /
                   docs/alice-log-0115
```

Rules:
- Never commit directly to `main`.
- One branch per logical change (one log entry, one profile, one fix).
- Delete branches after they are merged to keep things tidy.

---

## Writing Good Commit Messages

A good commit message tells the reader what changed and why.

Format:
```
<type>(<scope>): <short summary in present tense>

[optional body: more detail if needed]
```

Rules:
- Use the imperative mood: "add log" not "added log"
- Keep the summary under 72 characters
- Reference an issue if relevant: `fix(alice): correct typo, closes #12`

Examples of good commit messages:
```
docs(alice): add daily log 2024-01-15
feat(bob): initialize member profile
fix: correct broken link in resources/git-workflow.md
chore: add .gitkeep to empty logs directory
```

Examples of bad commit messages:
```
update
fixed stuff
WIP
asdfgh
```

---

## Handling Merge Conflicts

A merge conflict happens when two branches change the same lines of a file. Git cannot decide which version to keep, so it asks you to resolve it manually.

### When a conflict occurs

```bash
git merge upstream/main
# CONFLICT (content): Merge conflict in some-file.md
# Automatic merge failed; fix conflicts and then commit the result.
```

### What a conflict looks like in a file

```
<<<<<<< HEAD
Your version of the line
=======
The upstream version of the line
>>>>>>> upstream/main
```

### How to resolve it

1. Open the conflicting file in your editor.
2. Decide which version to keep (or write a combined version).
3. Remove the conflict markers (`<<<<<<<`, `=======`, `>>>>>>>`).
4. Stage the resolved file: `git add <file>`
5. Complete the merge: `git commit`

---

## Common Mistakes and How to Fix Them

### Committed to main by accident

```bash
# Move the commit to a new branch instead
git branch my-new-branch       # create branch pointing to current commit
git reset --hard HEAD~1        # move main back one commit
git checkout my-new-branch     # switch to the new branch
```

### Pushed something wrong to your fork

```bash
# Revert the bad commit and push the revert
git revert <commit-sha>
git push origin <branch>
```

### Forgot to pull before starting work (now have diverged history)

```bash
git fetch upstream
git rebase upstream/main
# Resolve any conflicts, then continue:
git rebase --continue
```

### Accidentally deleted a file

```bash
git checkout HEAD -- <file>
```

---

## Further Reading

- [Pro Git Book](https://git-scm.com/book/en/v2) (free online)
- [GitHub Docs: Pull Requests](https://docs.github.com/en/pull-requests)
- [Conventional Commits](https://www.conventionalcommits.org/)
