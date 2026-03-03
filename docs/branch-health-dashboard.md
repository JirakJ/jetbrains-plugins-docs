# Branch Health Dashboard

> Monitor Git branch health, staleness, and merge readiness from your IDE.

## Overview

Branch Health Dashboard provides a comprehensive overview of all Git branches in your repository, tracking staleness, merge conflicts, CI status, and branch lifecycle. It helps teams identify abandoned branches, prevent merge conflicts, and maintain a clean repository.

## Installation

1. Go to **Settings → Plugins → Marketplace**
2. Search for **"Branch Health Dashboard"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.3+, Java 17+, Git

## Features

### Free Tier
- Branch list with last commit date and author
- Staleness indicators (Fresh, Aging, Stale, Abandoned)
- Ahead/behind commit counts vs. main branch
- Basic branch health score (0-100)
- Quick branch checkout/delete actions

### Pro Tier
- Merge conflict prediction (diff analysis)
- CI/CD status integration (GitHub Actions, GitLab CI)
- Branch lifecycle tracking (creation → merge/delete)
- Team branch ownership view
- Automated stale branch notifications
- Branch naming convention enforcement
- Merge readiness score with recommendations
- Custom staleness thresholds
- Export branch report (CSV/JSON)

## Configuration

### Settings Location
**Settings → Tools → Branch Health Dashboard**

| Setting | Default | Description |
|---------|---------|-------------|
| Main branch | `main` | Branch to compare against |
| Stale threshold (days) | `14` | Days before branch is marked stale |
| Abandoned threshold (days) | `30` | Days before branch is marked abandoned |
| Show remote branches | `true` | Include remote-only branches |
| Auto-refresh interval (min) | `5` | Dashboard refresh interval |

## Tool Windows

### Branch Health
- **Location:** Bottom panel
- **Content:** Sortable branch table with health score, staleness, ahead/behind, author, and last activity
- **Actions:** Checkout, delete, merge, compare with main

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Alt+B` | Open Branch Health Dashboard |

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
