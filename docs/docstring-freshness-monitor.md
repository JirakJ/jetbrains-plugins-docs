# Docstring Freshness Monitor

> Detect stale documentation from git history — every doc block gets a 0–100 freshness score.

**Free & open source** — source: https://github.com/JirakJ/docstring-freshness-monitor (Apache-2.0); contributions welcome.

## Overview

Docstring Freshness Monitor flags documentation that has drifted out of sync with the code it describes. For each doc block it counts the commits that touched the code below it since the doc itself last changed, and turns that into a freshness score from 0 to 100. An IDE inspection surfaces stale and rotten docs directly in the editor, and a tool window lists per-block scores for the current file.

It covers Javadoc/KDoc, Python docstrings, JSDoc, and `#` comment blocks, and needs a Git repository with history to compute scores.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Docstring Freshness Monitor"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2+, the bundled Git plugin, and a Git repository with history.

## Features

- **Freshness scoring** — 0–100 score per doc block, computed from the commits that touched the code below it since the doc last changed
- **Stale documentation inspection** — stale blocks are reported as warnings, rotten blocks as errors; also available project-wide via **Analyze → Inspect Code**
- **Multi-language** — Javadoc/KDoc, Python docstrings, JSDoc, and `#` comment blocks
- **Doc Freshness tool window** — per-block scores for the current file
- **Configurable thresholds** — fresh / aging / stale / rotten score boundaries

## Configuration

**Settings → Tools → Docstring Freshness Monitor**

| Setting | Default | Description |
|---------|---------|-------------|
| Fresh at score ≥ | `80` | Freshness score at or above which a doc block is **Fresh** |
| Aging at score ≥ | `50` | Below the fresh threshold but at or above this score: **Aging** |
| Stale at score ≥ (below: rotten) | `20` | Below the aging threshold but at or above this score: **Stale**; lower scores are **Rotten** |

## Tool Windows

### Doc Freshness
- **Location:** Bottom panel (secondary)
- **Content:** A table of doc blocks in the current file — **File**, **Line**, **Score**, **Level**, and **Code Changes** (commits to the code since the doc last changed). The **Scan Current File** button populates the table.

## Inspections

| Inspection | Level | Description |
|-----------|-------|-------------|
| Stale documentation (group *Documentation freshness*) | Warning (Error for rotten) | Flags documentation that git history shows is out of date. Run project-wide via **Analyze → Inspect Code**. |

## Supported Languages

- **Java, Kotlin** — Javadoc, KDoc
- **Python** — docstrings
- **JavaScript, TypeScript** — JSDoc
- **Other files** — `#` comment blocks

## FAQ

**Why don't my doc blocks show a freshness score?**
Scoring is computed from git history, so the project must be a Git repository with commits and the bundled Git plugin must be enabled.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
