# Schema Drift Alert

> Detect schema definition drift between modules before integration breaks.

## Overview

Schema Drift Alert gives you a dedicated place inside your IDE to track the schema definitions your project relies on. It adds a tool window that holds a searchable catalog of schema entries, so you can review them in one spot and catch divergence between modules before it turns into a broken integration.

It is aimed at developers working across multiple modules or services that share data contracts, where small, uncoordinated schema changes are easy to miss.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Schema Drift Alert"**
3. Click **Install** and restart the IDE

**Requirements:** Any IntelliJ-based IDE 2023.2+

## Features

### Free Tier
- **Schema Drift Alert tool window** docked in the right sidebar
- **Searchable catalog** of schema entries with live, case-insensitive filtering as you type
- **Open Schema Drift Alert** action in the **Tools** menu to bring the tool window forward
- **Per-project settings** that persist with the project, including a configurable entry limit

### Professional Tier
Paid subscription (5.90/month) that adds:
- Higher usage limits
- Reusable templates
- Export / import
- Team workflows

## Configuration

**Settings → Tools → Schema Drift Alert**

| Setting | Default | Description |
|---------|---------|-------------|
| Max entries | 200 | Maximum number of schema entries kept in the catalog |

Settings are stored per project.

## Tool Windows

### Schema Drift Alert
- **Location:** right panel
- **Content:** a list of catalog entries shown as `key: value`, with a search field at the bottom that filters the list in real time

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Open Schema Drift Alert | Tools menu | Opens (shows) the Schema Drift Alert tool window |

## FAQ

**How do I open the plugin?**
Use **Tools → Open Schema Drift Alert**, or click the **Schema Drift Alert** tab on the right edge of the IDE.

**Which IDEs are supported?**
It depends only on the core IntelliJ platform, so it runs in any IntelliJ-based IDE (such as IntelliJ IDEA, PyCharm, WebStorm, or GoLand) on build 2023.2 or newer.

**Are my settings shared across projects?**
No. Settings are stored per project, so each project keeps its own entry limit.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
