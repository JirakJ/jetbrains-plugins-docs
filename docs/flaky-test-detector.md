# Flaky Test Detector

> Detect, track, and quarantine flaky tests directly in your JetBrains IDE.

**Free & open source** — source: https://github.com/JirakJ/flaky-test-detector (Apache-2.0); contributions welcome.

## Overview

Flaky Test Detector records the results of tests you run from the IDE and identifies non-deterministic tests — tests that pass and fail intermittently without code changes. Every test earns a percentage-based flakiness score, so you can see at a glance which tests are stable and which need attention.

It listens to the IDE's test runner, so results from any framework run through it are recorded. Results surface through gutter icons on Java and Kotlin test methods, a sortable dashboard, and quarantine marking for known-flaky tests.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Flaky Test Detector"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2+ with a test runner. Tests must be run from the IDE — only results of the IDE's test runner are recorded.

## Features

- **Automatic tracking** — records every test run (pass/fail/error/skip) automatically
- **Flakiness score** — share of consecutive runs whose outcome changed (pass ↔ fail), in %
- **Categories** — Stable, Suspicious, Flaky, and Highly Unstable, with configurable thresholds
- **Gutter icons** — reliability indicators on Java and Kotlin test methods
- **Dashboard** — sortable, filterable table with a last-10-runs sparkline and trend
- **Quarantine** — mark known-flaky tests in the dashboard, manually or automatically above a threshold
- **Configurable** — category thresholds, minimum runs, and history retention

## Configuration

**Settings → Tools → Flaky Test Detector**

| Setting | Default | Description |
|---------|---------|-------------|
| Enable Flaky Test Detector | On | Enable or disable the flaky test detection analysis |
| Show gutter icons next to @Test | On | Display flakiness status icons in the editor gutter |
| History retention (days) | `30` | Number of days to keep test execution history (1–365) |
| Minimum runs for scoring | `3` | Runs required before a flakiness score is calculated (1–100) |
| Suspicious (%) | `1.0` | Scores at or above this mark a test as suspicious |
| Flaky (%) | `15.0` | Scores above this mark a test as flaky |
| Highly unstable (%) | `50.0` | Scores above this mark a test as highly unstable |
| Enable auto-quarantine | Off | Quarantine tests automatically once they have the minimum number of runs and reach the threshold score |
| Quarantine threshold (%) | `80.0` | Flakiness score that triggers auto-quarantine |

## Tool Windows

### Flaky Tests
- **Location:** Bottom panel (secondary)
- **Content:** Summary line (total, flaky, quarantined) and a sortable table with **Test**, **Class**, **Score**, **Last 10** (sparkline), **Trend**, and **Quarantined** columns. A filter switches between All, Flaky Only, Stable Only, and Quarantined; **Toggle Quarantine** marks or unmarks the selected test.

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| View Flaky Test History | Tools menu | Open the Flaky Tests tool window |
| Clear Flaky Test History | Tools menu | Clear all recorded test history (after confirmation) |

## FAQ

**Why don't I see a flakiness score yet?**
A test needs at least *Minimum runs for scoring* (default 3) recorded runs before a score is calculated. Run your tests a few times from the IDE and scores will appear.

**How is the score calculated?**
It is the share of consecutive runs whose outcome flipped between pass and fail: 0% means the result never changes, while higher values indicate more non-deterministic behavior.

**Does quarantine skip the test?**
No. Quarantine is a marker in the dashboard that helps you track known-flaky tests; it does not change how tests run.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
