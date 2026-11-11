# Branch Health Dashboard

> Score, monitor, and clean up your Git branches without leaving the IDE.

**Free & open source** — source: https://github.com/JirakJ/branch-health-dashboard (Apache-2.0); contributions welcome.

## Overview

Branch Health Dashboard gives every local and remote-tracking Git branch a health score from 0 to 100, based on its age, recent activity, how far it has fallen behind the base branch, and how many files it changes that the base branch also changed. A sortable dashboard shows the score next to ahead/behind counts, conflict risk, and a rebase-or-merge recommendation, and a cleanup action removes local branches that are already merged. It is built for teams that want to stop stale branches from silently accumulating risk.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Branch Health Dashboard"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2+ with the bundled Git plugin. The plugin scans the first Git repository of the project.

## Features

### Branch health scoring
- **Health score (0–100)** — Age (up to −40 pts), activity over the last 30 days (+10 to −10 pts), commits behind the base branch (up to −15 pts), and overlap with base-branch changes (up to −20 pts).
- **Status** — Healthy (≥75), Aging (≥50), Stale (≥25), Dead (<25).
- **Ahead/behind** — compared with `main`, `master`, or `develop` (local first, then `origin/`).
- **Conflict risk** — files changed on both sides since the merge base.
- **Rebase advice** — REBASE, MERGE, or EITHER, based on the ahead/behind counts.

### Dashboard
- **Sortable table** — health, age, activity, ahead/behind, conflict risk, and advice per branch.
- **Filter by status** — Healthy, Aging, Stale, or Dead.

### Scan and cleanup
- **Scan Branch Health** shows a summary and, when enabled, a stale-branch notification.
- **Cleanup Stale Branches** lists local branches already merged into `HEAD` and deletes them with `git branch -d` after confirmation. `main`, `master`, `develop`, and your ignored branches are never offered.

## Configuration

**Settings → Tools → Branch Health Dashboard**

| Setting | Default | Description |
|---------|---------|-------------|
| Stale branch threshold (days) | `30` | Branches with no commits for this many days are considered stale (range 1–365) |
| Enable notifications | On | Show a summary and a stale-branch warning after each scan |
| Ignored branches | `main, develop, master` | Comma-separated branch names excluded from scans and cleanup; matches local and `origin/` names |

## Tool Windows

### Branch Health
- **Location:** Bottom panel
- **Content:** Sortable table of local and remote-tracking branches with health score, age, activity, ahead/behind, conflict risk, and rebase advice, filterable by status, plus a scan button.

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Scan Branch Health | VCS menu; Branch Health tool window | Scan all branches and calculate health scores |
| Cleanup Stale Branches | VCS menu | Delete local branches already merged into `HEAD`, after confirmation |

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
