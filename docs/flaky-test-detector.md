# Flaky Test Detector

> Identify, track, and quarantine flaky tests directly in your JetBrains IDE.

## Overview

Flaky Test Detector monitors your test suite for non-deterministic tests — tests that pass and fail intermittently without code changes. It tracks test execution history, calculates flakiness scores, and provides quarantine functionality to isolate unreliable tests from CI pipelines.

## Installation

1. Go to **Settings → Plugins → Marketplace**
2. Search for **"Flaky Test Detector"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.3+, Java 17+, JUnit/TestNG

## Features

### Free Tier
- Test execution history tracking (last 10 runs)
- Flakiness score (0-100) per test
- Visual flakiness indicators in test runner
- Basic flaky test list with pass/fail ratio
- Gutter icons for known flaky tests

### Pro Tier
- Unlimited execution history
- Root cause analysis (timing, ordering, resource contention)
- Test quarantine mode (skip flaky tests in CI)
- Flakiness trend dashboard (30-day view)
- Re-run strategies (retry count, delay configuration)
- Git integration — correlate flakiness with code changes
- Team notification on new flaky tests
- Export report (JUnit XML annotations, CSV)
- CI/CD integration (quarantine list export)

## Configuration

### Settings Location
**Settings → Tools → Flaky Test Detector**

| Setting | Default | Description |
|---------|---------|-------------|
| History depth | `10` | Number of runs to track per test |
| Flakiness threshold | `20%` | Minimum fail rate to flag as flaky |
| Auto-quarantine | `false` | Automatically quarantine highly flaky tests |
| Retry count | `3` | Number of retries for flaky tests |
| Retry delay (ms) | `1000` | Delay between retries |

## Tool Windows

### Flaky Test Dashboard
- **Location:** Bottom panel
- **Content:** Flaky test list, flakiness scores, execution history chart, quarantine controls
- **Actions:** Quarantine test, retry test, view history, export report

## Inspections

| Inspection | Severity | Description |
|-----------|----------|-------------|
| Flaky Test | WARNING | Test has intermittent pass/fail pattern |
| Quarantined Test | INFO | Test is currently quarantined |

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
