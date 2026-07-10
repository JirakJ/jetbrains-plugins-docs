# Terminal Command Recorder

> Record, annotate, and replay terminal command sequences safely.

## Overview

Terminal Command Recorder gives you a dedicated place inside your JetBrains IDE to capture terminal command sequences as titled records, keep them a search away, and reuse them instead of retyping. Records appear in a tool window docked to the right edge of the IDE, each shown as a title alongside its command content.

A search box filters your records as you type, matching on both the title and the command text, so the sequence you need is only a few keystrokes away. It is aimed at developers who run the same setup, build, or deployment commands often and want them organized without leaving the editor.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Terminal Command Recorder"**
3. Click **Install** and restart the IDE

**Requirements:** IntelliJ-based IDE 2023.2+

## Features

### Free Tier
- Save terminal command sequences as titled, searchable records
- Live search that filters records by title and content as you type
- Dedicated tool window docked to the right edge of the IDE
- Project-level settings persistence

### Professional Tier
- Unlimited usage
- Advanced presets
- Export and import of records
- Team-ready workflows

The plugin is free to install and use with the Free tier; the Professional tier is a paid subscription upgrade.

## Configuration

**Settings → Tools → Terminal Command Recorder**

| Setting | Default | Description |
|---------|---------|-------------|
| Max stored items | 100 | Maximum number of records kept for the project. Persisted per project in `terminal-command-recorder.xml`. |

## Tool Windows

### Terminal Command Recorder
- **Location:** right panel
- **Content:** a scrollable list of saved records (shown as `title - content`) with a search field at the bottom that filters the list as you type.

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Open Terminal Command Recorder | Tools menu | Opens and focuses the Terminal Command Recorder tool window. |

## FAQ

**How do I open the recorder?**
Use **Tools → Open Terminal Command Recorder**, or click the **Terminal Command Recorder** tool window on the right edge of the IDE.

**How does search work?**
Type in the search box at the bottom of the tool window. Records are filtered case-insensitively by both their title and their command content as you type.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
