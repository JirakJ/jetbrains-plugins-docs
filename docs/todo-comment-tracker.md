# TODO Comment Tracker

> Track TODO/FIXME comments with owner and age visibility.

## Overview

TODO Comment Tracker gives you a dedicated place inside the IDE to keep track of
TODO/FIXME items instead of losing them across scattered comments. It adds a
searchable tool window and a project-scoped settings page, all built with native
JetBrains UI components so it fits the look and feel of your IDE.

The plugin is free to install. A paid Professional subscription unlocks
additional capabilities (see **Features**).

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"TODO Comment Tracker"**
3. Click **Install** and restart the IDE

**Requirements:** IntelliJ-based IDE 2023.2+ (works in all IntelliJ-based IDEs)

## Features

### Free Tier
- Dedicated **tool window** for browsing tracked entries
- **Live search** — type in the filter field to narrow the list as you go; matching is case-insensitive and looks at both the entry name and its text
- Entries are ordered with the **most recently updated first**
- **Project-scoped settings**, persisted per project
- Open directly from the **Tools** menu

### Professional Tier
The paid subscription adds:
- Advanced usage limits
- Templates
- Export / import
- Team workflows

## Configuration

**Settings → Tools → TODO Comment Tracker**

| Setting | Default | Description |
|---------|---------|-------------|
| Max entries | 200 | Maximum number of entries kept in the tracker list |

Settings are stored per project, so each project keeps its own configuration.

## Tool Windows

### TODO Comment Tracker
- **Location:** right-hand panel
- **Content:** a scrollable list of tracked entries with a search field at the bottom. Typing in the field filters the list instantly; the most recently updated entries appear at the top.

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Open TODO Comment Tracker | Tools menu | Opens (and focuses) the TODO Comment Tracker tool window |

## FAQ

**How do I open the tracker?**
Use **Tools → Open TODO Comment Tracker**, or click the **TODO Comment Tracker**
tab on the right edge of the IDE.

**Are my settings shared across projects?**
No. Configuration is stored at the project level, so every project has its own
independent settings.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
