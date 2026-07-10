# Git-Aware Dev Journal

> A development journal that links every note to its Git commit, branch, and file position.

## Overview

Git-Aware Dev Journal keeps a searchable log of the reasoning behind your code. Every entry is captured together with the commit hash, branch, and cursor position it belongs to, so the "why" behind a change stays attached to the code long after the diff scrolls out of view.

It is built for developers who want to stop losing decisions, TODOs, and blockers. Conventional commit messages can be turned into entries automatically, and a per-branch narrative reconstructs the story of your work.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Git-Aware Dev Journal"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2+, JDK 17+, a Git repository

## Features

Git-Aware Dev Journal is a freemium plugin: the core journaling features are free, while reporting, sync, sharing, and export belong to the paid tier.

### Free Tier
- **Git-linked notes** — every entry is auto-linked to the current commit hash, branch, and file position
- **Six entry types** — Notes, Decisions, TODOs, Blockers, Insights, and Questions
- **Auto-capture** — conventional commits (feat, fix, docs, refactor…) are parsed into journal entries
- **Branch narratives** — an auto-generated story of your work on each branch
- **Timeline view** — a chronological view of all entries with search and filters
- **Code hover context** — hover an annotated line to see why the code was written

### Professional Tier
- **Standup generator** — Markdown or Slack-formatted standup reports built from your journal
- **PR/MR summary generator** — pull-request descriptions assembled from journal entries
- **Unlimited notes**
- **Cross-device sync**
- **Team sharing** — share entries through the `.dev-journal/` directory in your repository
- **Export** — Markdown, JSON, and CSV

## Configuration

**Settings → Tools → Git-Aware Dev Journal**

| Setting | Default | Description |
|---------|---------|-------------|
| Auto-capture from conventional commits | On | Automatically create journal entries from conventional commit messages |
| Standup time window (hours) | `24` | How far back to look when generating standup summaries (range 1–168) |
| Journal directory | `.dev-journal` | Path, relative to the project root, where journal files are stored |

## Tool Windows

### Dev Journal
- **Location:** Bottom panel
- **Content:** Chronological timeline of journal entries with search and filters

## Actions

| Action | Location | Shortcut | Description |
|--------|----------|----------|-------------|
| Add Journal Entry | Tools menu; editor context menu | `Ctrl+Shift+J` | Add a development journal entry at the current cursor position |

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
