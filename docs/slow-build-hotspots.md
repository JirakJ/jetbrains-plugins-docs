# Slow Build Hotspots

> Identify and fix Gradle build bottlenecks directly in your JetBrains IDE.

## Overview

Slow Build Hotspots parses Gradle `--profile` HTML reports to pinpoint build performance bottlenecks. It detects slow tasks, cache misses, non-incremental builds, and excessive configuration time — providing severity-rated hotspots with optimization recommendations and before/after time projections.

## Installation

1. Go to **Settings → Plugins → Marketplace**
2. Search for **"Slow Build Hotspots"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.3+, Java 17+, Gradle 7.0+

## Getting Started

1. Run your Gradle build with profiling: `./gradlew build --profile`
2. Open the **Build Hotspots** tool window (bottom panel)
3. Click **"Analyze Build Profile"** or use **Tools → Analyze Build Profile**
4. Review hotspots, sorted by impact

## Features

### Free Tier
- Gradle profile HTML report parsing
- Hotspot detection with severity levels (🔴 Critical >30s, 🟠 Slow 10–30s, 🟡 Notable 5–10s)
- Task breakdown table (task name, duration, cache status, incremental flag)
- Build health report (top 10 slowest tasks, cache hit-rate, config vs. execution split)
- Build history (last 5 profiles)
- Performance dashboard in tool window
- Cache hit-rate tracking

### Pro Tier
- Optimization suggestions with quick-fixes (enable build cache, parallel execution, configuration cache)
- Before/after time projections per suggestion
- 30-day build time trend graphs with regression detection
- Unlimited build history
- All inline performance hints
- CSV/JSON data export
- Git commit correlation (build regression detection)

## Configuration

### Settings Location
**Settings → Tools → Slow Build Hotspots**

| Setting | Default | Range | Description |
|---------|---------|-------|-------------|
| Enabled | `true` | — | Enable/disable plugin |
| Slow task threshold (%) | `10` | 1–100 | Minimum % of total build time to flag |
| Configuration threshold (%) | `20` | 1–100 | Configuration phase warning threshold |
| Profile directory override | *(empty)* | Path | Custom Gradle profile directory |
| Auto-analyze | `false` | — | Auto-analyze after each build |
| Max history entries | `50` | 10–500 | Maximum stored build profiles |

**Persistent Storage:** `buildHotspotsSettings.xml` (application scope)

## Tool Windows

### Build Hotspots
- **Location:** Bottom panel
- **Icon:** Custom hotspot icon
- **Tabs:**
  1. **Task Breakdown** — All tasks sorted by duration with cache status
  2. **Hotspots** — Detected issues with severity, type, impact, and suggestions
  3. **Trends** — 30-day build time trends with regression detection (Pro)
- **Toolbar:** Analyze button + status label

## Hotspot Types

| Type | Description | Critical Threshold |
|------|-------------|-------------------|
| `SLOW_TASK` | Tasks consuming disproportionate build time | ≥30% of total |
| `CACHE_MISS` | Tasks with cache misses adding time | ≥5000ms |
| `NON_INCREMENTAL` | Non-incremental tasks adding time | ≥5000ms |
| `CONFIGURATION_TIME` | Configuration phase too long | ≥40% of total |
| `DEPENDENCY_RESOLUTION` | Dependency resolution delays | Variable |

## Actions

| Action | Menu Location | Description |
|--------|---------------|-------------|
| Analyze Build Profile | Tools menu | Parse latest Gradle profile and show results |

## Git Integration (Optional)

When Git4Idea plugin is available:
- **Build Regression Detector** — Correlates build time changes with commits
- **Build Impact Predictor** — Estimates impact of code changes on build time
- **Build Performance Timeline** — Timeline view of performance vs. commits

## FAQ

**Q: Where does Gradle put profile reports?**
A: By default in `build/reports/profile/`. Run `./gradlew build --profile` to generate.

**Q: Does it work with Maven?**
A: No. Currently Gradle only. Maven support is planned.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
