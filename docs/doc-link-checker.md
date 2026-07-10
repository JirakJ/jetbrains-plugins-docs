# Doc Link Checker

> Validate internal project documentation links and jump to broken references instantly.

## Overview

Doc Link Checker helps you keep the internal links in your project documentation healthy without leaving the IDE. It surfaces documentation entries in a dedicated tool window so you can find a reference and navigate to it in a couple of keystrokes.

The panel keeps a searchable catalog of entries and filters it live as you type, so locating a specific link or reference stays fast even in large projects. It is aimed at developers who maintain README files, docs folders, and other in-repo documentation and want a quick way to spot and reach the references that matter.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Doc Link Checker"**
3. Click **Install** and restart the IDE

**Requirements:** IntelliJ-based IDE 2023.2+

## Features

### Free Tier
- Documentation catalog tool window with a live, case-insensitive filter
- Quick navigation: results narrow as you type in the search field
- JetBrains-native UI that follows the active IDE theme
- Project-level settings that persist with the project
- Open the panel from the **Tools** menu or the right-hand tool window
- Available during indexing (dumb-aware)

### Professional Tier
- Advanced usage limits
- Templates
- Export / import
- Team workflows

## Configuration

**Settings → Tools → Doc Link Checker**

| Setting | Default | Description |
|---------|---------|-------------|
| Max entries | 200 | Maximum number of documentation entries kept in the catalog |

## Tool Windows

### Doc Link Checker
- **Location:** Right panel
- **Content:** A searchable list of documentation entries with a filter field at the bottom. The list updates live as you type, matching on both the entry name and its content.

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Open Doc Link Checker | Tools menu | Shows the Doc Link Checker tool window |

## FAQ

**How do I open the panel?**
Use **Tools → Open Doc Link Checker**, or click the **Doc Link Checker** tab on the right edge of the IDE.

**How does search work?**
Type in the field at the bottom of the panel. Entries are filtered instantly by a case-insensitive match against both the entry name and its content.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
