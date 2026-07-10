# PR Description Builder

> Build consistent pull request descriptions from structured sections and checklists.

## Overview

PR Description Builder gives you a dedicated tool window for keeping reusable pull-request description entries close to your code. Each entry pairs a short title with its content, and a live filter lets you find and reuse the right section without leaving the editor — so every PR you open follows the same structure.

It is aimed at developers who write pull or merge request descriptions regularly and want them to stay consistent across a project or team.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"PR Description Builder"**
3. Click **Install** and restart the IDE

**Requirements:** Any IntelliJ-based IDE (IntelliJ IDEA, PyCharm, WebStorm, GoLand, Rider, …), version **2023.2+**.

## Features

PR Description Builder is free to use, with an optional paid upgrade.

### Free Tier
- Right-hand tool window listing your saved PR description entries
- Live search that filters entries by title or content as you type
- Entries kept newest-first, with duplicate titles collapsed
- Project-level settings persistence

### Professional Tier
- Unlimited usage
- Advanced presets
- Export / import
- Team-ready workflows

## Configuration

**Settings → Tools → PR Description Builder**

| Setting | Default | Description |
|---------|---------|-------------|
| Max stored items | 100 | Maximum number of PR description entries retained. Stored per project. |

## Tool Windows

### PR Description Builder
- **Location:** right panel
- **Content:** a scrollable list of your saved entries (shown as `title - content`) with a search field at the bottom that narrows the list live as you type. Search is case-insensitive and matches both the title and the content.

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Open PR Description Builder | **Tools → Open PR Description Builder** | Opens the PR Description Builder tool window. |

## FAQ

**Which IDEs are supported?**
Any IntelliJ-based IDE on version 2023.2 or newer. The plugin depends only on the platform, so IntelliJ IDEA, PyCharm, WebStorm, GoLand, Rider, and the other JetBrains IDEs all work.

**Is there a keyboard shortcut to open it?**
No shortcut ships by default. Open it from **Tools → Open PR Description Builder**, or assign your own under **Settings → Keymap** by searching for "Open PR Description Builder".

**Where are my settings stored?**
Per project — each project keeps its own **Max stored items** value.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
