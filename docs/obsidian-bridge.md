# Obsidian IDE Bridge

> Bring your Obsidian vault into your JetBrains IDE — complete and follow wiki-links, see backlinks, browse tags and the link graph, and search your notes without leaving the editor.

**Free & open source** — source: https://github.com/JirakJ/obsidian-bridge (Apache-2.0); contributions welcome.

## Overview

Obsidian IDE Bridge connects an Obsidian vault to your JetBrains IDE. The vault's Markdown notes are indexed when a project opens and kept up to date as files are created, edited, renamed, moved, or deleted. From there you get `[[wiki-link]]` completion in any file, gutter icons on code comments that link to notes, backlinks, a tag tree, a link graph, and full-text search.

It is aimed at developers who keep their engineering knowledge in Obsidian and want to reach it — and link code to it — without switching windows.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Obsidian IDE Bridge"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2+. Works with IntelliJ IDEA, WebStorm, PyCharm, CLion, GoLand, PhpStorm, Rider, RubyMine, and Android Studio.

## Features

- **Vault index** — Markdown notes are indexed on project open and kept current as vault files change (`.obsidian/` and `.trash/` are skipped).
- **`[[wiki-link]]` completion** — note titles are suggested after `[[` in any file.
- **Code comment links** — a gutter icon on code comments containing `[[Note]]` opens the linked note (can be turned off in Settings).
- **Backlinks** — notes that link to the note open in the editor; double-click to open one.
- **Tags** — tags from frontmatter and inline `#tags`, nested by `/` (for example `project/alpha`), with note counts.
- **Graph** — notes and resolved links; click a node to open the note.
- **Search Vault** — full-text search over titles, aliases, tags, paths, and note content.
- **Frontmatter parsing** — title, aliases, and tags.
- **Daily note and new note** — open or create today's daily note, or create a new note and open it.
- **Status bar widget** — shows the vault and note count.

Links resolve like in Obsidian: explicit paths first, then note name or alias; for duplicate names the note in the same folder wins, otherwise the shallowest path.

## Configuration

**Settings → Tools → Obsidian IDE Bridge**

| Setting | Default | Description |
|---------|---------|-------------|
| Vault path | *(empty)* | Filesystem path to your Obsidian vault (must contain a `.obsidian/` folder) |
| Vault name | *(folder name)* | Display name for the vault |
| Show gutter icons for [[wiki-links]] in code comments | On | Show the gutter icon that opens a linked note |

Additional vaults can be added to `obsidian-bridge.xml` in the IDE configuration directory; they are indexed too.

## Tool Windows

### Backlinks
- **Location:** Right panel (secondary)
- **Content:** Notes that link to the note open in the editor

### Tags
- **Location:** Left panel (secondary)
- **Content:** Nested tag tree with note counts

### Graph
- **Location:** Bottom panel
- **Content:** Graph of notes (nodes) and resolved wiki-links (edges); click a node to open it

## Actions

All actions live under **Tools → Obsidian IDE Bridge**.

| Action | Shortcut | Description |
|--------|----------|-------------|
| Search Vault | `Ctrl+Alt+O` (macOS `⌘⌥O`) | Search across all registered vaults |
| Open Daily Note | `Ctrl+Alt+D` (macOS `⌘⌥D`) | Open or create today's daily note |
| New Note | `Ctrl+Alt+N` (macOS `⌘⌥N`) | Create a new note in the vault and open it |
| Re-index Vault | — | Force re-index of all registered vaults |
| Vault Diagnostics | — | Show vault health and statistics |

## Supported File Types

- **Markdown (`.md`)** — Obsidian notes: wiki-links, frontmatter, and tags
- **Wiki-links (`[[note-name]]`)** — completed in any file and linked from code comments

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
