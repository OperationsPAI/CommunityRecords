# CommunityRecords

CommunityRecords is a learning journal community designed for beginners. It serves two purposes:

- Record daily learning: insights, concepts learned, errors encountered and how they were resolved.
- Practice open-source collaboration: Git operations, Pull Request workflow, Issue management, and code review.

---

## Repository Structure

```
CommunityRecords/
├── README.md                  # Project overview and quick start guide
├── CONTRIBUTING.md            # Contribution guide (how to submit your learning records)
├── members/                   # Learning records for all community members
│   ├── README.md              # How to join the community
│   └── <your-username>/       # Your personal learning space
│       ├── profile.md         # Personal introduction
│       └── logs/              # Daily learning logs
│           └── YYYY-MM-DD.md
├── templates/                 # Reusable templates
│   ├── daily-log.md           # Daily learning log template
│   ├── weekly-summary.md      # Weekly summary template
│   └── member-profile.md      # Member profile template
└── resources/                 # Shared learning resources
    └── git-workflow.md        # Git and open-source workflow guide
```

---

## Quick Start

### Step 1: Learn the open-source workflow

If this is your first time contributing to an open-source project, read these first:
- [Contributing Guide (CONTRIBUTING.md)](./CONTRIBUTING.md)
- [Git Workflow Guide (resources/git-workflow.md)](./resources/git-workflow.md)

### Step 2: Create your personal space

1. Fork this repository to your GitHub account.
2. Clone your fork locally:
   ```bash
   git clone https://github.com/<your-username>/CommunityRecords.git
   cd CommunityRecords
   ```
3. Create a folder under `members/` named after your GitHub username:
   ```bash
   mkdir -p members/<your-username>/logs
   ```
4. Copy the profile template and fill it in:
   ```bash
   cp templates/member-profile.md members/<your-username>/profile.md
   ```
5. Commit your changes and open a Pull Request.

### Step 3: Record your daily learning

1. Copy the daily log template:
   ```bash
   cp templates/daily-log.md members/<your-username>/logs/$(date +%Y-%m-%d).md
   ```
2. Open the file in your editor and fill in today's learning content.
3. Commit and push:
   ```bash
   git add .
   git commit -m "docs(<your-username>): add daily log YYYY-MM-DD"
   git push origin <your-branch>
   ```
4. Open a Pull Request.

---

## Commit Message Convention

Follow this format:

```
<type>(<scope>): <short description>
```

| Type    | When to use                        | Example                                      |
|---------|------------------------------------|----------------------------------------------|
| `docs`  | Add or update a log or document    | `docs(alice): add daily log 2024-01-15`      |
| `feat`  | Add a new feature or template      | `feat: add weekly summary template`          |
| `fix`   | Correct a mistake in existing content | `fix(alice): correct typo in 2024-01-15 log` |
| `chore` | Maintenance tasks                  | `chore: update README`                       |

---

## Community Members

See [members/README.md](./members/README.md) to learn how to join.

---

## Contributing

All contributions are welcome, whether it is fixing a typo, improving a template, or enhancing the documentation.
Please read [CONTRIBUTING.md](./CONTRIBUTING.md) for details.
