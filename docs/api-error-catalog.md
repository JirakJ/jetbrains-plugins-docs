# API Error Catalog

> A searchable, in-IDE catalog of API error codes and their handling branches across your codebase.

## Overview

API Error Catalog collects the API error codes and error-handling branches scattered across your project and surfaces them in a dedicated tool window. Instead of grepping for status codes and catch blocks, you browse the catalog and filter to the entry you need as you type.

It is built entirely on JetBrains-native UI components and keeps its state per project, so it works in any IntelliJ-based IDE regardless of the language you write in.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"API Error Catalog"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2+

## Features

### Free Tier
- Searchable catalog of API error codes and handling branches in a dedicated tool window
- Search-as-you-type filtering that matches both the error key and its description
- JetBrains-native UI components
- Project-level settings and state persistence

### Professional Tier (4.90/month)
- Advanced usage limits
- Templates
- Export / import
- Team workflows

## Configuration

**Settings → Tools → API Error Catalog**

| Setting | Default | Description |
|---------|---------|-------------|
| Max entries | 200 | Maximum number of catalog entries retained in the list. |

## Tool Windows

### API Error Catalog
- **Location:** right tool window panel
- **Content:** the collected catalog entries, listed as `key: value`. A search field at the bottom filters the list live as you type, matching against both the error code and its description.

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Open API Error Catalog | **Tools → Open API Error Catalog** | Opens (or focuses) the API Error Catalog tool window. |

## FAQ

**Which IDEs and languages are supported?**
The plugin depends only on the IntelliJ platform, so it runs in any JetBrains IDE and is not tied to a specific language.

**Are catalog entries and settings shared between projects?**
No. State and settings are stored per project, so each project keeps its own catalog and configuration.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
