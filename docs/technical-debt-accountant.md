# Technical Debt Accountant

> Quantify technical debt in dollars, score codebase health A–F, and prioritize refactoring by ROI.

## Overview

Technical Debt Accountant turns abstract code-quality issues into **business metrics**. Catalog debt items by category and priority, track the time spent working around them, convert that time into dollar costs at a configurable hourly rate, and surface an at-a-glance A–F health grade in the tool window and status bar.

Built for developers who need to make the business case for refactoring, it generates management-ready reports with ROI analysis, monthly interest tracking, burndown trends, and forecasts — bridging the gap between engineering and stakeholders.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Technical Debt Accountant"**
3. Click **Install** and restart the IDE

**Requirements:** IntelliJ IDEA 2025.1+ (build 251), Java 17+. The Git4Idea plugin is optional and enables Git integration when present.

## Features

### Debt Health Score
- **A–F health grade** — a 0–100 score with a letter grade summarizing the codebase's debt pressure, shown in the tool window, reports, and status bar
- **Status bar widget** — always-on `Debt <grade> · <monthly interest>/mo` indicator with a detailed tooltip; click to open the Tech Debt tool window
- **Monthly debt budget** — set a budget and get flagged when recurring interest exceeds it

### Debt Tracking
- Catalog debt items with 9 categories, 4 priority levels, and estimated fix times
- Add debt at the cursor's file and line with **Alt+D**
- Workaround time tracking (start/stop timer or manual logging)
- Priority-colored gutter icons with debt tooltips

### Analysis & Detection
- **TODO/FIXME scanner** — imports `TODO`/`FIXME`/`HACK`/`XXX`/`OPTIMIZE` comments as debt items with marker-based category and priority; re-scans deduplicate automatically
- **Hotspot detection** — identifies files with the highest weighted debt concentration
- **Git integration** — links debt items to commits and tracks file authors via blame
- **Project persistence** — inventory stored in `.tech-debt/inventory.json` for Git tracking

### Financial Modeling
- **Dollar valuation** — converts workaround time to cost at the configured hourly rate
- **Monthly interest** — tracks recurring workaround cost over rolling 30-day windows
- **ROI calculator** — computes breakeven months and prioritizes by return on investment
- **Burndown charts** — tracks debt resolution trends over time
- **Management reports** — executive-ready Markdown with summaries and ROI opportunities
- **CSV/JSON export** — shares the backlog with computed dollar costs for Excel/Sheets

### Planning & Reporting
- **Sprint suggestions** — recommends a backlog of debt items maximizing ROI within a time budget
- **Weekly digest** — Markdown/HTML report with a week-over-week delta
- **Trend forecast** — projects debt count, dollars, and burndown from digest snapshot history
- **Debt SLAs** — evaluates the inventory against a project SLA policy and flags breaches; the policy lives in an editable `.debt-sla.json`

## Configuration

**Settings → Tools → Technical Debt Accountant**

| Setting | Default | Description |
|---------|---------|-------------|
| Hourly rate | `80.0` | Developer hourly rate used to calculate debt cost |
| Currency | `USD` | Display currency: USD, EUR, GBP, or CZK |
| Monthly debt budget | `0.0` | Flags the project as over budget when monthly interest exceeds this (`0` disables the check) |
| Inventory path | `.tech-debt` | Directory where the debt inventory is stored (relative to project root) |
| Auto-detect debt items | Enabled | Automatically scan for tech debt markers in the project |
| Show gutter icons | Enabled | Display priority-colored icons in the editor gutter |
| Max free items | `50` | Maximum number of items shown before requiring action |

## Tool Window

### Tech Debt
- **Location:** bottom panel (secondary)
- **Summary bar:** health grade and score, active item count, total workaround cost, and an over-budget warning when applicable
- **Table columns:** ID, File, Category, Priority, Description, Workaround (min), Resolved
- **Buttons:** Add Debt Item, Resolve Selected, Generate Report

## Status Bar Widget

An always-on widget shows `Debt <grade> · <monthly interest>/mo` (or just `Debt <grade>` when there is no recurring interest). Its tooltip lists the health grade and label, score out of 100, active item count, monthly interest, and budget status. Click it to open the Tech Debt tool window.

## Actions

All actions are available from the **Tools** menu.

| Action | Location | Shortcut | Description |
|--------|----------|----------|-------------|
| Add Debt Item | Tools menu, editor context menu | `Alt+D` | Log a technical debt item at the current cursor position |
| Log Workaround Time | Tools menu | — | Log time spent on a workaround for a debt item |
| Generate Debt Report | Tools menu | — | Generate a management-ready Markdown report |
| Suggest Sprint Items… | Tools menu | — | Recommend a sprint backlog maximizing ROI within a time budget |
| Evaluate Debt SLAs… | Tools menu | — | Evaluate the inventory against the SLA policy and flag breaches |
| Weekly Digest… | Tools menu | — | Generate a weekly digest (Markdown/HTML) with week-over-week delta |
| Debt Trend Forecast… | Tools menu | — | Project debt count, dollars, and burndown from snapshot history |
| Scan TODO/FIXME Comments… | Tools menu | — | Import TODO/FIXME/HACK/XXX/OPTIMIZE comments as debt items |
| Export Debt Inventory… | Tools menu | — | Export the inventory as CSV or JSON with computed dollar costs |
| Edit Debt SLA Policy | Tools menu | — | Open `.debt-sla.json` for editing (created from defaults if missing) |

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

Priority weight feeds the weighted hotspot score and prioritization. Each level renders as a colored gutter icon.

| Priority | Weight |
|----------|--------|
| Critical | 4.0 |
| High | 3.0 |
| Medium | 2.0 |
| Low | 1.0 |

## Data Storage

- **Inventory:** JSON at `.tech-debt/inventory.json` — per-project and Git-trackable. Each item records a UUID, file path, line range, category, priority, description, estimated fix time, workaround logs, timestamps, author, and linked commit.
- **SLA policy:** `.debt-sla.json` in the project, created from defaults on first use and editable via the *Edit Debt SLA Policy* action.

## Git Integration

When the Git4Idea plugin is available:
- Automatic author detection via `git blame`
- Commit linking for debt items

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
