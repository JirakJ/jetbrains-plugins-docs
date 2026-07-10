# Test Data Factory

> Generate deterministic test data fixtures with reusable templates, without leaving your IDE.

## Overview

Test Data Factory is a JetBrains IDE plugin for building and reusing test-data records from a dedicated tool window. Each record has a title and content, and a search box filters the list as you type so you can retrieve fixtures quickly while you code and test.

The plugin integrates through a right-hand tool window and a **Tools** menu action, and stores its configuration at the project level.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Test Data Factory"**
3. Click **Install** and restart the IDE

**Requirements:** Any IntelliJ-based JetBrains IDE, version 2023.2 or newer.

## Features

Test Data Factory uses a freemium model.

### Free Tier
- In-IDE tool window to create, store, and browse test-data records
- Instant, case-insensitive search across record titles and content
- Project-level settings persistence

### Professional Tier
A paid subscription (see the Marketplace listing for current pricing) that adds:

- Unlimited usage
- Advanced presets
- Export / import
- Team-ready workflows

## Configuration

**Settings → Tools → Test Data Factory**

| Setting | Default | Description |
|---------|---------|-------------|
| Max stored items | 100 | Maximum number of records the plugin keeps. |

Settings are persisted per project in `test-data-factory.xml`.

## Tool Windows

### Test Data Factory
- **Location:** right tool-window bar
- **Content:** a scrollable list of stored records (shown as `title - content`) with a search field beneath it that filters the list live by title or content.

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Open Test Data Factory | **Tools** menu | Opens and focuses the Test Data Factory tool window. |

## FAQ

**How do I open the panel?**
Use **Tools → Open Test Data Factory**, or click the **Test Data Factory** tab on the right edge of the IDE.

**Where is my configuration stored?**
Per project, in `test-data-factory.xml` inside the project configuration directory.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
