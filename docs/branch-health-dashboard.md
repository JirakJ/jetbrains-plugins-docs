# Branch Health Dashboard

> Score, monitor, and clean up your Git branches without leaving the IDE.

## Overview

Branch Health Dashboard gives every Git branch a health score from 0 to 100 based on age, activity, how far it has fallen behind, and conflict risk. It tracks branch age, visualizes commit activity, predicts merge conflicts, and recommends a merge strategy — all from a dashboard inside your editor. It is built for teams that want to stop stale branches from silently accumulating risk and keep the repository clean.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Branch Health Dashboard"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.3+, JDK 17+, Git (via the bundled Git4Idea plugin)

## Features

### Branch Health Scoring
- **Health score (0–100)** — A single number per branch, based on age, activity, behind-count, and conflict risk.
- **Color-coded status** — Healthy (≥75, green), Aging (≥50, yellow), Stale (≥25, orange), Dead (<25, red).
- **Score breakdown** — Age (up to −40 pts), Activity (+10 to −10 pts), Behind count (up to −15 pts), Conflict risk (up to −20 pts).

### Branch Monitoring
- **Age tracking** — Color-coded branch age at a glance: Healthy ≤7 days, Aging 7–30 days, Stale >30 days.
- **Activity heatmap** — Commits-per-day visualization with trend indicators for each branch.
- **Stale branch detection** — Configurable age threshold with balloon notifications when branches go stale.
- **Branch comparison** — Ahead/behind commit counts against the base branch.

### Dashboard
- **Sortable table** — Sort branches by health score, age, or activity.
- **Filter by status** — Show only Healthy, Aging, Stale, or Dead branches.
- **All branches in one view** — Local and remote branches displayed together with full metrics.

### Merge, Cleanup & Conflicts
- **Conflict prediction** — Detects common files across branches and assigns a risk level: LOW, MEDIUM, HIGH, or CRITICAL.
- **Rebase advisor** — Recommends the optimal merge strategy per branch: REBASE, MERGE, or EITHER.
- **Cleanup automation** — Batch-delete merged branches with dry-run support; protected branches (main, master, develop) are never removed.
- **Orphan commit detection** — Finds commits no longer reachable from any branch.
- **Enhanced notifications** — Team notifications and branch policy enforcement.

## Configuration

**Settings → Tools → Branch Health Dashboard**

| Setting | Default | Description |
|---------|---------|-------------|
| Stale branch threshold (days) | `30` | Branches with no commits for this many days are considered stale (range 1–365). |
| Scan interval (minutes) | `60` | How often the plugin checks repository branches for staleness (range 5–1440). |
| Enable notifications | On | Show notifications when stale or unhealthy branches are detected. |
| Ignored branches | `main, develop, master` | Comma-separated list of branch names to exclude from health checks. |

## Tool Windows

### Branch Health
- **Location:** Bottom panel
- **Content:** Sortable table of all local and remote branches showing health score, age, activity, and ahead/behind counts, with filtering by status (Healthy, Aging, Stale, Dead).

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Scan Branch Health | VCS / Git menu | Scan all branches and calculate health scores. |
| Cleanup Stale Branches | VCS / Git menu | Delete stale branches with confirmation. |

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
