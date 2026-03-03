# Metal GPU Monitor

> Real-time Apple GPU monitoring and performance metrics for macOS.

## Overview

Metal GPU Monitor provides real-time Apple Silicon and discrete GPU monitoring directly in your JetBrains IDE. Using native macOS APIs via **JNA** (Java Native Access) and **IOKit**, it displays GPU utilization, memory usage, temperature, and power consumption — essential for Metal shader developers and macOS performance optimization.

## Installation

1. Open your JetBrains IDE **on macOS**
2. Go to **Settings → Plugins → Marketplace**
3. Search for **"Metal GPU Monitor"**
4. Click **Install** and restart the IDE

**Requirements:** macOS only, JetBrains IDE 2024.3+, Java 17+, Apple Silicon or discrete GPU

## Features

### Free Tier
- Real-time GPU utilization percentage
- GPU memory usage (used/total)
- GPU temperature monitoring
- Basic performance graph (last 60 seconds)
- Status bar widget with GPU utilization

### Pro Tier
- Detailed GPU metrics (clock speed, power consumption, fan speed)
- Multi-GPU monitoring (eGPU support)
- Performance history (30-minute rolling window)
- Alert thresholds (notify on high temp/utilization)
- Metal shader performance correlation
- GPU process list (which apps use GPU)
- Export metrics (CSV/JSON)
- Grafana-compatible metric export

## Configuration

### Settings Location
**Settings → Tools → Metal GPU Monitor**

| Setting | Default | Description |
|---------|---------|-------------|
| Refresh interval (ms) | `1000` | GPU data polling interval |
| Show status bar | `true` | Display GPU utilization in status bar |
| Temperature unit | Celsius | Temperature display unit (°C/°F) |
| Alert on temp (°C) | `90` | Temperature alert threshold |
| Alert on utilization (%) | `95` | Utilization alert threshold |

## Tool Windows

### GPU Monitor
- **Location:** Right panel
- **Content:** Real-time GPU metrics, utilization graph, memory bar, temperature gauge
- **Widgets:** GPU name, utilization %, memory used/total, temperature, power draw

## Technical Details

- **Native Access:** Uses JNA to call macOS IOKit framework
- **Data Source:** `IOServiceMatching("IOAccelerator")` for GPU metrics
- **Polling:** Background thread with configurable interval
- **No Network:** All monitoring is local — no data leaves your machine

## Platform Support

| Platform | Support |
|----------|---------|
| macOS (Apple Silicon) | ✅ Full support |
| macOS (Intel + discrete GPU) | ✅ Full support |
| macOS (Intel integrated) | ⚠️ Limited metrics |
| Linux / Windows | ❌ Not supported |

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
