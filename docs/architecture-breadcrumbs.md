# Architecture Breadcrumbs

> Embed architecture decisions, patterns, and constraints as breadcrumbs that live next to the code they describe.

**Free & open source** — source: https://github.com/JirakJ/architecture-breadcrumbs (Apache-2.0); contributions welcome.

## Overview

Architecture Breadcrumbs keeps architectural knowledge where it belongs — in your codebase. Instead of decisions decaying in wiki pages, chat threads, or the heads of people who have moved on, you attach short, categorized notes (breadcrumbs) to the exact line they explain: why an approach was chosen, which pattern is in play, what constraint applies, or what still needs attention.

Breadcrumbs are stored in `.arch-breadcrumbs.json` at the project root, so they are versioned with your code and shared with your team through Git. Each breadcrumb records an author and can link to related breadcrumbs elsewhere in the project.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Architecture Breadcrumbs"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.2+.

## Features

### Capture context
- Add a breadcrumb on the current line and set its **text**, **category**, **author**, and optional **links** to other breadcrumbs.
- Six categories: **Decision**, **Pattern**, **Constraint**, **TODO (Architecture)**, **Warning**, and **Context**.
- Everything is stored in `.arch-breadcrumbs.json` — versioned with the project, no external service required.

### In the editor
- A **gutter icon** marks every breadcrumbed line, with the note as its tooltip.
- Gutter icons can be turned off entirely or per category.
- Works in any file type.

### Browse and navigate
- The **Architecture Breadcrumbs** tool window lists every breadcrumb in a table with a category filter and full-text search; double-click a row to jump to the line.
- **Navigate Linked Breadcrumbs** jumps to the breadcrumbs linked from the one at the caret, or lets you pick from all breadcrumbs.

## Configuration

**Settings → Tools → Architecture Breadcrumbs**

| Setting | Default | Description |
|---------|---------|-------------|
| Enable Architecture Breadcrumbs | On | Turns gutter icons and the add/navigate actions on or off |
| Show gutter icons | On | Display an icon in the editor gutter for each breadcrumb |
| Gutter Icons per Category | All on | Per-category toggles for Decision, Pattern, Constraint, TODO (Architecture), Warning, and Context |

## Tool Windows

### Architecture Breadcrumbs
- **Location:** Bottom panel
- **Content:** A searchable, category-filterable table of every breadcrumb in the project. Double-click to navigate. Empty until you add your first breadcrumb.

## Actions

| Action | Location | Shortcut | Description |
|--------|----------|----------|-------------|
| Add Architecture Breadcrumb | Editor context menu | `Ctrl+Shift+B` | Add a breadcrumb annotation at the current line |
| Navigate Linked Breadcrumbs | Navigate (Go To) menu | — | Jump to linked breadcrumbs, or pick from all breadcrumbs |

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
