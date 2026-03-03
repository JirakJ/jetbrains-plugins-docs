# ADR Companion

> Architecture Decision Records management directly in your JetBrains IDE.

## Overview

ADR Companion helps development teams create, manage, and navigate Architecture Decision Records (ADRs) without leaving the IDE. It provides templates, status tracking, cross-referencing between ADRs, and integration with your project's documentation workflow.

## Installation

1. Go to **Settings → Plugins → Marketplace**
2. Search for **"ADR Companion"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.3+, Java 17+

## Features

### Free Tier
- Create new ADRs from templates (MADR, Nygard, custom)
- ADR index view with status overview
- Basic status management (Proposed, Accepted, Deprecated, Superseded)
- ADR file navigation (`.md` files in `docs/adr/` or configurable directory)
- Syntax highlighting for ADR metadata

### Pro Tier
- Cross-reference linking between ADRs (supersedes/superseded-by)
- ADR search and filtering by status, date, author
- Relationship graph visualization
- Export to Confluence/Wiki formats
- ADR health checks (stale decisions, missing statuses)
- Template customization
- Git blame integration (who decided what, when)

## Configuration

### Settings Location
**Settings → Tools → ADR Companion**

| Setting | Default | Description |
|---------|---------|-------------|
| ADR Directory | `docs/adr` | Directory for ADR files (relative to project root) |
| Template | MADR | Default ADR template format |
| Auto-number | `true` | Automatically number new ADRs |
| Date format | `yyyy-MM-dd` | Date format for ADR headers |
| Status values | Proposed, Accepted, Deprecated, Superseded | Configurable status options |

## Tool Windows

### ADR Explorer
- **Location:** Right panel
- **Content:** Hierarchical list of all ADRs with status icons, search bar, and quick-create button
- **Actions:** Create new ADR, change status, view relationships

## Actions

| Action | Shortcut | Description |
|--------|----------|-------------|
| New ADR | `Ctrl+Alt+N` | Create a new ADR from template |
| ADR Index | — | Open ADR explorer panel |
| Change Status | — | Update ADR status (context menu) |

## Supported File Types

- Markdown (`.md`) — ADR content files
- ADR index files (auto-generated)

## FAQ

**Q: Where are ADRs stored?**
A: In your project directory (default: `docs/adr/`), tracked by version control.

**Q: Can I customize the ADR template?**
A: Yes. Create a `.adr-template.md` in your ADR directory or use the settings panel.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
