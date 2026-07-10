# Dead Code & Drift Radar

> Find forgotten, drifting, and dead code before it becomes debt — every file gets a 0–100 drift score.

## Overview

Dead Code & Drift Radar identifies abandoned, drifting, and dead code by combining Git history with static reference analysis. Every file — and individual methods — is assigned a **drift score** from 0 to 100, so you can see at a glance what is actively maintained and what is rotting.

Scores surface as color-coded gutter icons in the editor and as a sortable dashboard in a dedicated tool window. It is aimed at teams who want to keep a large codebase healthy by catching stale code early, rather than waiting for it to become unmaintainable technical debt.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Dead Code & Drift Radar"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2+, JDK 21+, and a Git repository (Git history feeds the drift score).

## Features

### Core drift analysis
- **Drift score** — a 0–100 health metric per file, combining Git history and reference analysis
- **Gutter icons** — color-coded indicators showing each element's drift level directly in the editor
- **Hover tooltips** — author, last change date, reference count, and the drift breakdown
- **Project View badges** — drift status shown in the project tree without opening files
- **Configurable thresholds** — set your own boundaries for each drift level

### Advanced analysis & reporting
- **Method-level drift scores** — scoring for individual methods, not just whole files
- **Project heatmap** — visualize drift hotspots across the entire project
- **Trend analysis and cleanup backlog** — track drift over time and prioritize cleanup
- **Zombie and orphan code detection** — flag unreachable and unreferenced code
- **Safe-to-remove confidence scores** — gauge how safe a deletion is
- **Report export** — generate SARIF and JUnit XML reports
- **CI integration** — run drift analysis as a Gradle task

## Configuration

**Settings → Tools → Dead Code & Drift Radar**

| Setting | Default | Description |
|---------|---------|-------------|
| Enable drift analysis | `on` | Continuously monitor code drift across the project |
| Active threshold | `25` | Scores at or below this are **Active** (recently touched) |
| Cooling threshold | `50` | Scores up to this are **Cooling** (not recently modified) |
| Drifting threshold | `75` | Scores up to this are **Drifting**; above it is **Dead** |
| Ignored paths | *(empty)* | Comma-separated list of paths to exclude from scanning |

### Drift levels

| Level | Score | Meaning |
|-------|-------|---------|
| Active | 0–25 | Healthy, actively maintained |
| Cooling | 26–50 | Early signs of reduced activity |
| Drifting | 51–75 | Significantly drifting toward dead |
| Dead | 76–100 | Appears dead or abandoned |

Score ranges follow the default thresholds above and shift when you change them.

## Tool Windows

### Drift Radar
- **Location:** Bottom panel (secondary)
- **Content:** A sortable table of code elements with columns **Element**, **Type**, **Drift Score**, **Level**, **Last Modified**, and **References**, ordered by score
- **Filter:** Dropdown to show All, Active, Cooling, Drifting, or Dead elements

## Actions

Both actions live under **Tools → Drift Radar**.

| Action | Location | Description |
|--------|----------|-------------|
| Scan Project for Drift | Tools → Drift Radar | Analyze all project files for code drift |
| Scan Current File for Drift | Tools → Drift Radar | Analyze the current file for code drift |

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
