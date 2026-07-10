# Changelog Enforcer

> Keep your changelog entries present and well-formed before every release.

## Overview

Changelog Enforcer helps teams that maintain a changelog make sure entries are captured and well-formed before a release goes out. It adds a dedicated tool window with a searchable catalog of changelog entries and a live filter, so you can review what's recorded without leaving the editor.

The plugin runs in any IntelliJ-based IDE and is free to use. Freemium licensing is enabled at the manifest level, but the plugin remains fully functional without a license; premium features may be introduced in future releases.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Changelog Enforcer"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2+, JDK 17+

## Features

- Verify that changelog entries are present and well-formed before a release
- Browse entries in a dedicated, right-docked tool window
- Filter the catalog live with case-insensitive search across entry keys and content
- Open the tool window in one click from the **Tools** menu
- Project-scoped settings that persist with the project

## Configuration

**Settings → Tools → Changelog Enforcer**

| Setting | Default | Description |
|---------|---------|-------------|
| Max entries | 200 | Maximum number of entries retained in the catalog |

Settings are stored per project (`changelog-enforcer.xml`).

## Tool Windows

### Changelog Enforcer

- **Location:** right panel
- **Content:** a searchable list of changelog entries with a filter box below it. Type in the box to narrow the list by entry key or value as you go.

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Open Changelog Enforcer | **Tools** menu | Reveals the Changelog Enforcer tool window |

## FAQ

**Do I need a paid license?**
No. The plugin is fully functional for free. Optional licensing is enabled so premium features can be added later without breaking existing use.

**How do I open the tool window?**
Use **Tools → Open Changelog Enforcer**, or click the Changelog Enforcer tab on the right edge of the IDE.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
