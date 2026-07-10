# Docstring Freshness Monitor

> Detect stale documentation from git history — every docstring gets a 0–100 freshness score.

## Overview

Docstring Freshness Monitor flags documentation that has drifted out of sync with the code it describes. It analyzes git history to compare when the code around a doc block last changed against when the documentation itself last changed, then assigns each docstring a freshness score from 0 to 100. Color-coded gutter icons and an IDE inspection surface stale docs directly in the editor, so you always know which comments still reflect the code.

It covers Java/Kotlin (Javadoc, KDoc), Python (docstrings), and JavaScript/TypeScript (JSDoc), and needs a Git repository with history to compute scores.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Docstring Freshness Monitor"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2+, JDK 17+, a Git repository with history (freshness scoring uses git blame/log).

## Features

Docstring Freshness Monitor is freemium: the core detection features are free, and the advanced project-wide and CI features unlock with a paid license.

### Free Tier
- **Freshness scoring** — 0–100 score for every docstring, computed from git history
- **Gutter icons** — 🟢 Fresh, 🟡 Aging, 🔴 Stale next to each doc block
- **Hover tooltips** — last code change, last doc change, and divergent commit count
- **Stale documentation inspection** with configurable severity
- **Multi-language** — Java/Kotlin, Python, JavaScript/TypeScript
- **Mark as reviewed** — quick-fix to acknowledge a stale doc without editing it

### Professional Tier
- All languages enabled simultaneously
- Project dashboard with treemap visualization
- Trend analysis tracking
- Export reports (HTML, JSON, CSV)
- CI integration with SARIF and JUnit XML output
- Custom score-algorithm extension point

## Configuration

**Settings → Tools → Docstring Freshness Monitor**

| Setting | Default | Description |
|---------|---------|-------------|
| Aging threshold (days) | `80` | Documents older than this many days since last code change are marked as aging |
| Stale threshold (days) | `50` | Documents older than this many days since last code change are marked as stale |
| Rotten threshold (days) | `20` | Documents older than this many days since last code change are marked as rotten |
| Java / Kotlin (Javadoc, KDoc) | `on` | Analyze freshness of Javadoc and KDoc comments |
| Python (docstrings) | `on` | Analyze freshness of Python docstrings |
| JavaScript / TypeScript (JSDoc) | `on` | Analyze freshness of JSDoc comments |
| Ignored patterns | *(empty)* | Comma-separated glob patterns to exclude from analysis (e.g. `*/test/*`, `*/generated/*`) |

## Tool Windows

### Doc Freshness
- **Location:** Bottom panel (secondary)
- **Content:** A **Dashboard** tab with a sortable table of doc blocks — File, Line, Score, Level, and Code Changes (the number of code changes since the doc last changed). The **Scan Current File** and **Scan Project** toolbar buttons populate the table.

## Inspections

| Inspection | Level | Description |
|-----------|-------|-------------|
| Stale documentation | Warning | Flags documentation that git history shows is out of date; grouped under "Documentation freshness". Offers a **Mark as reviewed** quick-fix. Run project-wide via **Analyze → Inspect Code**. |

## Supported Languages

- **Java, Kotlin** — Javadoc, KDoc
- **Python** — docstrings
- **JavaScript, TypeScript** — JSDoc

## FAQ

**Why don't my doc blocks show a freshness score?**
Scoring is computed from git history, so the project must be a Git repository with commits, and the optional Git integration (Git4Idea) must be available.

**How do I acknowledge a stale doc without rewriting it?**
Use the **Mark as reviewed** quick-fix on the inspection warning; it resets freshness without changing the text.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
