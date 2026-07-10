# Dependency Upgrade Planner

> Plan dependency upgrades with grouped risk insights and actionable order.

## Overview

Dependency Upgrade Planner adds a dedicated tool window for planning your dependency upgrades without leaving the editor. Upgrade entries appear as `key: value` pairs in a scrollable list that you filter with an inline search box, so you can find a dependency by name or note as you type. A single **Tools** menu command opens the panel, and a per-project settings page lets you tune how many entries the list keeps.

It is a lightweight, JetBrains-native panel built from standard IDE list and search components, with its configuration stored per project. The core planner is free, and an optional Professional subscription adds advanced usage limits, templates, import/export, and team workflows.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Dependency Upgrade Planner"**
3. Click **Install** and restart the IDE

**Requirements:** Any IntelliJ-based IDE 2023.2+

## Features

### Free Tier
- **Dependency Upgrade Planner** tool window, docked on the right edge of the IDE
- Searchable entry list with live, as-you-type filtering on both name and value (case-insensitive), most recently updated first
- **Open Dependency Upgrade Planner** action in the **Tools** menu
- Per-project settings page
- Built entirely from native JetBrains UI components

### Professional Tier
- Advanced usage limits
- Templates
- Export / import
- Team workflows

The Pro tier is a paid upgrade (5.90/month).

## Configuration

**Settings → Tools → Dependency Upgrade Planner**

| Setting | Default | Description |
|---------|---------|-------------|
| Max entries | 200 | Maximum number of entries kept in the list. |

Settings are stored per project (in `dependency-upgrade-planner.xml`).

## Tool Windows

### Dependency Upgrade Planner
- **Location:** right tool-window bar
- **Content:** a scrollable list of entries shown as `key: value`, with a search box at the bottom that filters the entries live by name or value.

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Open Dependency Upgrade Planner | **Tools** menu | Reveals and focuses the Dependency Upgrade Planner tool window. |

## FAQ

**How do I open it?**
Use **Tools → Open Dependency Upgrade Planner**, or click the **Dependency Upgrade Planner** tab on the right edge of the IDE.

**Is it free?**
Yes. The core functionality is free; the optional Professional tier adds advanced usage limits, templates, export/import, and team workflows.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
