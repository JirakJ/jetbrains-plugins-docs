# Runbook Quick Access

> Index and open operational runbooks from the IDE with instant search.

## Overview

Runbook Quick Access adds a right-hand tool window that keeps your operational runbooks one click away. Records appear in a scrollable list and are filtered live as you type in the search box, so you can find the right procedure without leaving the editor.

It is aimed at developers and operators who keep frequently used notes, checklists, or runbooks alongside their work and want to reach them from inside the IDE.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Runbook Quick Access"**
3. Click **Install** and restart the IDE

**Requirements:** Any JetBrains IDE 2023.2 or later (depends only on the IntelliJ platform, so it runs in every IntelliJ-based IDE).

Runbook Quick Access is distributed as a freemium plugin: it is free to install, with an optional paid license.

## Features

- **Runbook tool window** docked on the right edge of the IDE, listing your runbook records.
- **Instant search** — a filter field at the bottom of the tool window narrows the list as you type, matching on both the record title and its content (case-insensitive).
- **Open from the Tools menu** — the *Open Runbook Quick Access* action brings the tool window to the front from anywhere in the IDE.
- **Project-scoped settings** persisted per project.

## Configuration

**Settings → Tools → Runbook Quick Access**

The settings page exposes a single **Max stored items** field (default `100`), the maximum number of runbook records to retain per project.

## Tool Windows

### Runbook Quick Access
- **Location:** right tool-window panel
- **Content:** a searchable list of runbook records. Type in the field at the bottom to filter the list by title or content.

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Open Runbook Quick Access | Tools menu | Reveals and focuses the Runbook Quick Access tool window. |

## FAQ

**Where does the tool window appear?**
On the right side of the IDE. If it is hidden, run **Tools → Open Runbook Quick Access** or click the *Runbook Quick Access* stripe button on the right.

**Do I need a paid license?**
No. The plugin installs and runs for free; a paid license is optional.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
