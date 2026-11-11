# Metal GPU Monitor

> Real-time Apple GPU monitoring — utilization, memory, and thermal state — inside your JetBrains IDE on macOS.

**Free & open source** — source: https://github.com/JirakJ/metal-gpu-monitor-plugin (Apache-2.0); contributions welcome.

## Overview

Metal GPU Monitor brings live Apple GPU statistics into your JetBrains IDE. It reads GPU utilization, memory usage, and thermal state through the native macOS IOKit API, so you don't have to switch to Activity Monitor while you work.

Built for macOS developers — Metal shader authors, ML engineers, and anyone doing GPU-heavy work — it shows the numbers in a status-bar widget and a dedicated tool window with a live chart, and can alert you when utilization, memory, or temperature gets too high. All monitoring is local; no data leaves your machine.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Metal GPU Monitor"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2025.1+ on macOS (Apple Silicon or Intel Mac). The plugin reads GPU statistics through the native IOKit API and does nothing on Linux or Windows.

## Features

- **Status bar widget** — GPU utilization at a glance (icon + %, % only, or bar)
- **Tool window** — live chart of GPU utilization and memory, device info, and a list of GPU-related processes (the IDE and WindowServer first)
- **Thermal state** — Nominal / Fair / Serious / Critical as reported by the system
- **Alerts** — notifications when GPU utilization or memory exceeds your thresholds, or the thermal state becomes serious, with a cooldown
- **Data export** — the last 5 minutes of samples plus the current one as JSON or CSV

macOS does not report GPU utilization per process, so the process list shows which processes are likely using the GPU, not how much.

## Configuration

**Settings → Tools → GPU Monitor**

| Setting | Default | Description |
|---------|---------|-------------|
| Refresh interval | 100ms | GPU polling interval (50ms / 100ms / 250ms / 500ms / 1s) |
| Status bar format | Icon + % | Widget display: Icon + %, % only, Bar, or Off |
| Export format | JSON | Format used when exporting data (JSON or CSV) |
| Enable GPU alerts | On | Master toggle for threshold notifications |
| GPU threshold (%) | 80 | Utilization level that triggers an alert (10–100) |
| Memory threshold (%) | 90 | Memory level that triggers an alert (10–100) |
| Alert cooldown (s) | 60 | Minimum seconds between repeated alerts (10–600) |

## Tool Windows

### GPU Monitor
- **Location:** Bottom panel (secondary)
- **Content:** Live chart of GPU utilization and memory over time, device info (GPU model and core count, thermal state, memory bar), and the GPU-related process list. The toolbar has **Pause**, a **Refresh** interval selector, and **Export**.

## Actions

Available under **Tools → GPU Monitor**:

| Action | Description |
|--------|-------------|
| Toggle GPU Monitoring | Pause or resume GPU monitoring |
| Export GPU Data... | Export the last 5 minutes of samples plus the current one to JSON or CSV |

## FAQ

**Q: Why is this macOS only?**
A: It uses the native macOS IOKit API to read GPU statistics. There is no cross-platform equivalent that provides the same data.

**Q: Why doesn't the process list show per-process percentages?**
A: macOS does not report GPU utilization per process, so the list shows which processes are likely using the GPU rather than how much.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
