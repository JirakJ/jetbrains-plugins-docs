# Dead Code Drift Radar

> Detect and track unused code accumulation over time in your JetBrains IDE.

## Overview

Dead Code Drift Radar identifies dead code (unused classes, methods, imports, variables) and tracks how it accumulates over time. Unlike simple "unused" warnings, it shows the **drift trend** — helping teams understand whether dead code is growing, shrinking, or stable across commits.

## Installation

1. Go to **Settings → Plugins → Marketplace**
2. Search for **"Dead Code Drift Radar"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.3+, Java 17+

## Features

### Free Tier
- Dead code detection (unused methods, classes, imports, variables)
- Project-wide dead code summary (count and percentage)
- Inline gutter markers for unused code
- Basic drift tracking (last 5 scans)

### Pro Tier
- Full drift trend visualization (30-day chart)
- Git integration — dead code linked to introducing commits
- Hotspot analysis (files with most dead code)
- Safe removal suggestions with impact analysis
- Bulk dead code cleanup actions
- Export drift report (CSV/Markdown)
- Team comparison (dead code by contributor)
- CI/CD integration (fail builds on drift increase)

## Configuration

### Settings Location
**Settings → Tools → Dead Code Drift Radar**

| Setting | Default | Description |
|---------|---------|-------------|
| Scan scope | Project | Scan scope (Project, Module, Directory) |
| Include tests | `false` | Include test files in scan |
| Ignore patterns | *(empty)* | File patterns to exclude |
| Drift threshold | `5%` | Alert when dead code exceeds threshold |
| Auto-scan on commit | `false` | Run scan before each commit |

## Tool Windows

### Dead Code Radar
- **Location:** Bottom panel
- **Content:** Dead code summary, drift chart, file hotspot list, removal actions
- **Actions:** Scan project, remove selected dead code, export report

## Inspections

| Inspection | Severity | Description |
|-----------|----------|-------------|
| Unused Method | WARNING | Methods never called in project |
| Unused Class | WARNING | Classes never instantiated or referenced |
| Unused Import | WEAK WARNING | Import statements not used |
| Unused Variable | WEAK WARNING | Variables assigned but never read |

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
