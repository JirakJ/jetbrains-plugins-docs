# Git-Aware Dev Journal

> A development journal that links every note to its Git commit, branch, and file position.

**Free & open source** — source: https://github.com/JirakJ/git-aware-dev-journal (Apache-2.0); contributions welcome.

## Overview

Git-Aware Dev Journal keeps a searchable log of the reasoning behind your code. Every entry is captured together with the current branch, HEAD commit, file, and line it belongs to, so the "why" behind a change stays attached to the code long after the diff scrolls out of view.

It is built for developers who want to stop losing decisions, TODOs, and blockers. Entries are stored as plain JSON in your project, and the tool window can copy a Markdown standup or a per-branch summary to the clipboard.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Git-Aware Dev Journal"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2+. The bundled Git plugin is optional and enables branch and commit capture.

## Features

- **Git-linked entries** — each entry records the current branch and HEAD commit (when the Git plugin is present) plus file and line
- **Six entry types** — Notes, Decisions, TODOs, Blockers, Insights, and Questions, with tags
- **Dev Journal tool window** — sortable table with a branch filter and text/tag search
- **Copy Standup** — Markdown standup of recent entries (configurable time window)
- **Copy Branch Summary** — all entries on the selected branch, grouped by type
- **Plain JSON storage** — `.dev-journal/entries.json` in your project, easy to commit and share

## Configuration

**Settings → Tools → Git-Aware Dev Journal**

| Setting | Default | Description |
|---------|---------|-------------|
| Standup time window (hours) | `24` | How far back the **Copy Standup** button looks (range 1–168) |
| Journal directory | `.dev-journal` | Relative to the project root, or absolute. Takes effect after reopening the project. |

## Tool Windows

### Dev Journal
- **Location:** Bottom panel (secondary)
- **Content:** Table of entries with **Type**, **Entry**, **Branch**, **Commit**, **File**, **Timestamp**, and **Tags** columns, a branch filter, a search field, and **Add Entry**, **Copy Standup**, and **Copy Branch Summary** buttons.

## Actions

| Action | Location | Shortcut | Description |
|--------|----------|----------|-------------|
| Add Journal Entry | Tools menu; editor context menu | `Ctrl+Shift+J` | Add a development journal entry at the current cursor position |

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
