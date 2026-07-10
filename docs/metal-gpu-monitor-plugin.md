# Metal GPU Monitor

> Real-time Apple GPU monitoring — utilization, memory, thermal state, and per-process usage — inside your JetBrains IDE on macOS.

## Overview

Metal GPU Monitor brings live Apple GPU telemetry directly into your JetBrains IDE. It reads GPU utilization, memory usage, thermal state, and per-process GPU consumption through native macOS IOKit APIs (via JNA), so you never have to switch to Activity Monitor while you work.

Built for macOS developers — Metal shader authors, ML engineers, and anyone doing GPU-heavy work — it surfaces the numbers as a status-bar widget and a dedicated tool window with live charts. All monitoring is local; no data leaves your machine.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Metal GPU Monitor"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2025.1+ · JDK 17+ · macOS 14+ (Sonoma or later) · Apple Silicon (M1/M2/M3/M4) or an Intel Mac with an integrated or discrete GPU. macOS only — the plugin relies on Apple IOKit and Metal APIs and does nothing on Linux or Windows.

## Features

Metal GPU Monitor is freemium: the core monitor is free, and a Pro subscription (paid, via the JetBrains Marketplace, with a 30-day trial) unlocks extended history, alerts, and export.

### Free Tier
- **Status bar widget** — at-a-glance GPU utilization percentage with a color-coded indicator
- **Tool window** — dedicated bottom panel with live charts of GPU utilization and memory usage
- **Thermal state monitoring** — real-time thermal level: Nominal, Fair, Serious, or Critical
- **Device info** — GPU model, vendor, and core count
- **Basic per-process tracking** — the top GPU-consuming processes
- **5-minute history** — short-term charts of recent GPU activity

### Pro Tier
- **24-hour history** — extended data retention with scrollable charts
- **Configurable alerts** — get notified when GPU utilization or memory crosses your thresholds, with a cooldown to avoid spam
- **Data export** — save monitoring data to JSON or CSV for external analysis
- **Full per-process list** — complete per-process GPU usage with the IDE's own process highlighted
- **Custom dashboard layouts** — rearrange the tool-window panels

## Configuration

**Settings → Tools → GPU Monitor**

| Setting | Default | Description |
|---------|---------|-------------|
| Refresh interval | 1 second | GPU polling interval (1 / 2 / 5 / 10 seconds) |
| Status bar format | Icon + % | Widget display: Icon + %, % only, Bar, or Off |
| Enable GPU alerts | On | Master toggle for threshold notifications |
| GPU threshold (%) | 80 | Utilization level that triggers an alert (10–100) |
| Memory threshold (%) | 90 | Memory level that triggers an alert (10–100) |
| Alert cooldown (s) | 60 | Minimum seconds between repeated alerts (10–600) |

## Tool Windows

### GPU Monitor
- **Location:** bottom panel (secondary)
- **Content:** live charts of GPU utilization and memory over time, a per-process GPU usage table, and a device-info panel (model, vendor, core count, thermal state)

## Actions

Available under **Tools → GPU Monitor**:

| Action | Location | Description |
|--------|----------|-------------|
| Toggle GPU Monitoring | Tools → GPU Monitor | Pause or resume GPU monitoring |
| Export GPU Data... | Tools → GPU Monitor | Export monitoring data to JSON or CSV (Pro) |

## FAQ

**Q: Why is this macOS only?**
A: It uses native macOS IOKit APIs and the Metal framework to read GPU performance counters. These are specific to Apple's OS and hardware — there is no cross-platform equivalent that provides the same detail.

**Q: Will it slow down my IDE?**
A: No. GPU polling runs on a background thread at your chosen interval (default 1 second). The overhead is negligible — comparable to leaving Activity Monitor open.

**Q: Does it support external GPUs (eGPUs)?**
A: Yes. Any GPU visible to macOS IOKit is detected, including eGPUs connected over Thunderbolt.

**Q: How does the Pro trial work?**
A: You get 30 days of full Pro access. After the trial, Pro features are disabled and you continue on the free tier. Upgrade anytime via the JetBrains Marketplace.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
