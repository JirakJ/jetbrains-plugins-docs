# Structurizr DSL

> Enterprise-grade Structurizr DSL and C4 model support for JetBrains IDEs.

## Overview

The Structurizr DSL plugin brings full language support for Structurizr DSL to all JetBrains IDEs, enabling developers to write **C4 model architecture diagrams as code** (`.dsl` files) with syntax highlighting, intelligent completion, 9 inspections with quick-fixes, 16 live templates, navigation, validation, and live diagram preview.

## Installation

1. Go to **Settings → Plugins → Marketplace**
2. Search for **"Structurizr DSL"**
3. Click **Install** and restart the IDE

**Requirements:** Any JetBrains IDE 2023.2+

## Quick Start

1. Create a new file with `.dsl` extension
2. Type `ws` and press `Tab` to expand the workspace template
3. Use `Ctrl+Space` for code completion
4. Open **View → Tool Windows → Structurizr Preview** for live diagrams (Pro)

## Features

### Free Tier
- Full custom language (lexer, parser, PSI tree)
- Syntax highlighting (19 configurable color attributes)
- Code completion (keywords, identifiers, tags, style properties)
- 9 inspections with quick-fixes
- 16 live templates
- Go to Definition (`Ctrl+Click`)
- Find Usages (`Alt+F7`)
- Go to Symbol (`Ctrl+Alt+Shift+N`)
- Structure View (hierarchical tree)
- Breadcrumbs navigation
- Code formatting (`Ctrl+Alt+L`)
- Code folding
- Line markers (gutter icons for elements)
- Comment/uncomment (`Ctrl+/`)
- Brace matching
- Hover documentation (`Ctrl+Q`)
- Rename refactoring (`Shift+F6`)
- `!include` file navigation

### Pro Tier
- Live diagram preview (real-time C4 rendering)
- Split editor (code + diagram side-by-side)
- Export: SVG, PNG, PlantUML, Mermaid, DOT, JSON
- Copy to clipboard: SVG, PNG, PlantUML, Mermaid, Image
- Structurizr CLI integration (auto-download)
- Dark mode toggle for preview
- Configurable zoom and refresh delay

## Live Templates

| Shortcut | Description |
|----------|-------------|
| `ws` | Full workspace with model and views |
| `per` | Person definition |
| `ss` | Software system |
| `con` | Container with technology |
| `comp` | Component definition |
| `rel` | Relationship (`->`) |
| `dep` | Deployment environment with node |
| `sv` | System context view |
| `cv` | Container view |
| `sty` | Styles block |
| `depenv` | Deployment environment |
| `depnode` | Deployment node |
| `dynview` | Dynamic view |
| `filtview` | Filtered view |
| `infnode` | Infrastructure node |
| `inc` | !include directive |

## Inspections

| Inspection | Level | Quick Fix |
|-----------|-------|-----------|
| Undefined Reference | ERROR | Create missing element |
| Unused Element | WEAK WARNING | Remove unused element |
| Duplicate Identifier | ERROR | Rename element |
| Empty Block | WEAK WARNING | Remove empty block |
| Missing Required Property | ERROR | Add required property |
| Deprecated Keyword | WARNING | Update to new syntax |
| Invalid Color Value | ERROR | Suggest valid format |
| Invalid Element Context | ERROR | Move to correct parent |
| Invalid Relationship | ERROR | Remove/correct relationship |

## Configuration

### Global Settings
**Settings → Tools → Structurizr DSL**

| Setting | Default | Description |
|---------|---------|-------------|
| Use embedded CLI | `true` | Use built-in Structurizr CLI |
| CLI timeout (s) | `30` | CLI execution timeout |
| Live preview | `true` | Enable live diagram preview |
| Auto-refresh | `true` | Refresh preview on file change |
| Preview delay (ms) | `500` | Delay before preview refresh |
| Default export format | PNG | Default export format |
| Export dimensions | 1920×1080 | Export image size |
| Show breadcrumbs | `true` | Navigation breadcrumbs |
| Code folding | `true` | Enable code folding |
| Line markers | `true` | Gutter icons for elements |

### Project Settings
**Settings → Tools → Structurizr DSL → Project Settings**

| Setting | Description |
|---------|-------------|
| Project CLI path | Override global CLI path |
| Default workspace file | Default `.dsl` file to open |
| Export directory | Project-specific export location |

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl+Space` | Code completion |
| `Ctrl+Click` / `Ctrl+B` | Go to definition |
| `Alt+F7` | Find usages |
| `Ctrl+Alt+L` | Format code |
| `Ctrl+/` | Comment/uncomment line |
| `Ctrl+Alt+Shift+N` | Go to symbol |
| `Ctrl+Shift+R` | Refresh preview |
| `Shift+F6` | Rename refactoring |
| `Ctrl+Q` | Quick documentation |

## Tool Windows

### Structurizr Preview
- **Location:** Right panel
- **Content:** Live C4 diagram, zoom controls, export buttons
- **Features:** Dark mode, system theme integration, auto-refresh

## Supported C4 Keywords

- **Model:** `workspace`, `model`, `person`, `softwareSystem`, `container`, `component`, `group`
- **Deployment:** `deploymentEnvironment`, `deploymentNode`, `infrastructureNode`, `softwareSystemInstance`, `containerInstance`
- **Views:** `systemLandscape`, `systemContext`, `container`, `component`, `filtered`, `dynamic`, `deployment`, `custom`
- **Directives:** `!include`, `!identifiers`, `!impliedRelationships`, `!const`, `!var`, `!docs`, `!adrs`, `!script`

## External Integrations

- **Structurizr CLI** — Diagram rendering and validation
- **PlantUML** — Export as PlantUML syntax
- **Mermaid** — Export as Mermaid syntax
- **C4 Model** — Full C4 diagram support

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
