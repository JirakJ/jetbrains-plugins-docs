# Commit Template Manager

> Keep a searchable library of reusable commit-message templates inside your IDE.

## Overview

Commit Template Manager gives you a dedicated tool window for storing reusable
commit templates and finding them again quickly with an always-on search box, so
you spend less time re-typing the same commit messages. It is aimed at developers
who reuse the same commit formats — such as Conventional Commits prefixes or
recurring changelog snippets — and want those snippets one search away.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Commit Template Manager"**
3. Click **Install** and restart the IDE

**Requirements:** Any IntelliJ-based IDE 2023.2 or newer. The plugin depends only
on the core platform, so it runs across the IntelliJ family (IntelliJ IDEA,
PyCharm, WebStorm, GoLand, Rider, and others).

## Features

The plugin uses a freemium model: it is fully functional without a license, with a
paid Professional tier for advanced workflows.

### Free Tier
- Reusable commit templates in a dedicated tool window
- Real-time search across template titles and content
- Newest-first list, de-duplicated by title
- Project-level settings persistence

### Professional Tier
- Unlimited usage
- Advanced presets
- Export / import
- Team-ready workflows

## Configuration

Open **Settings → Tools → Commit Template Manager**.

| Setting | Default | Description |
|---------|---------|-------------|
| Max stored items | 100 | Maximum number of templates kept in the list. |

Settings are stored per project in `commit-template-manager.xml`, so each project
keeps its own configuration.

## Tool Windows

### Commit Template Manager
- **Location:** right-hand tool window panel
- **Content:** a scrollable list of your templates shown as `title - content`,
  with a search field at the bottom. Typing filters the list in real time,
  matching either the title or the body (case-insensitive).

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Open Commit Template Manager | **Tools** menu | Opens and focuses the Commit Template Manager tool window. |

## FAQ

**Do I need a license to use it?**
No. The plugin is freemium — every core feature works without a license. A
Professional tier is offered for advanced, team-oriented workflows.

**Where are my settings stored?**
Configuration is saved at the project level in `commit-template-manager.xml`, so
settings do not leak between projects.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
