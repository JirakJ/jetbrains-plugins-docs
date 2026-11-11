# Git Workflow Enforcer

> Validate Git branch names and commit messages before commits happen.

**Free & open source** — source: https://github.com/JirakJ/git-workflow-enforcer (Apache-2.0); contributions welcome.

## Overview

Git Workflow Enforcer catches Git convention violations inside the IDE instead of in code review. It validates branch names and commit messages against a chosen workflow — keeping your Git history clean and your team consistent.

Pick a preset (Gitflow, Trunk-Based Development, GitHub Flow, or Custom), then override the rules for the whole team in a versioned `.git-workflow.yaml` file. Compliance is shown in a status bar widget and a violations tool window, and checked at commit time with a **Commit Anyway / Cancel** prompt.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Git Workflow Enforcer"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2+ with the bundled Git plugin.

## Features

### Branch naming
- Gitflow, trunk-based, GitHub Flow, or custom regex patterns
- Base-branch check (for example, `feature/*` must start from `develop`)

### Commit message validation
- Conventional Commits format with 11 allowed types: `feat`, `fix`, `docs`, `style`, `refactor`, `perf`, `test`, `build`, `ci`, `chore`, `revert`
- Maximum subject length (default 72 characters)
- Optional JIRA/issue key requirement

### IDE integration
- Status bar widget with the current branch's compliance status
- Pre-commit check with **Commit Anyway** / **Cancel**
- Violations tool window grouped by type, with fix suggestions

### Team configuration
- Shared `.git-workflow.yaml` versioned in Git, read on every check
- Workflow presets: Gitflow, Trunk-Based Development, GitHub Flow, Custom

### Preset defaults

| Preset | Branch patterns | Conventional Commits |
|--------|-----------------|----------------------|
| Gitflow | `feature/.+`, `bugfix/.+`, `release/.+` (from `develop`), `hotfix/.+` (from `main`/`master`), plus `main`, `master`, `develop` | Required |
| Trunk-Based Development | `[a-z0-9-]+/[a-z0-9-]+` (from `main`), plus `main` | Not required |
| GitHub Flow | `[a-z0-9]+(-[a-z0-9]+)*` (from `main`), plus `main` | Not required |
| Custom | none until defined in `.git-workflow.yaml` | Not required |

## Configuration

**Settings → Tools → Git Workflow Enforcer** (per project)

| Setting | Default | Description |
|---------|---------|-------------|
| Enable Git Workflow Enforcer | On | Toggle all workflow enforcement on or off |
| Workflow preset | Gitflow | Gitflow, Trunk-Based Development, GitHub Flow, or Custom |
| Enable branch name validation | On | Validate branch names against the workflow naming conventions |
| Enable commit message validation | On | Validate commit messages for format and content |

Commit message rules (Conventional Commits, issue reference, subject length) and branch patterns come from the selected preset and can be overridden in `.git-workflow.yaml`.

### Team rules file

Place `.git-workflow.yaml` in the project root:

```yaml
preset: gitflow
branches:
  - pattern: "feature/.+"
    allowed_base: [develop]
    description: Feature branches from develop
commits:
  conventional_commits: true
  max_subject_length: 72
  require_issue_ref: true
  issue_ref_pattern: "[A-Z]+-\\d+"
  allowed_types: [feat, fix, docs, chore]
  format_pattern: ""
```

## Tool Windows

### Git Workflow
- **Location:** Bottom panel (secondary)
- **Content:** Current violations for the active branch, grouped by type, with fix suggestions and a **Refresh** button

## FAQ

**Where do shared team rules live?**
In a `.git-workflow.yaml` file at the project root, versioned in Git. It is read on every check, so edits apply immediately.

**Does it block commits or just warn?**
When a commit has violations, the IDE shows them with **Commit Anyway** and **Cancel** — you decide whether to proceed.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
