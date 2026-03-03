# Obsidian Bridge

> Seamlessly connect your JetBrains IDE with your Obsidian knowledge vault.

## Overview

Obsidian Bridge creates a two-way connection between your JetBrains IDE and Obsidian, enabling developers to link code to knowledge base notes, create notes from code context, and navigate between IDE and Obsidian seamlessly. It supports Obsidian's wiki-link syntax, frontmatter, and vault structure.

## Installation

1. Go to **Settings → Plugins → Marketplace**
2. Search for **"Obsidian Bridge"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.3+, Java 17+, Obsidian installed (optional but recommended)

## Features

### Free Tier
- Obsidian vault browser in IDE
- Create notes from code context (right-click → "Create Obsidian Note")
- Wiki-link syntax highlighting in Markdown files
- Navigate to Obsidian notes from code comments (`[[note-name]]`)
- Basic vault search

### Pro Tier
- Two-way link synchronization
- Code snippet embedding in notes (auto-updating)
- Daily notes integration with development activity
- Tag-based navigation between code and notes
- Frontmatter metadata from project context
- ADR/documentation template integration
- Knowledge graph visualization (code ↔ notes)
- Bulk note creation from project structure
- Obsidian URI scheme support (open notes in Obsidian app)

## Configuration

### Settings Location
**Settings → Tools → Obsidian Bridge**

| Setting | Default | Description |
|---------|---------|-------------|
| Vault path | *(empty)* | Path to Obsidian vault directory |
| Note template | Default | Template for new notes |
| Link format | Wiki-link | Link syntax (`[[wiki]]` or `[markdown]()`) |
| Auto-create daily | `false` | Create daily dev note on IDE open |
| Tag prefix | `dev/` | Prefix for auto-generated tags |

## Tool Windows

### Obsidian Vault
- **Location:** Right panel
- **Content:** Vault file tree, search bar, recent notes, linked notes
- **Actions:** Create note, open in Obsidian, search vault, view backlinks

## Actions

| Action | Shortcut | Description |
|--------|----------|-------------|
| Create Obsidian Note | `Ctrl+Alt+O` | Create note from current code context |
| Open in Obsidian | — | Open linked note in Obsidian app |
| Search Vault | — | Full-text search across Obsidian vault |

## Supported File Types

- Markdown (`.md`) — Obsidian notes
- Wiki-links (`[[note-name]]`) in code comments
- Frontmatter (YAML metadata)

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
