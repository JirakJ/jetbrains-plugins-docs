# Slow Build Hotspots

> Find and fix Gradle build bottlenecks from inside your JetBrains IDE.

## Overview

Slow Build Hotspots parses the HTML report produced by Gradle's `--profile` flag to pinpoint slow tasks, cache misses, and non-incremental operations. Each finding is surfaced as a ranked, severity-rated hotspot with a concrete optimization suggestion, so you can see exactly where your build spends its time and what to change to speed it up.

Results appear in a dedicated tool window with a task breakdown, the detected hotspots, and a per-build time breakdown. It is aimed at developers and build engineers working in Gradle projects who want build-performance analysis without leaving the IDE or wiring up external tooling.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Slow Build Hotspots"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2+, JDK 17+, and a Gradle project that can produce `--profile` HTML reports.

## Getting Started

1. Generate a profile: run `./gradlew build --profile` (Gradle writes an HTML report under `build/reports/profile/`).
2. Open the **Build Hotspots** tool window (bottom of the IDE).
3. Click **Analyze Latest Build** in the tool window, or run **Tools → Analyze Build Profile**.
4. Review the **Task Breakdown**, **Hotspots**, and **Trend** tabs — hotspots are sorted by impact. A summary notification reports how many hotspots were found.

## Features

### Build Analysis
- Parse Gradle `--profile` HTML reports automatically
- Ranked hotspot detection with Critical / Warning / Info severity
- Cache-miss analysis — flag cacheable tasks that missed the build cache
- Non-incremental detection — find tasks that ran without incremental support

### Visualization
- Task breakdown: every task sorted by duration, with cache and incremental status
- Hotspots view: detected issues with severity, type, impacted task, impact (ms), and a suggestion
- Per-build time breakdown: total build time, task count, and an ASCII bar chart of the slowest tasks

### Optimization
- Per-hotspot optimization suggestions — enable the build cache (`org.gradle.caching=true`), incremental compilation, the configuration cache (`org.gradle.configuration-cache=true`), lazy task configuration, or split large tasks

## Configuration

**Settings → Tools → Slow Build Hotspots**

| Setting | Default | Description |
|---------|---------|-------------|
| Enable Slow Build Hotspots | On | Master enable toggle for the plugin |
| Auto-analyze after build | Off | Run analysis automatically when a build completes |
| Slow task threshold (%) | 10 | Flag tasks taking more than this share of total build time (1–100) |
| Configuration threshold (%) | 20 | Flag when the configuration phase exceeds this share of total time (1–100) |
| Profile directory | *(auto-detect)* | Override the Gradle profile directory; leave empty to auto-detect `build/reports/profile` |
| Max history entries | 50 | Number of past analyses to keep in history (10–500) |

**Persistent storage:** `buildHotspotsSettings.xml` (application scope, roamable).

## Tool Window

### Build Hotspots
- **Location:** bottom panel (secondary)
- **Toolbar:** **Analyze Latest Build** and **Clear** buttons, with a status line along the bottom
- **Tabs:**
  - **Task Breakdown** — every task sorted by duration, with cache and incremental status
  - **Hotspots** — detected issues with severity, type, task, impact (ms), and suggestion
  - **Trend** — total build time, task count, and an ASCII bar chart of the slowest tasks in the analyzed build

## Hotspot Detection

Every hotspot is rated **Critical 🔴**, **Warning 🟡**, or **Info 🟢** based on its impact. The analyzer produces four kinds of hotspot, sorted by impact:

| Type | Detected when | Critical at |
|------|---------------|-------------|
| Slow Task | Task exceeds the slow-task threshold (default 10%) of total build time | ≥ 30% of total |
| Cache Miss | A cacheable task missed the cache (duration > 500 ms) | ≥ 5000 ms |
| Non-Incremental | Task ran non-incrementally (duration > 500 ms) | ≥ 5000 ms |
| Configuration Time | Configuration phase exceeds the configuration threshold (default 20%) | ≥ 40% of total |

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Analyze Build Profile | Tools menu | Parse the latest Gradle profile report and show the detected hotspots |

## FAQ

**Q: Where does Gradle put profile reports?**
A: By default under `build/reports/profile/`. Generate one with `./gradlew build --profile`. You can point the plugin at a different location via **Profile directory** in settings.

**Q: Does it support Maven?**
A: No. The analyzer reads Gradle `--profile` HTML reports only.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
