# Dead Code & Drift Radar

> Find forgotten, drifting, and dead code before it becomes debt — every scanned file gets a 0–100 drift score.

**Free & open source** — source: https://github.com/JirakJ/dead-code-drift-radar (Apache-2.0); contributions welcome.

## Overview

Dead Code & Drift Radar identifies abandoned and drifting files by combining Git history with reference analysis. Every scanned file gets a **drift score** from 0 to 100 — built from how long ago it last changed, how often it changes (from `git log`), and how many places reference it — so you can see at a glance what is actively maintained and what is rotting.

Results appear in a sortable **Drift Radar** tool window. It is aimed at teams who want to keep a large codebase healthy by catching stale code early, rather than waiting for it to become unmaintainable technical debt.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Dead Code & Drift Radar"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.2+, a Git repository, and the `git` executable on your PATH.

## Features

- **Drift score** — 0–100 per file, combining last-change age and change frequency from `git log` with incoming reference counts
- **Drift levels** — Active, Cooling, Drifting, and Dead, with configurable thresholds
- **Drift Radar tool window** — sortable table of scanned files with a level filter
- **Scan Project / Scan Current File** — under **Tools → Drift Radar**
- **Ignored paths** — exclude path prefixes or globs (`*`, `**`) from scanning

## Configuration

**Settings → Tools → Dead Code & Drift Radar**

| Setting | Default | Description |
|---------|---------|-------------|
| Active threshold | `25` | Scores up to this value are **Active** (recently touched) |
| Cooling threshold | `50` | Scores between Active and this value are **Cooling** (not recently modified) |
| Drifting threshold | `75` | Scores between Cooling and this value are **Drifting**; above it is **Dead** |
| Ignored paths | *(empty)* | Project-relative path prefixes or globs (`*`, `**`), one per line or comma-separated |

### Drift levels

| Level | Score (default thresholds) | Meaning |
|-------|-------|---------|
| Active | 0–25 | Healthy, actively maintained |
| Cooling | 26–50 | Early signs of reduced activity |
| Drifting | 51–75 | Significantly drifting toward dead |
| Dead | 76–100 | Appears dead or abandoned |

## Tool Windows

### Drift Radar
- **Location:** Bottom panel (secondary)
- **Content:** A sortable table with columns **Element**, **Type**, **Drift Score**, **Level**, **Last Modified**, and **References**
- **Filter:** Dropdown to show All, Active, Cooling, Drifting, or Dead entries

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Scan Project for Drift | Tools → Drift Radar | Analyze all project files for code drift |
| Scan Current File for Drift | Tools → Drift Radar | Analyze the current file for code drift |

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
