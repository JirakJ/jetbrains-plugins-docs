# Code Search Presets

> Save and run reusable project-wide search presets with one click.

## Overview

Code Search Presets adds a right-hand tool window where you keep frequently used searches as named presets. Each preset is a titled record you can recall instantly, so you stop retyping the same project-wide queries. A filter box narrows the list as you type, matching on both the preset title and its contents.

Presets and settings are scoped to the current project, and the panel opens from the Tools menu or from the tool window strip. The plugin depends only on the core IntelliJ platform, so it runs in any JetBrains IDE regardless of the languages in your project.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Code Search Presets"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2+

## Features

The plugin is freemium: the free tier covers the core workflow, and a Professional tier raises limits and adds extras.

### Free Tier
- Save reusable search presets and recall them from the tool window
- Instant filtering across preset titles and contents
- Right-hand tool window built with native JetBrains UI components
- Project-level settings persistence

### Professional Tier
- Unlimited stored presets
- Advanced presets
- Export and import
- Team-ready workflows

## Configuration

**Settings → Tools → Code Search Presets**

| Setting | Default | Description |
|---------|---------|-------------|
| Max stored items | 100 | Maximum number of presets kept for the project |

## Tool Windows

### Code Search Presets
- **Location:** right-hand tool window
- **Content:** a scrollable list of saved presets shown as `title - content`, with a search field beneath it that filters the list live by title or content (case-insensitive)

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Open Code Search Presets | Tools menu | Shows and focuses the Code Search Presets tool window |

## FAQ

**How do I open the panel?**
Use **Tools → Open Code Search Presets**, or click the **Code Search Presets** tab on the right edge of the IDE.

**Are presets shared across projects?**
No. Settings are stored per project (in `code-search-presets.xml`), so each project keeps its own configuration.

**Is it limited to a specific language?**
No. The plugin depends only on the core IntelliJ platform, so it works in any JetBrains IDE and with any project type.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
