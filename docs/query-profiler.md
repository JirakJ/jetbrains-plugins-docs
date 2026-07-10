# Query Profiler

> Profile and compare query execution snippets captured during development.

## Overview

Query Profiler adds a dedicated tool window to your JetBrains IDE for keeping the query snippets you capture while developing. Each snippet is stored as a named entry, and the tool window shows them in a single searchable list so you can find and review them without leaving the editor.

It is aimed at developers who work with database or query code and want a lightweight, in-IDE place to stash, search, and revisit query snippets. Everything runs with native JetBrains UI components and per-project settings.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Query Profiler"**
3. Click **Install** and restart the IDE

**Requirements:** Any IntelliJ-based JetBrains IDE, version 2023.2 or later.

## Features

Query Profiler is freemium: a free tier covers the core workflow, and a paid Professional subscription unlocks advanced capabilities.

### Free Tier

- **Query Profiler tool window** with a searchable catalog of captured query snippets
- **Live search** across snippet names and contents, case-insensitive
- Entries ordered with the most recently updated first
- Native JetBrains UI components
- Per-project configuration

### Professional Tier

- Advanced usage limits
- Snippet templates
- Export / import
- Team workflows

## Configuration

**Settings → Tools → Query Profiler**

| Setting | Default | Description |
|---------|---------|-------------|
| Max entries | 200 | Maximum number of query snippet entries kept in the catalog. |

Settings are stored per project.

## Tool Windows

### Query Profiler

- **Location:** right tool window bar
- **Content:** a scrollable list of captured query snippets (each shown as `name: snippet`) with a search box below it. Type in the box to filter the list live — matches are found in both the snippet name and its contents.

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Open Query Profiler | **Tools** menu | Opens and focuses the Query Profiler tool window. |

## FAQ

**How do I open the Query Profiler?**
Run **Tools → Open Query Profiler**, or click the **Query Profiler** tab on the right edge of the IDE.

**How does the search work?**
Type into the field at the bottom of the tool window. The list filters as you type, matching your text against both the name and the contents of each snippet, ignoring case.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
