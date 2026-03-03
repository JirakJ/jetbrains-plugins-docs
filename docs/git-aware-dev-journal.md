# Git-Aware Dev Journal

> Automatic developer journaling linked to your Git activity.

## Overview

Git-Aware Dev Journal automatically creates and maintains a developer journal tied to your Git commits, branches, and work sessions. It generates daily summaries, tracks time spent on features, and creates standup-ready reports from your actual development activity.

## Installation

1. Go to **Settings → Plugins → Marketplace**
2. Search for **"Git-Aware Dev Journal"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.3+, Java 17+, Git

## Features

### Free Tier
- Automatic journal entries from Git commits
- Daily activity summary
- Branch-based work session tracking
- Manual note additions to journal entries
- Last 7 days of journal history

### Pro Tier
- Unlimited journal history
- Standup report generation (yesterday/today/blockers)
- Time tracking per branch/feature
- Weekly/monthly summary generation
- Markdown export
- Team activity overview (shared repository)
- Custom journal templates
- Integration with project management tools
- Search and filter journal entries

## Configuration

### Settings Location
**Settings → Tools → Git-Aware Dev Journal**

| Setting | Default | Description |
|---------|---------|-------------|
| Auto-journal commits | `true` | Create entries from Git commits |
| Journal directory | `.dev-journal` | Storage location (project root) |
| Include diff stats | `true` | Include file change stats in entries |
| Time tracking | `true` | Track time per branch |
| Standup format | Default | Template for standup reports |

## Tool Windows

### Dev Journal
- **Location:** Right panel
- **Content:** Chronological journal entries, daily summaries, search bar
- **Actions:** Add manual note, generate standup, export week, search entries

## Actions

| Action | Shortcut | Description |
|--------|----------|-------------|
| Add Journal Note | `Alt+J` | Add manual note to today's journal |
| Generate Standup | — | Create standup report from recent activity |
| Export Journal | — | Export journal entries as Markdown |

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
