# Docstring Freshness Monitor

> Track documentation staleness and keep docstrings in sync with code changes.

## Overview

Docstring Freshness Monitor detects when code changes make existing documentation (docstrings, KDoc, Javadoc, JSDoc) stale. It tracks the last modification date of both code and its documentation, alerting developers when documentation needs updating after code changes.

## Installation

1. Go to **Settings → Plugins → Marketplace**
2. Search for **"Docstring Freshness Monitor"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.3+, Java 17+

## Features

### Free Tier
- Stale docstring detection for Java/Kotlin
- Freshness indicators in editor gutter (🟢 Fresh, 🟡 Aging, 🔴 Stale)
- Basic freshness report (top 10 stale docstrings)
- Configurable staleness threshold

### Pro Tier
- Multi-language support (Python, JavaScript, TypeScript)
- Full project freshness dashboard
- Git-aware staleness (compares docstring vs. code commit dates)
- Auto-update reminders on pre-commit
- Freshness trend tracking
- Bulk documentation update workflow
- Export freshness report (CSV/Markdown)
- CI/CD integration (warn on stale docs percentage)

## Configuration

### Settings Location
**Settings → Tools → Docstring Freshness Monitor**

| Setting | Default | Description |
|---------|---------|-------------|
| Staleness threshold (days) | `30` | Days before docstring is marked stale |
| Show gutter icons | `true` | Display freshness indicators |
| Include private methods | `false` | Monitor private method docstrings |
| Languages | Java, Kotlin | Languages to monitor |
| Ignore patterns | `**/test/**` | File patterns to exclude |

## Tool Windows

### Docstring Freshness
- **Location:** Bottom panel
- **Content:** Freshness summary, stale docstring list, aging timeline
- **Actions:** Navigate to stale docstring, mark as reviewed, generate report

## Inspections

| Inspection | Severity | Description |
|-----------|----------|-------------|
| Stale Docstring | WARNING | Docstring not updated after code change |
| Missing Docstring | WEAK WARNING | Public method without documentation |
| Parameter Mismatch | WARNING | Docstring parameters don't match method signature |

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
