# Git Workflow Enforcer

> Validate Git branch names, commit messages and protected branches before commits happen.

**Free & open source** — source: https://github.com/JirakJ/git-workflow-enforcer (Apache-2.0); contributions welcome.

## Overview

Git Workflow Enforcer catches Git convention violations inside the IDE instead of in code review. It validates branch names, commit messages and commits on protected branches against a chosen workflow — keeping your Git history clean and your team consistent.

Pick a preset (Gitflow, Trunk-Based Development, GitHub Flow, or Custom), then override the rules for the whole team in a versioned `.git-workflow.yaml` file. Compliance is shown in a status bar widget and a violations tool window, and checked at commit time with a **Commit Anyway / Cancel** prompt.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Git Workflow Enforcer"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2+ with the bundled Git plugin.

## Features

### Branch naming
- Gitflow, trunk-based, GitHub Flow, or custom regex patterns

### Protected branches
- The pre-commit check flags committing directly on a protected branch such as `main`
- Blocked (error) or only warned, depending on `block_direct_push` / `require_pr`
- Protected branches can be exact names or regexes (for example `release/.*`)

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

| Preset | Branch patterns | Conventional Commits | Protected branches |
|--------|-----------------|----------------------|--------------------|
| Gitflow | `feature/.+`, `bugfix/.+`, `release/.+`, `hotfix/.+`, plus `main`, `master`, `develop` | Required | `main`, `master`, `develop` |
| Trunk-Based Development | `[a-z0-9-]+/[a-z0-9-]+`, plus `main` | Not required | `main` |
| GitHub Flow | `[a-z0-9]+(-[a-z0-9]+)*`, plus `main` | Not required | `main` |
| Custom | none until defined in `.git-workflow.yaml` | Not required | `main`, `master` unless defined in `.git-workflow.yaml` |

Every preset blocks direct commits on its protected branches.

## Configuration

**Settings → Tools → Git Workflow Enforcer** (per project)

| Setting | Default | Description |
|---------|---------|-------------|
| Enable Git Workflow Enforcer | On | Toggle all workflow enforcement on or off |
| Workflow preset | Gitflow | Gitflow, Trunk-Based Development, GitHub Flow, or Custom |
| Enable branch name validation | On | Validate branch names against the workflow naming conventions |
| Enable commit message validation | On | Validate commit messages for format and content |

Each toggle switches only its own check. Commit message rules (Conventional Commits, issue reference, subject length), branch patterns and the protected-branch policy come from the selected preset and can be overridden in `.git-workflow.yaml`. The protected-branch check runs whenever the plugin is enabled; turn it off in `.git-workflow.yaml` by setting both `block_direct_push` and `require_pr` to `false`.

### Team rules file

Place `.git-workflow.yaml` in the project root:

```yaml
preset: gitflow
branches:
  - pattern: "feature/.+"
    description: Feature branches
commits:
  conventional_commits: true
  max_subject_length: 72
  require_issue_ref: true
  issue_ref_pattern: "[A-Z]+-\\d+"
  allowed_types: [feat, fix, docs, chore]
  format_pattern: ""
merge:
  protected_branches: [main, develop, "release/.*"]
  block_direct_push: true   # commit on a protected branch = error
  require_pr: true          # with block_direct_push: false = warning only
```

| `merge:` key | Default | Effect |
|--------------|---------|--------|
| `protected_branches` | `[main, master]` | Branch names or regexes treated as protected |
| `block_direct_push` | `true` | Committing directly on a protected branch is reported as an error |
| `require_pr` | `true` | When blocking is off, committing on a protected branch is reported as a warning |

An `allowed_base` key on a branch rule is accepted for compatibility but not enforced.

## Tool Windows

### Git Workflow
- **Location:** Bottom panel (secondary)
- **Content:** Current violations for the active branch, grouped by type, with fix suggestions and a **Refresh** button

## FAQ

**Where do shared team rules live?**
In a `.git-workflow.yaml` file at the project root, versioned in Git. It is read on every check, so edits apply immediately.

**Does it block commits or just warn?**
When a commit has violations, the IDE shows them with **Commit Anyway** and **Cancel** — you decide whether to proceed. With errors (for example a commit directly on a protected branch with `block_direct_push: true`) the default button is **Cancel**.

**Does this replace branch protection on the Git server?**
No. The protected-branch check runs in the IDE at commit time; keep server-side branch protection for enforcement.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
