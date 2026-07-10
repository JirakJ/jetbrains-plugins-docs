# Git Tag Navigator

> Browse, compare, and navigate release tags directly in the IDE.

## Overview

Git Tag Navigator adds a dedicated tool window for browsing release tags without leaving your editor. Tags appear in a scrollable list that you filter with an inline search box, so you can locate a release by name or description as you type. A single **Tools** menu command opens the panel, and a per-project settings page lets you tune how many entries the list keeps.

It is a lightweight, JetBrains-native panel built from standard IDE list and search components, with its configuration stored per project.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Git Tag Navigator"**
3. Click **Install** and restart the IDE

**Requirements:** IntelliJ-based IDE 2023.2+

## Features

### Free Tier
- **Git Tag Navigator** tool window, docked on the right edge of the IDE
- Searchable tag list with live, as-you-type filtering on both tag name and description
- **Open Git Tag Navigator** action in the **Tools** menu
- Per-project settings page

### Professional Tier
A paid upgrade (subscription) that adds advanced usage limits, templates, export/import, and team workflows.

## Configuration

**Settings → Tools → Git Tag Navigator**

| Setting | Default | Description |
|---------|---------|-------------|
| Max entries | 200 | Maximum number of tag entries kept in the list. |

Settings are stored per project.

## Tool Windows

### Git Tag Navigator
- **Location:** right tool-window bar
- **Content:** a searchable list of release tags. Type in the search field at the bottom of the panel to filter the list by name or description.

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Open Git Tag Navigator | Tools menu | Reveals and focuses the Git Tag Navigator tool window. |

## FAQ

**How do I open it?**
Choose **Tools → Open Git Tag Navigator**, or click the **Git Tag Navigator** tab on the right tool-window bar.

**Is it free?**
The core functionality is free. A paid Professional tier adds advanced limits, templates, export/import, and team workflows.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
