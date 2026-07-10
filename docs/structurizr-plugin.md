# Structurizr DSL

> Full language support and live C4 diagram preview for Structurizr DSL in JetBrains IDEs.

## Overview

Structurizr DSL brings complete language support for [Structurizr DSL](https://docs.structurizr.com/dsl/language) — the text-based language for describing software architecture with the [C4 model](https://c4model.com/) — to any JetBrains IDE. You author `.dsl` files with syntax highlighting, context-aware completion, inspections, navigation, and refactoring, then render the resulting C4 diagrams live inside the IDE and export them to common formats.

It is aimed at developers and architects who keep their architecture "as code" alongside the source it describes.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Structurizr DSL"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.3+ (IntelliJ IDEA, WebStorm, PyCharm, GoLand, CLion, Rider, and the rest of the family) on Windows, macOS, or Linux.

## Quick Start

1. Create a file with a `.dsl` extension.
2. Type `ws` and press **Tab** to scaffold a workspace with `model` and `views` blocks.
3. Press **Ctrl+Space** for context-aware completion; **Ctrl+Click** jumps to element definitions.
4. Open the **Structurizr Preview** tool window (or the split editor) to watch the C4 diagram render as you type.

## Features

Structurizr DSL is freemium: the full authoring, navigation, and analysis language support is free. A Professional license unlocks live diagram preview, the split editor, file export, and CLI integration.

### Free

- Full Structurizr DSL language: lexer, parser, and PSI for `.dsl` files
- Syntax highlighting with a configurable color scheme, including `${...}` variable-substitution highlighting
- Context-aware code completion for keywords, elements, relationships, views, and properties, with smart relationship-target completion after `->` (suggests only defined elements, excluding the source)
- 21 live templates
- 10 code inspections with quick fixes
- Color preview swatches in the gutter with a built-in color picker
- Code folding, formatting (**Ctrl+Alt+L**), brace matching, comment/uncomment (**Ctrl+/**), and quote handling
- Navigation: Go to Definition (**Ctrl+Click**), Find Usages (**Alt+F7**), Go to Symbol (**Ctrl+Alt+Shift+N**), Structure View, breadcrumbs, line markers, and `!include` file navigation
- Rename refactoring (**Shift+F6**) across all references
- Quick documentation on hover (**Ctrl+Q**)
- Copy the rendered diagram to the clipboard as SVG, PlantUML, Mermaid, or image

### Professional

- Live diagram preview — real-time C4 rendering as you edit
- Split editor — DSL code and diagram side by side
- Export diagrams to file: SVG, PNG, PlantUML, Mermaid, DOT, or JSON
- Structurizr CLI integration — auto-download and manage the CLI used for rendering

## Live Templates

Type the shortcut and press **Tab** to expand.

| Shortcut | Expands to |
|----------|------------|
| `ws` | Workspace with model and views |
| `per` | Person definition |
| `ss` | Software System definition |
| `con` | Container definition |
| `comp` | Component definition |
| `rel` | Relationship (`->`) |
| `dep` | Deployment environment with a node |
| `sv` | System Context view |
| `cv` | Container view |
| `sty` | Styles block |
| `depenv` | Deployment Environment |
| `depnode` | Deployment Node |
| `dynview` | Dynamic View |
| `filtview` | Filtered View |
| `infnode` | Infrastructure Node |
| `inc` | `!include` directive |
| `cst` | `!const` constant |
| `grp` | Group block |
| `props` | Properties block |
| `anim` | Animation block |
| `autolay` | `autoLayout` |

## Inspections

| Inspection | Level | Description |
|------------|-------|-------------|
| Undefined reference | Error | Flags references to elements or identifiers that are never defined |
| Unused element | Weak warning | Highlights defined elements that are never referenced |
| Duplicate identifier | Error | Detects the same identifier declared more than once |
| Empty block | Weak warning | Flags empty `{ }` blocks |
| Missing required property | Error | Flags elements or views missing a required property |
| Deprecated keyword | Warning | Flags deprecated DSL keywords and suggests current syntax |
| Invalid color value | Error | Flags invalid hex colors (including the British `colour` spelling) |
| Invalid element context | Error | Flags elements declared in the wrong parent scope |
| Invalid relationship | Error | Flags malformed or invalid relationships |
| Duplicate view key | Error | Detects views sharing the same key, which Structurizr rejects on export |

## Actions

| Action | Location | Shortcut | Description |
|--------|----------|----------|-------------|
| Structurizr DSL File | File → New | — | Create a new `.dsl` file |
| Refresh Structurizr Preview | Tools → Structurizr; editor context menu | `Ctrl+Shift+R` | Re-render the diagram preview |
| Export Structurizr Diagram… | Editor context menu; Tools → Structurizr → Export | — | Export via dialog to SVG, PNG, PlantUML, Mermaid, DOT, or JSON |
| Export as SVG / PNG / PlantUML… | Tools → Structurizr → Export | — | Quick export to a single format |
| Copy as SVG / PlantUML / Mermaid / Image | Tools → Structurizr → Copy Diagram; editor context menu | — | Copy the rendered diagram to the clipboard |

## Keyboard Shortcuts

Standard IDE bindings for the language features this plugin provides:

| Shortcut | Action |
|----------|--------|
| `Ctrl+Space` | Code completion |
| `Ctrl+Click` / `Ctrl+B` | Go to definition |
| `Alt+F7` | Find usages |
| `Ctrl+Alt+Shift+N` | Go to symbol |
| `Ctrl+Alt+L` | Reformat code |
| `Ctrl+/` | Comment / uncomment |
| `Shift+F6` | Rename |
| `Ctrl+Q` | Quick documentation |

## Configuration

### Global — Settings → Tools → Structurizr DSL

Organized into five groups: Structurizr CLI, Live Preview, Export, Editor, and Code Completion.

| Setting | Default | Notes |
|---------|---------|-------|
| CLI path | *(empty)* | Path to the `structurizr-cli` JAR or executable |
| Use embedded CLI if available | On | Use the bundled CLI when no path is set |
| Timeout (seconds) | 30 | Maximum time to wait for CLI operations |
| Enable live preview | On | Render the diagram as you edit |
| Auto-refresh preview on save | On | Refresh the preview when the file is saved |
| Refresh delay (ms) | 500 | Delay before refreshing after typing |
| Show preview in split editor by default | On | Open new `.dsl` files with the split view |
| Zoom level (%) | 100 | Preview zoom |
| Use system theme | On | Match the preview to the IDE theme |
| Dark mode for preview | Off | Force a dark diagram theme |
| Default format | PNG | One of PNG, SVG, PlantUML, Mermaid, DOT, JSON |
| Default directory | *(empty)* | Leave empty to use the source file directory |
| Image width | 1920 | Raster export width |
| Image height | 1080 | Raster export height |
| Include metadata in exports | On | Embed workspace metadata |
| Auto-open exported file | On | Open the file after export |
| Show breadcrumbs | On | Navigation breadcrumbs |
| Enable code folding | On | Fold DSL blocks |
| Show line markers | On | Gutter icons for element definitions |
| Enable inspections | On | Run the code inspections |
| Auto-popup completion | On | Show completion automatically |
| Include element references in completion | On | Offer defined elements as suggestions |
| Show documentation in completion popup | On | Attach docs to completion items |

### Project — Settings → Tools → Structurizr DSL → Project Settings

Project settings override the global ones.

| Setting | Description |
|---------|-------------|
| Use project-specific CLI path | Enable a per-project CLI override |
| Project CLI path | CLI JAR/executable to use for this project |
| Default workspace file | The default `.dsl` file for this project |
| Export directory | Per-project export location (empty falls back to global) |
| Override global preview settings | Use the project preview delay below |
| Preview delay (ms) | Per-project refresh delay |

## Tool Windows

### Structurizr Preview

- **Location:** right panel (secondary)
- **Content:** live C4 diagram rendered from the active `.dsl` file, refreshing as you edit

## Supported Keywords

All Structurizr DSL keywords are supported, including:

- **Model:** `workspace`, `model`, `person`, `softwareSystem`, `container`, `component`, `group`, `element`
- **Deployment:** `deploymentEnvironment`, `deploymentNode`, `deploymentGroup`, `infrastructureNode`, `softwareSystemInstance`, `containerInstance`
- **Views:** `systemLandscape`, `systemContext`, `container`, `component`, `filtered`, `dynamic`, `deployment`, `custom`, `image`
- **Styles:** `styles`, `element`, `relationship`, `theme`, `themes`, `terminology`
- **Directives:** `!include`, `!identifiers`, `!impliedRelationships`, `!const`, `!var`, `!docs`, `!adrs`, `!script`, `!plugin`, `!element(s)`, `!relationship(s)`
- **Properties:** `tags`, `description`, `technology`, `url`, `properties`, `perspectives`

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
