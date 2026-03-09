# Contributing Guide

Thank you for participating in CommunityRecords. This guide walks you through the standard open-source collaboration workflow for submitting your learning records.

---

## Table of Contents

- [Before You Start](#before-you-start)
- [Fork and Clone the Repository](#fork-and-clone-the-repository)
- [Create a Branch](#create-a-branch)
- [Make Your Changes](#make-your-changes)
- [Open a Pull Request](#open-a-pull-request)
- [Code Review and Merge](#code-review-and-merge)
- [Stay in Sync](#stay-in-sync)
- [Questions and Feedback](#questions-and-feedback)

---

## Before You Start

Make sure you have:
- A [GitHub](https://github.com) account
- [Git](https://git-scm.com/downloads) installed on your machine
- Read the [Git Workflow Guide](./resources/git-workflow.md) (strongly recommended for newcomers)

---

## Fork and Clone the Repository

### 1. Fork the repository

Click the **Fork** button in the top-right corner of this repository page to copy it to your GitHub account.

### 2. Clone your fork locally

```bash
# Replace <your-username> with your GitHub username
git clone https://github.com/<your-username>/CommunityRecords.git
cd CommunityRecords
```

### 3. Add the upstream remote

```bash
git remote add upstream https://github.com/OperationsPAI/CommunityRecords.git

# Verify the remotes
git remote -v
# Expected output:
# origin    https://github.com/<your-username>/CommunityRecords.git (fetch)
# origin    https://github.com/<your-username>/CommunityRecords.git (push)
# upstream  https://github.com/OperationsPAI/CommunityRecords.git (fetch)
# upstream  https://github.com/OperationsPAI/CommunityRecords.git (push)
```

---

## Create a Branch

Never work directly on the `main` branch. Every change should be made on a dedicated branch.

```bash
# First, update your local main branch
git checkout main
git pull upstream main

# Create and switch to a new branch
# Naming format: <type>/<username>-<short-description>
git checkout -b docs/<your-username>-daily-log-2024-01-15
```

Branch naming conventions:

| Type | Format | Example |
|------|--------|---------|
| Add a log | `docs/<username>-log-YYYY-MM-DD` | `docs/alice-log-2024-01-15` |
| Initialize profile | `feat/<username>-init` | `feat/alice-init` |
| Fix content | `fix/<username>-<description>` | `fix/alice-typo` |
| Update a template | `feat/update-<template-name>` | `feat/update-daily-template` |

---

## Make Your Changes

### First time: create your personal space

```bash
# Create your directory
mkdir -p members/<your-username>/logs

# Copy the profile template
cp templates/member-profile.md members/<your-username>/profile.md

# Open profile.md in your editor and fill in your information
```

### Add a daily learning log

```bash
# Copy the daily log template (replace the date with today's date)
cp templates/daily-log.md members/<your-username>/logs/2024-01-15.md

# Open the file and fill in today's learning content
```

### Stage and commit

```bash
# Check which files have changed
git status

# Review the specific changes
git diff

# Stage your changes
git add members/<your-username>/

# Commit with a meaningful message
git commit -m "docs(<your-username>): add daily log 2024-01-15"
```

Commit message format:

```
<type>(<scope>): <short description>

[optional] longer description
```

| Type | Meaning |
|------|---------|
| `docs` | Documentation or log changes |
| `feat` | New feature or new content |
| `fix` | Correct a mistake |
| `chore` | Maintenance tasks |

Examples:
- `docs(alice): add daily log 2024-01-15`
- `feat(bob): initialize member profile`
- `fix(carol): correct error description in 2024-01-10 log`

### Push to your fork

```bash
git push origin docs/<your-username>-daily-log-2024-01-15
```

---

## Open a Pull Request

1. Go to your fork on GitHub (`https://github.com/<your-username>/CommunityRecords`).
2. GitHub will usually show a banner prompting you to compare and open a pull request. Click **Compare & pull request**.
3. Alternatively, go to **Pull requests** and click **New pull request**.
4. Verify the targets:
   - **base repository**: `OperationsPAI/CommunityRecords`, **base**: `main`
   - **head repository**: `<your-username>/CommunityRecords`, **compare**: your branch
5. Fill in the PR title and description using the provided template.
6. Click **Create pull request**.

---

## Code Review and Merge

After opening a PR:
- Maintainers or other members may leave review comments.
- If changes are requested, commit to the same branch and the PR will update automatically.
- Once the PR is approved, a maintainer will merge it into `main`.

---

## Stay in Sync

Regularly sync upstream changes into your fork:

```bash
# Fetch upstream changes
git fetch upstream

# Switch to main
git checkout main

# Merge upstream changes
git merge upstream/main

# Push to your fork
git push origin main
```

---

## Questions and Feedback

- Have a question or found a problem? [Open an Issue](https://github.com/OperationsPAI/CommunityRecords/issues/new).
- Have a suggestion? Issues and PRs are both welcome.

---

Note: Your first PR may run into unexpected issues. That is completely normal. Post your question in an Issue and the community will help you.

