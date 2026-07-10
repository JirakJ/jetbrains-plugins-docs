# Architecture Breadcrumbs

> Embed architecture decisions, patterns, and constraints as breadcrumbs that live next to the code they describe.

## Overview

Architecture Breadcrumbs keeps architectural knowledge where it belongs — in your codebase. Instead of decisions decaying in wiki pages, chat threads, or the heads of people who have moved on, you attach short, categorized notes (breadcrumbs) to the exact line they explain: why an approach was chosen, which pattern is in play, what constraint applies, or what still needs attention.

Breadcrumbs are stored in a project-local `.arch-breadcrumbs.json` file, so they are versioned with your code, shared through Git, and visible to everyone on the team. Each breadcrumb records an author and can be linked to related breadcrumbs elsewhere in the project.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Architecture Breadcrumbs"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.3+, JDK 21+. Optional: the bundled **Git4Idea** plugin for VCS integration.

## Features

### Capture context
- Add a breadcrumb on the current line and set its **text**, **category**, **author**, and optional **links** to related breadcrumbs.
- Six categories: **Decision**, **Pattern**, **Constraint**, **TODO (Architecture)**, **Warning**, and **Context**.
- Everything is stored in `.arch-breadcrumbs.json` — versioned with the project, no external files or sync tools required.

### In the editor
- Color-coded **gutter icons** mark every breadcrumbed line.
- Choose the gutter icon style: **Default**, **Minimal**, or **Colorful**.
- Turn individual categories on or off.

### Browse and navigate
- The **Architecture Breadcrumbs** tool window lists every breadcrumb with **Category**, **Text**, **File**, **Line**, and **Author** columns; search by text and filter by category.
- **Navigate Linked Breadcrumbs** jumps between breadcrumbs you have linked together.

### Team and VCS
- `.arch-breadcrumbs.json` is designed for Git sharing, and every breadcrumb records its author.
- Optional Git4Idea integration adds VCS context.

## Configuration

**Settings → Tools → Architecture Breadcrumbs**

| Setting | Default | Description |
|---------|---------|-------------|
| Enable Architecture Breadcrumbs | On | Toggle all breadcrumb annotations on or off |
| Show gutter icons | On | Display an icon in the editor gutter for each breadcrumb |
| Icon style | Default | Gutter icon style: Default, Minimal, or Colorful |
| Breadcrumb categories | All on | Per-category toggles for Decision, Pattern, Constraint, TODO (Architecture), Warning, and Context |

## Tool Windows

### Architecture Breadcrumbs
- **Location:** Bottom panel
- **Content:** A searchable, category-filterable list of every breadcrumb in the project (Category, Text, File, Line, Author). Empty until you add your first breadcrumb.

## Actions

| Action | Location | Shortcut | Description |
|--------|----------|----------|-------------|
| Add Architecture Breadcrumb | Editor context menu | Ctrl+Shift+B | Add a breadcrumb annotation at the current line |
| Navigate Linked Breadcrumbs | Navigate (Go To) menu | — | Jump between linked breadcrumbs |

## Supported Languages

Java, Kotlin, Python, JavaScript/TypeScript, and Go.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
