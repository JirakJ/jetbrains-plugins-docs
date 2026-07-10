# Flaky Test Detector

> Detect, track, and quarantine flaky tests directly in your JetBrains IDE.

## Overview

Flaky Test Detector automatically records your test execution history and identifies non-deterministic tests — tests that pass and fail intermittently without code changes. Every test earns a percentage-based reliability score, so you can see at a glance which tests are stable and which need attention.

It hooks into the IDE's test runner, so it works with any JetBrains-supported test framework, and surfaces results through editor gutter icons, a sortable dashboard, and quarantine controls that keep known-flaky tests from blocking your workflow.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Flaky Test Detector"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2+, JDK 17+, any JetBrains-supported test framework

## Features

Flaky Test Detector is freemium: the core tracking and dashboard are free, with additional features unlocked by a license.

### Free Tier
- **Automatic tracking** — records every test run (pass/fail/error/skip) automatically
- **Flakiness score** — percentage-based reliability metric per test
- **Gutter icons** — reliability indicators next to `@Test` annotations
- **Dashboard** — sortable table with sparkline stability visualizations
- **Quarantine mode** — isolate known-flaky tests from blocking development
- **One-click rerun** — rerun any test directly from the dashboard

### Pro Tier
- Unlimited tests and history retention
- Flakiness trend charts
- Git correlation (find the commit that broke a test)
- Module- and package-level aggregation
- Auto-quarantine rules
- Export reports (JSON, CSV, HTML)
- CI/CD integration

## Configuration

**Settings → Tools → Flaky Test Detector**

| Setting | Default | Description |
|---------|---------|-------------|
| Enable Flaky Test Detector | On | Master switch for the detection analysis |
| Show gutter icons next to @Test | On | Display flakiness status icons in the editor gutter |
| History retention (days) | `30` | Number of days to keep test execution history (1–365) |
| Minimum runs for scoring | `3` | Runs required before a flakiness score is calculated (1–100) |
| Suspicious (%) | `1.0` | Failure rate above this marks a test as suspicious |
| Flaky (%) | `15.0` | Failure rate above this marks a test as flaky |
| Highly unstable (%) | `50.0` | Failure rate above this marks a test as highly unstable |
| Enable auto-quarantine | Off | Automatically quarantine tests that exceed the threshold |
| Quarantine threshold (%) | `80.0` | Tests with a failure rate above this are auto-quarantined |

## Tool Windows

### Flaky Tests
- **Location:** Bottom panel (secondary)
- **Content:** Sortable table of tracked tests showing test name, class, flakiness score and category, a sparkline of the last runs, a trend indicator, and quarantine state. A filter switches between All, Flaky Only, Stable Only, and Quarantined tests, and tests can be rerun or quarantined directly from the panel.

## Actions

All actions are available under the **Tools** menu.

| Action | Location | Shortcut | Description |
|--------|----------|----------|-------------|
| Rerun Flaky Tests | Tools menu | `Alt+Shift+F` | Rerun all tests with a non-zero flakiness score |
| Quarantine Test | Tools menu | — | Toggle quarantine status on the selected test |
| View Flaky Test History | Tools menu | — | Open the Flaky Tests tool window |
| Clear Flaky Test History | Tools menu | — | Clear all recorded test history |

## FAQ

**Why don't I see a flakiness score yet?**
A test needs at least *Minimum runs for scoring* (default 3) recorded runs before a score is calculated. Run your suite a few times and scores will appear.

**Which test frameworks are supported?**
Any JetBrains-supported framework. The plugin listens to the IDE's test runner, so JUnit, TestNG, pytest, Jest, and others are all tracked automatically.

**How is the score calculated?**
The score reflects how often a test's outcome changes between consecutive runs: 0% means the result never changes (stable), while higher values indicate more non-deterministic behavior.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
