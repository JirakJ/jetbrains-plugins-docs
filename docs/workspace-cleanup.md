# Workspace Cleanup

> Find and remove workspace bloat safely to reclaim disk space.

## Overview

Workspace Cleanup scans your project for the files that quietly consume disk space — build outputs, caches, logs, temp files, dependency folders, and IDE-generated artifacts — and shows exactly how much each category is costing you. Review the detected candidates in a dedicated tool window and reclaim space with one click, either selectively per item or with a full Deep Clean.

It recognizes artifacts from common toolchains, including Gradle, Maven, npm, pip, and pytest, and keeps a running tally of how much space you have reclaimed over time.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Workspace Cleanup"**
3. Click **Install** and restart the IDE

**Requirements:** IntelliJ-based IDE 2023.2+ (works in any IntelliJ-platform IDE)

## Features

Workspace Cleanup is freemium: workspace scanning and build-artifact cleanup are free, with a paid Professional upgrade that unlocks full-category cleanup, custom rules, and automation.

### Free Tier
- Workspace scan that detects build outputs, caches, logs, temp files, dependencies, and IDE artifacts
- Category breakdown showing reclaimable size per category
- Build-artifact cleanup

### Professional Tier
- Full-category cleanup across all categories, plus one-click Deep Clean
- Custom cleanup rules and protected paths
- Scheduled auto-scan on a configurable interval
- Cleanup history and reclaimed-space analytics

### Detected categories
- **Build Artifacts** — compiled outputs, build directories, and distribution folders
- **Caches** — build tool, package manager, and bytecode caches
- **Log Files** — application, build, and debug output files
- **Temporary Files** — backup files, swap files, and other temporary artifacts
- **Dependencies** — downloaded dependency directories such as `node_modules` and virtual environments
- **IDE Artifacts** — IDE-generated workspace files and caches

## Configuration

**Settings → Tools → Workspace Cleanup**

| Setting | Default | Description |
|---------|---------|-------------|
| Enabled categories | All enabled | Categories included in scans and cleanup (Build Artifacts, Caches, Log Files, Temporary Files, Dependencies, IDE Artifacts) |
| Enable auto-scan | Off | Periodically rescan the workspace in the background |
| Scan interval (minutes) | 60 | How often auto-scan runs (1–1440) |
| Show notifications after scan/clean | On | Show a balloon summary after each scan or cleanup |
| Confirm before cleaning | On | Ask for confirmation before deleting anything |
| Additional protected paths | (none) | Comma-separated paths that are never cleaned |

## Tool Windows

### Workspace Cleanup
- **Location:** bottom panel
- **Content:** a category-by-category breakdown of reclaimable space, the list of detected cleanup candidates, and controls to select items and run cleanup or a Deep Clean.

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Scan Workspace | Tools menu | Scan the workspace for cleanup candidates and populate the dashboard |
| Deep Clean Workspace | Tools menu | Remove all detected build artifacts and caches in one operation |

## FAQ

**Will it delete files without asking?**
No. With **Confirm before cleaning** enabled (the default), the plugin prompts before removing anything, and you can review and select individual candidates in the tool window first.

**How do I stop a folder from being cleaned?**
Add it to **Additional protected paths** in Settings → Tools → Workspace Cleanup as a comma-separated list. Protected paths are always excluded from cleanup.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
