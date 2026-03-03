# Run Config Drift Detector

> Detect and prevent run configuration inconsistencies across team members.

## Overview

Run Config Drift Detector monitors your IDE run configurations for drift — when configurations change between developers, branches, or over time. It version-controls run configurations, detects differences, and ensures team consistency.

## Installation

1. Go to **Settings → Plugins → Marketplace**
2. Search for **"Run Config Drift Detector"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.3+, Java 17+

## Features

### Free Tier
- Run configuration snapshot comparison
- Drift detection between local and shared configs
- Visual diff of configuration parameters
- Basic drift notifications
- Last 5 configuration snapshots

### Pro Tier
- Unlimited snapshot history
- Git integration — track config changes per commit
- Team configuration baseline enforcement
- Auto-fix drift (reset to baseline)
- Environment variable drift detection
- JVM argument comparison
- Working directory validation
- Configuration health score
- Export configuration as sharable format
- CI/CD parameter consistency checking

## Configuration

### Settings Location
**Settings → Tools → Run Config Drift Detector**

| Setting | Default | Description |
|---------|---------|-------------|
| Auto-scan interval | `5 min` | How often to check for drift |
| Baseline source | `.idea/runConfigurations` | Baseline configuration location |
| Ignore fields | *(empty)* | Configuration fields to ignore in comparison |
| Alert on drift | `true` | Show notification when drift detected |

## Tool Windows

### Configuration Drift
- **Location:** Bottom panel
- **Content:** Configuration comparison table, drift summary, diff viewer
- **Actions:** Compare configs, reset to baseline, export config, take snapshot

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
