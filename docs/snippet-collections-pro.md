# Snippet Collections Pro

> Organize team code snippets by tags, language, and project scope.

## Overview

Snippet Collections Pro stores reusable code snippets in a dedicated tool window docked to the right edge of the IDE. Each snippet pairs a title with its content, and a search field at the bottom of the panel filters the list as you type.

It is aimed at teams and individual developers who want quick, in-IDE retrieval of common code without leaving the editor. The plugin is project-scoped — its configuration is saved per project, so each project keeps its own settings.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Snippet Collections Pro"**
3. Click **Install** and restart the IDE

**Requirements:** Any IntelliJ-based IDE 2023.2 or newer.

## Features

Snippet Collections Pro is a freemium plugin: the core workflow is free, and a paid Pro tier unlocks additional capabilities.

### Free Tier
- Snippet tool window with a scrollable, searchable list of records
- Case-insensitive live search across snippet titles and content
- Project-level settings persistence

### Professional Tier
- Unlimited usage
- Advanced presets
- Export / import
- Team-ready workflows

## Configuration

**Settings → Tools → Snippet Collections Pro** (project-level)

| Setting | Default | Description |
|---------|---------|-------------|
| Max stored items | 100 | Upper bound on the number of snippets kept in the collection. |

Settings are stored per project (in the project's `snippet-collections-pro.xml`), not globally.

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Open Snippet Collections Pro | **Tools** menu | Opens and focuses the Snippet Collections Pro tool window. |

## Tool Windows

### Snippet Collections Pro
- **Location:** right-hand tool window panel
- **Content:** a scrollable list of snippet records (each shown as *title – content*) with a search field beneath it. Typing in the field instantly filters the list by title or content. The tool window loads even while the IDE is indexing.

## FAQ

**Do I need a license?**
No — the core snippet workflow is free. Pro features require a paid subscription, available through the JetBrains Marketplace.

**Are my settings shared across projects?**
No. Configuration is stored at the project level, so each project keeps its own settings.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
