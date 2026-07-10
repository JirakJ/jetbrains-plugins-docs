# HTTP Request History

> Track and replay recent HTTP client requests made during development, from a searchable panel inside your IDE.

## Overview

HTTP Request History keeps the HTTP client requests you make while developing within easy reach. It adds a dedicated tool window that lists your recent requests newest-first and lets you filter them instantly with a search box, so you can find and reuse an earlier call without digging back through scratch files or logs.

The plugin stores its history per project. It is aimed at developers who work with REST/HTTP endpoints day to day and want a fast, in-IDE way to revisit requests they have already run.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"HTTP Request History"**
3. Click **Install** and restart the IDE

**Requirements:** IntelliJ-based IDE 2023.2 or later

## Features

HTTP Request History is free to use, with an optional paid upgrade.

### Free Tier
- Recent-request history kept newest-first, de-duplicated by title
- Instant search across request titles and content
- Dedicated tool window built with native JetBrains UI components
- Project-level settings persistence

### Professional Tier
- Unlimited history
- Advanced request presets
- Export / import of history
- Team-ready workflows

## Configuration

**Settings → Tools → HTTP Request History**

| Setting | Default | Description |
|---------|---------|-------------|
| Max stored items | 100 | Maximum number of requests retained in the history list. |

Settings are stored per project, so each project keeps its own preferences.

## Tool Windows

### HTTP Request History
- **Location:** right tool-window bar
- **Content:** a scrollable list of recorded requests (shown as `title - content`), newest first, with a search field at the bottom that filters the list as you type.

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Open HTTP Request History | **Tools** menu | Opens and focuses the HTTP Request History tool window. |

## FAQ

**How do I open the panel?**
Use **Tools → Open HTTP Request History**, or click the **HTTP Request History** tab on the right edge of the IDE.

**How do I find a specific request?**
Type into the search box at the bottom of the tool window. The list filters by both title and content as you type; clearing the box shows everything again.

**Are my settings shared across projects?**
No. Configuration is stored per project, so history preferences do not leak between projects.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
