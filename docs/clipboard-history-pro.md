# Clipboard History Pro

> Searchable, persistent clipboard history with pinning, auto-categorization, and code-aware transformations.

## Overview

Clipboard History Pro turns the IDE's single-slot clipboard into a searchable history that survives restarts. Every text you copy is captured, classified by content type, and kept so you can find and reuse an earlier snippet instead of copying it again. Entries can be pinned, filtered by category, and run through built-in text and code transformations before you paste.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Clipboard History Pro"**
3. Click **Install** and restart the IDE

**Requirements:** Any IntelliJ-based IDE, version 2023.2 or later.

## Features

Clipboard History Pro is freemium: automatic capture and search are free, and a Professional tier unlocks the power features.

### Free Tier
- Automatic clipboard capture into a browsable history
- Full-text search across all captured entries

### Professional Tier
- Unlimited history retention
- Pin favorites so frequently used snippets are never evicted
- Advanced text and code transformations
- Category filters
- Export

The Professional tier is a paid upgrade ($2.90/month).

### Auto-categorization
Captured entries are classified automatically as **Code**, **JSON**, **XML**, **URL**, **File Path**, or **Text**, so you can scan and filter the history by content type.

### Transformations
**Paste Transformed** opens a chooser, applies the selected transformation to the current clipboard content, and pastes the result in one step. Available transformations:

- **Case:** UPPER CASE, lower case, camelCase, snake_case, kebab-case, PascalCase
- **Escape / unescape:** JSON, HTML, XML
- **Encode / decode:** URL, Base64
- **Lines:** trim lines, remove empty lines, sort, reverse, keep unique, add line numbers

## Configuration

**Settings → Tools → Clipboard History Pro**

| Setting | Default | Description |
|---------|---------|-------------|
| Max clipboard entries | 200 | Maximum number of entries to retain in history. |
| Polling interval (ms) | 500 | How often the system clipboard is checked for new content. |
| Auto-categorize entries | Enabled | Automatically detect each entry's content category. |
| Excluded sources (comma-separated) | *(empty)* | Sources to skip when capturing clipboard content. |

## Tool Windows

### Clipboard Pro
- **Location:** Right panel (open via **View → Tool Windows → Clipboard Pro**).
- **Content:** A searchable list of captured clipboard entries. Each entry shows a preview, its detected category, and whether it is pinned. From here you can search the history, pin or unpin entries, delete individual entries, or clear the whole list.

## Actions

| Action | Location | Shortcut | Description |
|--------|----------|----------|-------------|
| Show Clipboard History | Edit menu | Ctrl+Shift+V | Opens the Clipboard Pro history panel. |
| Paste Transformed | Edit menu | — | Applies a transformation to clipboard content and pastes it in one step. |

## FAQ

**Does my clipboard history survive IDE restarts?**
Yes. History is persisted and reloaded automatically the next time the IDE starts.

**How do I keep an important snippet from being pushed out of history?**
Pin it. Pinned entries are protected from eviction when the history reaches its size limit.

**Can I stop certain sources from being captured?**
Yes. Add them to **Excluded sources** in Settings → Tools → Clipboard History Pro.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
