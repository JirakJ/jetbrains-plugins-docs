# ADR Companion

> Create, manage, and navigate Architecture Decision Records without leaving your JetBrains IDE.

## Overview

ADR Companion brings Architecture Decision Record (ADR) management directly into IntelliJ IDEA and other IntelliJ-based IDEs, so decisions stay version-controlled, discoverable, and colocated with the code they describe. It creates ADRs from established templates, tracks their lifecycle, links decisions to the code that implements them, and validates your decision log — in the editor and from CI.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"ADR Companion"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2025.1+ (build 251), JDK 17+. Optional: the **Git4Idea** plugin (bundled with most JetBrains IDEs) enables *Create ADR from Pull Request*.

## Features

### Create & Capture
- Create ADRs from **Nygard, MADR, RFC, Y-Statement, Tyree & Akerman**, or a custom template, with automatic numbering.
- **Create ADR from Code** — start a record pre-populated with the file, line, and selected code that prompted it.
- **Create ADR from Pull Request** — pick a recent merge commit and extract Context, Decision, and Consequences from the PR description (requires Git4Idea).
- **React Server Components support** — scan for `'use client'` / `'use server'` boundaries (including inline Server Actions) and see which are documented by an ADR.

### Browse & Navigate
- **ADR Explorer** tool window with full-text search (title, status, and Context/Decision/Consequences body) and status filtering.
- **Go to ADR** — a dedicated ADRs tab in Search Everywhere (Double-Shift); type a number or title to jump to a decision.
- **Code-to-ADR navigation** — `@adr` annotations in code become clickable gutter icons with a rich hover card, and `@adr:` completion works in every language.
- **ADR-to-Code navigation** — from any ADR, list and jump to every code location that references it.
- **Status bar widget** — live ADR count and per-status breakdown; click to open the Explorer.
- **Auto-discovery** of ADR directories (`doc/adr`, `docs/adr`, `docs/decisions`, …) with no configuration.
- **Graph and timeline views** of ADR relationships and decision history.

### Govern & Share
- **Lifecycle management** — Proposed → Accepted → Deprecated → Superseded, with automatic bidirectional supersede backlinks.
- **Workflow validator** — flag illegal status transitions, missing fields, and stale proposals (with a CLI for CI gating).
- **Pre-commit ADR gate** — validate the decision log before every commit; blocking errors prompt to confirm, warnings stay informational.
- **Coverage & impact report** — find the code referencing each ADR and surface orphaned decisions (also available as a CLI).
- **Copy ADR Status Summary** — one click copies a Markdown badge and status table of every ADR.
- **Index & graph export** — generate a consolidated Markdown index, or export the relationship graph as Mermaid or Graphviz DOT.
- **Export to HTML** — share decisions outside the IDE.
- **Built-in inspections** — catch missing fields, stale records, and `@adr` references pointing at missing or outdated decisions as you type.

## Configuration

**Settings → Tools → ADR Companion**

| Setting | Default | Description |
|---------|---------|-------------|
| ADR directory path | *(auto-detected)* | Path to the ADR directory, relative to the project root (e.g. `doc/adr`) |
| Auto-detect ADR directory | `true` | Automatically locate the ADR directory in the project |
| Default ADR format | Nygard | Template used for new ADRs (Nygard, MADR, RFC, Y-Statement, Tyree & Akerman, Custom) |
| Custom template path | *(empty)* | Markdown template file; when blank, the plugin looks for `.adr-template.md` or `template.md` in the ADR directory. Placeholders: `{{number}}`, `{{number:0000}}`, `{{title}}`, `{{date}}`, `{{status}}` |
| Staleness threshold (days) | `180` | ADRs untouched for this many days are flagged as stale (range 30–730) |
| Check ADR workflow before commit | `true` | Run the pre-commit gate; errors prompt to confirm, warnings are informational |

## Tool Windows

### ADR Companion
- **Location:** Right panel
- **Content:** The ADR Explorer — a searchable, status-filterable list of every ADR in the project. Full-text search matches title, status, and body; select an ADR to view and manage it.

## Inspections

| Inspection | Level | Description |
|-----------|-------|-------------|
| ADR structure validation | Warning | Flags ADR files with missing required fields or malformed structure |
| Stale Architecture Decision Record | Weak Warning | Flags ADRs left unchanged beyond the staleness threshold |
| Reference to missing or outdated ADR | Warning | Flags `@adr:NNN` annotations pointing at a missing, Deprecated, or Superseded ADR |

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Create New ADR | Tools → ADR Companion | Create a new ADR from a template, with automatic numbering |
| Browse ADRs | Tools → ADR Companion | Open the ADR Companion tool window |
| Change ADR Status | Tools → ADR Companion | Change the lifecycle status of the current ADR |
| Create ADR from Code | Tools → ADR Companion | Create an ADR pre-populated with the current code context |
| Create ADR from Selection | Editor context menu | Create an ADR from the selected code |
| Create ADR from Pull Request… | Tools → ADR Companion | Turn a merged PR into an ADR (requires Git4Idea) |
| Copy ADR Status Summary | Tools → ADR Companion | Copy a Markdown badge and status table of all ADRs |
| Generate ADR Index | Tools → ADR Companion | Generate a consolidated Markdown index of all ADRs |
| Export ADR Relationship Graph… | Tools → ADR Companion | Export the relationship graph as Mermaid or Graphviz DOT |
| Export ADRs to HTML | Tools → ADR Companion | Export all ADRs to a static HTML report |
| Generate ADR Coverage Report… | Tools → ADR Companion | Scan the project for ADR references and produce a coverage & impact report |
| Analyze React Server Components… | Tools → ADR Companion | Report ADR coverage of `'use client'` / `'use server'` boundaries |
| Validate ADR Workflow… | Tools → ADR Companion | Validate status transitions, required fields, and stale proposals |
| Find Code References to ADR | Tools → ADR Companion, Editor context menu | List and navigate every code location referencing the current ADR |

## Supported File Types

- **Markdown (`.md`)** — ADR content files, with YAML front-matter metadata.
- **`@adr:NNN` references** — recognized in comments in any language, with gutter icons, hover cards, and code completion.

## FAQ

**Q: Where are ADRs stored?**
A: In your project, under an auto-discovered directory (`doc/adr`, `docs/adr`, `docs/decisions`, …) or a path you set in Settings. They are plain Markdown, tracked by version control.

**Q: Which ADR templates are supported?**
A: Nygard, MADR, RFC, Y-Statement, Tyree & Akerman, and a custom template. Set the default in Settings, or point *Custom template path* at your own Markdown file.

**Q: Can I enforce ADR hygiene in CI?**
A: Yes. The workflow validator and the coverage report each ship an IDE-free CLI that exits non-zero when thresholds are breached, so you can gate pull requests.

**Q: Do I need Git for the plugin to work?**
A: No — only *Create ADR from Pull Request* needs the bundled Git4Idea plugin. Everything else works without Git.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
