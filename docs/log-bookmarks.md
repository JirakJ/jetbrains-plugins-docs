# Log Bookmarks

> Bookmark important log lines and jump back to them instantly during debugging.

## Overview

Log Bookmarks gives you a dedicated tool window that holds a searchable list of important log lines, so the ones worth remembering stay one place away during a debugging session. It targets developers working through long console output who want to keep track of key lines instead of scrolling to find them again.

Log Bookmarks is offered as a freemium plugin on the JetBrains Marketplace — the workflow described here is available for free.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Log Bookmarks"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2+, JDK 17+

## Features

- **Bookmarks tool window** — a dockable panel on the right that lists your saved log bookmarks, each shown with its title and content.
- **Live search** — a search box filters the list as you type, matching on both the title and the content of each bookmark (case-insensitive).
- **Newest-first list** — bookmarks are ordered with the most recent at the top.
- **Open from the Tools menu** — reveal the tool window from **Tools → Open Log Bookmarks**.
- **Configurable retention limit** — set how many bookmarks are kept (see Configuration).

## Configuration

**Settings → Tools → Log Bookmarks**

| Setting | Default | Description |
|---------|---------|-------------|
| Max stored items | 100 | Maximum number of log bookmarks to retain. |

## Tool Windows

### Log Bookmarks
- **Location:** right tool-window panel
- **Content:** a searchable list of your saved log bookmarks, newest first, with a search box at the bottom to filter by title or content.

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Open Log Bookmarks | Tools menu | Shows the Log Bookmarks tool window. |

## FAQ

**How do I open Log Bookmarks?**
Use **Tools → Open Log Bookmarks**, or click the **Log Bookmarks** tab on the right-hand tool-window strip.

**How does search work?**
Type in the search box at the bottom of the tool window. The list filters instantly to bookmarks whose title or content contains your text, ignoring case.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
