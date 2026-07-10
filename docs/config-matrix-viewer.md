# Config Matrix Viewer

> Compare configuration variants across environments in a matrix view.

## Overview

Config Matrix Viewer is an IntelliJ-platform plugin that surfaces your project's
configuration entries in a single, searchable panel, so you can compare variants
across environments without leaving the IDE. Entries appear as key/value pairs
that you can filter as you type, using standard JetBrains UI components.

The plugin is freemium: the core viewer is free, and an optional Professional
subscription unlocks advanced usage limits, templates, import/export, and team
workflows.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Config Matrix Viewer"**
3. Click **Install** and restart the IDE

**Requirements:** any IntelliJ-based IDE, 2023.2 or newer

## Features

### Free Tier
- Matrix panel that lists configuration entries as `key: value` pairs
- Live search field that filters the list as you type
- Open from the **Tools** menu or the right-hand tool window
- Built entirely from native JetBrains UI components
- Project-level settings persisted with the project

### Professional Tier
- Advanced usage limits
- Configuration templates
- Import / export
- Team workflows

## Configuration

**Settings → Tools → Config Matrix Viewer**

| Setting | Default | Description |
|---------|---------|-------------|
| Max entries | 200 | Maximum number of configuration entries kept in the matrix list. |

Settings are stored per project (in `config-matrix-viewer.xml`).

## Tool Windows

### Config Matrix Viewer
- **Location:** right tool-window bar
- **Content:** a scrollable list of configuration entries shown as `key: value`,
  with a search box at the bottom that filters the entries live.

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Open Config Matrix Viewer | **Tools** menu | Shows the Config Matrix Viewer tool window. |

## FAQ

**Do I need a paid license to use the plugin?**
No. The core matrix viewer is free; the Professional tier is an optional
subscription that adds templates, import/export, usage limits, and team features.

**How do I open the viewer?**
Use **Tools → Open Config Matrix Viewer**, or click the **Config Matrix Viewer**
tab on the right edge of the IDE.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
