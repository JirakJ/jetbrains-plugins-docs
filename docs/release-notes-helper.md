# Release Notes Helper

> Collect changes and generate release-note drafts from tagged entries.

## Overview

Release Notes Helper gives you a place inside your JetBrains IDE to capture changes as you make them and turn them into release-note drafts. Each change is stored as a record with a title and description, and every record stays searchable so you can find and reuse past entries when assembling notes for a release.

The plugin works in any IntelliJ-based IDE and keeps its settings per project, so each project holds its own configuration.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Release Notes Helper"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2+

## Features

### Free Tier
- Collect changes as records (title + description) in a dedicated tool window
- Instant search that filters records as you type
- Project-level settings persistence
- Works in any IntelliJ-based IDE

### Professional Tier
- Unlimited usage
- Advanced presets
- Export / import
- Team-ready workflows

Professional features are available through an in-IDE subscription (4.90/month).

## Configuration

**Settings → Tools → Release Notes Helper**

| Setting | Default | Description |
|---------|---------|-------------|
| Max stored items | 100 | Maximum number of records to retain for the project. |

## Tool Windows

### Release Notes Helper
- **Location:** Right tool-window panel
- **Content:** A searchable list of collected records, each shown as *title – description*, with a search box at the bottom that filters the list live as you type.

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Open Release Notes Helper | **Tools** menu | Opens the Release Notes Helper tool window. |

## FAQ

**Which IDEs are supported?**
Any IntelliJ-based IDE on build 2023.2 or newer (IntelliJ IDEA, PyCharm, WebStorm, GoLand, and others) — the plugin depends only on the core platform, not on a specific language.

**Where are my settings stored?**
Per project. Configuration is saved in the project's `release-notes-helper.xml`, so settings don't carry over between projects.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
