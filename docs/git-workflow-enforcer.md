# Git Workflow Enforcer

> Enforce Git branching conventions and commit standards in your IDE.

## Overview

Git Workflow Enforcer ensures your team follows consistent Git practices by enforcing branch naming conventions, commit message formats, and workflow rules (GitFlow, GitHub Flow, trunk-based) directly in the IDE — before code reaches the remote repository.

## Installation

1. Go to **Settings → Plugins → Marketplace**
2. Search for **"Git Workflow Enforcer"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.3+, Java 17+, Git

## Features

### Free Tier
- Branch naming convention enforcement (regex patterns)
- Conventional Commits validation (type, scope, description)
- 3 built-in workflow presets (GitFlow, GitHub Flow, Trunk-Based)
- Pre-commit hook for commit message validation
- Basic violation notifications

### Pro Tier
- Custom workflow rule definitions
- Branch lifecycle policies (auto-delete after merge)
- Protected branch warnings
- Commit message templates with auto-fill
- PR title/description validation
- Multi-repo workflow consistency
- Team-shared rules via `.git-workflow.yaml`
- Workflow compliance dashboard
- CI/CD integration (enforce rules in pipelines)

## Configuration

### Settings Location
**Settings → Tools → Git Workflow Enforcer**

| Setting | Default | Description |
|---------|---------|-------------|
| Workflow preset | GitHub Flow | Active workflow template |
| Branch pattern | `(feature\|bugfix\|hotfix)/.*` | Allowed branch name regex |
| Commit format | Conventional | Commit message format (Conventional, Angular, Custom) |
| Block invalid commits | `false` | Prevent commits with invalid messages |
| Team rules file | `.git-workflow.yaml` | Shared rules file path |

## Inspections

| Inspection | Severity | Description |
|-----------|----------|-------------|
| Invalid Branch Name | WARNING | Branch doesn't match naming convention |
| Invalid Commit Message | WARNING | Commit message violates format rules |
| Protected Branch Push | ERROR | Direct push to protected branch |

## Pre-Commit Checks

The plugin validates before each commit:
1. ✅ Commit message format (type, scope, description)
2. ✅ Branch naming convention
3. ✅ Ticket reference (optional, e.g., JIRA-123)
4. ✅ Message length limits (subject: 50 chars, body: 72 chars/line)

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
