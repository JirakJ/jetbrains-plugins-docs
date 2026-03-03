# Technical Debt Accountant

> Quantify technical debt in dollars, track workaround costs, and prioritize refactoring by ROI.

## Overview

Technical Debt Accountant translates abstract code quality issues into **business metrics**. It lets developers catalog technical debt items with categories and priorities, track time spent on workarounds, calculate dollar costs, and generate management-ready reports with ROI analysis — bridging the gap between developers and stakeholders.

## Installation

1. Go to **Settings → Plugins → Marketplace**
2. Search for **"Technical Debt Accountant"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.3+, Java 17+

## Features

### Free Tier (up to 50 items)
- Catalog tech debt items with 9 categories and 4 priority levels
- Add debt at cursor position with **Alt+D**
- Workaround time tracking (timer + manual logging)
- Hotspot detection (files with most concentrated debt)
- Git integration (commit linking, author tracking via blame)
- Priority-colored gutter icons (🔴 Critical, 🟡 High, 🔵 Medium, ⚪ Low)
- Tech Debt tool window with sortable table
- Project-level persistence in `.tech-debt/inventory.json` (Git-trackable)

### Pro Tier
- Unlimited debt items
- Dollar valuation (workaround time → cost at configurable hourly rate)
- Monthly interest calculation (30-day rolling windows)
- ROI calculator (breakeven analysis in months)
- Burndown chart with trend detection (IMPROVING/STABLE/WORSENING)
- Management report export (Markdown)
- CSV export

## Configuration

### Settings Location
**Settings → Tools → Technical Debt Accountant**

| Setting | Default | Description |
|---------|---------|-------------|
| Hourly rate | `$80.00` | Developer hourly rate for cost calculation |
| Currency | USD | Display currency (USD, EUR, GBP, CZK) |
| Inventory path | `.tech-debt` | Storage directory (relative to project root) |
| Show gutter icons | `true` | Display priority markers in editor |
| Auto-detect debt | `true` | Scan for tech debt markers automatically |
| Max free items | `50` | Free tier item limit |

## Tool Windows

### Tech Debt
- **Location:** Bottom panel
- **Content:** Summary bar (active items + total cost), sortable debt table, action buttons
- **Columns:** ID, File, Category, Priority, Description, Workaround (min), Resolved
- **Actions:** Add Debt Item, Resolve Selected, Generate Report (Pro)

## Actions

| Action | Shortcut | Description |
|--------|----------|-------------|
| Add Debt Item | `Alt+D` | Log technical debt at cursor position |
| Log Workaround Time | — | Track time spent on workarounds |
| Generate Debt Report | — | Create Markdown management report (Pro) |

## Debt Categories

| Category | Description |
|----------|-------------|
| Code Smell | Poor code quality requiring cleanup |
| Missing Tests | Insufficient test coverage |
| Outdated Dependency | Dependency needing upgrade |
| Security Vulnerability | Known security issue |
| Performance Issue | Code causing performance degradation |
| Documentation Gap | Missing or outdated documentation |
| Architecture Violation | Code violating architectural constraints |
| Hardcoded Value | Magic numbers or hardcoded configuration |
| Copy-Paste Code | Duplicated code requiring extraction |

## Priority Levels

| Priority | Weight | Gutter Icon |
|----------|--------|-------------|
| CRITICAL | 4× multiplier | 🔴 Error icon |
| HIGH | 3× multiplier | 🟡 Warning icon |
| MEDIUM | 2× multiplier | 🔵 Info icon |
| LOW | 1× multiplier | ⚪ Note icon |

## Data Storage

- **Format:** JSON (`.tech-debt/inventory.json`)
- **Scope:** Per-project, Git-trackable
- **Fields:** UUID, file path, line range, category, priority, description, estimated fix time, workaround logs, timestamps, author, linked commit, tags

## Git Integration

When Git4Idea plugin is available:
- Automatic author detection via `git blame`
- Commit hash linking for debt items
- Item age calculation from commit timestamps

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
