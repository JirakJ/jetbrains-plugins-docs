# Git Workflow Enforcer

> Validate Git branch names, commit messages, and merge policies before commits happen.

## Overview

Git Workflow Enforcer catches Git convention violations inside the IDE instead of in code review. It validates branch names, commit messages, and merge/push policies against a chosen workflow — keeping your Git history clean and your team consistent.

Pick a preset (Gitflow, Trunk-Based Development, GitHub Flow, or Custom) or define your own rules, then share them across the team through a versioned `.git-workflow.yaml` file. Compliance is surfaced in real time through a status bar widget, a violations tool window, and balloon notifications, and is enforced at commit time with block or warn options.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Git Workflow Enforcer"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.3+, JDK 17+, Git4Idea plugin (bundled with all JetBrains IDEs)

## Features

### Branch Naming
- Enforce Gitflow, trunk-based, GitHub Flow, or custom naming patterns
- Real-time validation with clear error messages
- Configurable regex patterns for any naming convention

### Commit Message Validation
- Conventional Commits format enforcement
- Configurable maximum subject length (default 72 characters)
- Optional JIRA / issue key requirement in commit messages
- Recognized commit types: `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `build`, `ci`, `chore`, `revert`

### Merge and Push Policies
- Block direct pushes to protected branches (default: `main`, `master`, `develop`)
- Enforce pull request workflows
- Merge direction validation (e.g. feature → develop, hotfix → main)
- Required reviewers per file path (CODEOWNERS-like rules)

### IDE Integration
- Status bar widget showing real-time compliance status
- Pre-commit validation with block or warn options
- Violations tool window grouped by type
- Balloon notifications with fix suggestions

### Team Configuration
- Shared `.git-workflow.yaml` versioned in Git
- Auto-reload when the config file changes
- Workflow presets: Gitflow, Trunk-Based Development, GitHub Flow, Custom

## Configuration

**Settings → Tools → Git Workflow Enforcer**

| Setting | Default | Description |
|---------|---------|-------------|
| Enable Git Workflow Enforcer | On | Toggle all workflow enforcement on or off |
| Workflow preset | Gitflow | Predefined workflow: Gitflow, Trunk-Based Development, GitHub Flow, or Custom |
| Enable branch name validation | On | Validate branch names against the workflow naming conventions |
| Enable commit message validation | On | Validate commit messages for format and content |
| Enable merge policy validation | On | Enforce merge direction rules defined by the workflow |
| Enforce Conventional Commits format | On | Require commit messages to follow the Conventional Commits spec |
| Require issue reference in commits | Off | Require a ticket/issue reference (e.g. JIRA-123) in each commit message |
| Max commit subject length | 72 | Maximum commit subject length (20–200) |
| Protected branches | `main,master,develop` | Comma-separated list of protected branch names |

Settings are stored per project.

## Tool Windows

### Git Workflow
- **Location:** bottom panel (secondary)
- **Content:** current workflow violations grouped by type — branch naming, commit format, and merge policy

## FAQ

**Where do shared team rules live?**
In a `.git-workflow.yaml` file at the project root, versioned in Git. The plugin auto-reloads it whenever the file changes.

**Does it block commits or just warn?**
Pre-commit validation runs as part of the IDE's commit checks and can either block a non-compliant commit or warn and let it through.

**Which JetBrains IDEs are supported?**
Any JetBrains IDE on version 2024.3 or newer that bundles the Git4Idea plugin (IntelliJ IDEA, GoLand, PyCharm, WebStorm, and the rest of the family).

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
