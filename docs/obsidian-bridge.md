# Obsidian IDE Bridge

> Bring your Obsidian vault into your JetBrains IDE — navigate wiki-links, backlinks, tags, and notes without leaving the editor.

## Overview

Obsidian IDE Bridge integrates one or more Obsidian vaults directly into JetBrains IDEs. It recognizes Obsidian `[[wiki-links]]`, shows backlinks for the current note, parses YAML frontmatter, searches your whole vault, and bridges `TODO`/`FIXME` comments in code to related notes. Vaults are indexed automatically when a project opens and kept current through VFS file watchers, so navigation and search stay in sync as your notes change.

It is aimed at developers who keep their engineering knowledge in Obsidian and want to reach it — and link code to it — without switching windows.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Obsidian IDE Bridge"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2+, JDK 17+. Works with IntelliJ IDEA, WebStorm, PyCharm, CLion, GoLand, PhpStorm, Rider, RubyMine, and Android Studio.

## Features

- **Wiki-link navigation and autocompletion** — jump through `[[note]]` links and autocomplete note titles inside `[[…]]`.
- **Backlinks panel** — see every note that links to the current one, with context preview.
- **Single and multi-vault support** — register one or several vaults.
- **Vault-wide full-text search** — search note contents and metadata across all vaults, with filter chips.
- **Frontmatter parsing** — read and display YAML frontmatter.
- **Interactive graph view** — notes as nodes, wiki-links as edges; click a node to open the note; traversal depth is configurable.
- **Code ↔ Notes bridging** — link `TODO`/`FIXME`/`HACK`/`NOTE` comments in code to Obsidian notes.
- **Tag tree navigation** — browse notes by hierarchical tags.
- **Daily notes** — open or create today's note in a single action.
- **Templates** — create notes from templates with variable substitution.
- **Editor & status bar integration** — wiki-link gutter icons in the editor, plus a status bar widget showing vault and note counts.

## Configuration

**Settings → Tools → Obsidian IDE Bridge**

| Setting | Default | Description |
|---------|---------|-------------|
| Vault Path | *(empty)* | Filesystem path to your Obsidian vault |
| Vault Name | `My Vault` | Display name for the vault |
| Graph Depth | `2` | Link-traversal depth for the graph view (1–10) |
| Show gutter icons | On | Show wiki-link gutter icons in the editor |

## Tool Windows

### Backlinks
- **Location:** right panel
- **Content:** notes that link to the current note, with a context preview

### Tags
- **Location:** left panel
- **Content:** hierarchical tag tree for browsing notes by tag

### Graph
- **Location:** bottom panel
- **Content:** interactive graph of notes (nodes) and wiki-links (edges); click a node to open it

## Actions

All actions live under **Tools → Obsidian IDE Bridge**.

| Action | Shortcut | Description |
|--------|----------|-------------|
| Search Vault | `Ctrl+Alt+O` (macOS `⌘⌥O`) | Search across all registered vaults |
| Open Daily Note | `Ctrl+Alt+D` (macOS `⌘⌥D`) | Open or create today's daily note |
| New Note | `Ctrl+Alt+N` (macOS `⌘⌥N`) | Create a new note from a template |
| Re-index Vault | — | Force re-index of all registered vaults |
| Vault Diagnostics | — | Show vault health and statistics |

## Supported File Types

- **Markdown (`.md`)** — Obsidian notes: wiki-links, frontmatter, and tags
- **Wiki-links (`[[note-name]]`)** — recognized in any file, including code comments, for code ↔ notes bridging
- **YAML frontmatter** — parsed from note headers

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
