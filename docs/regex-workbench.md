# Regex Workbench

> Build, test, and debug regular expressions with live matching, group visualization, and per-run performance metrics — without leaving your IDE.

## Overview

Regex Workbench is an interactive regular-expression development environment that lives in a tool window inside your JetBrains IDE. Type a pattern and some test text, and the plugin validates, compiles, and matches it as you type — highlighting every match in place and listing each match's capture groups in a results table.

It is aimed at developers who would otherwise switch to an external regex tester. Pattern building, flag toggling, replacement previews, and match inspection all stay in one panel, with per-run timing so you can spot slow patterns early.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Regex Workbench"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2+, JDK 17+

## Features

- **Live matching** — the pattern is re-evaluated on every keystroke in the pattern, test-text, and replacement fields, and whenever a flag is toggled. Matching runs off the UI thread.
- **Match highlighting** — every match is highlighted directly in the test-text area.
- **Group visualization** — numbered and named capture groups are listed for each match; named groups display as `name=value`.
- **Find & Replace preview** — enter a replacement string (with `$1` / `${name}` group references) to see the fully substituted text.
- **Syntax validation** — invalid patterns are reported in the status bar instead of matching, so you always see why a pattern failed.
- **Flag management** — toggle any of eight `java.util.regex` flags per pattern (see the flag table below).
- **Performance metrics** — every run reports the match count and elapsed time in milliseconds; the benchmark iteration count is configurable.
- **Regex history** — recent patterns are saved per project, up to a configurable limit.

## Configuration

**Settings → Tools → Regex Workbench**

| Setting | Default | Description |
|---------|---------|-------------|
| Max history size | 50 | Number of patterns kept in the per-project history |
| Benchmark iterations | 1000 | Iteration count used when measuring regex performance |
| Default flags | none | Regex flags enabled automatically for new patterns |

Settings are stored per project.

## Tool Windows

### Regex Workbench

- **Location:** bottom tool-window panel. Open it from **View → Tool Windows → Regex Workbench**, or **Tools → Open Regex Workbench**.
- **Content:**
  - **Pattern** — the regular-expression input field.
  - **Flags** — a row of checkboxes, one per flag (see below); hover a checkbox for its full name.
  - **Test Text** — a multi-line, word-wrapped area for the input to match against.
  - **Replace** — a *Replace with:* field plus a read-only preview showing the input with all matches replaced.
  - **Matches** — a table with **Match**, **Start**, **End**, and **Groups** columns, one row per match.
  - **Status bar** — shows `Ready`, the match count and elapsed time (for example `3 match(es) found in 0.412 ms`), or the validation/compile error.

All results update live as you type; there is no separate run action.

#### Flags

| Checkbox | Flag | `java.util.regex` constant |
|----------|------|----------------------------|
| I | Case Insensitive | `CASE_INSENSITIVE` |
| M | Multiline | `MULTILINE` |
| S | Dot All | `DOTALL` |
| U | Unicode Case | `UNICODE_CASE` |
| X | Comments | `COMMENTS` |
| L | Literal | `LITERAL` |
| D | Unix Lines | `UNIX_LINES` |
| C | Canonical Equivalence | `CANON_EQ` |

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Open Regex Workbench | Tools menu | Opens and focuses the Regex Workbench tool window |

## FAQ

**Which regex flavor does it use?**
The Java platform engine (`java.util.regex.Pattern`). Flags, capture-group syntax, and replacement syntax all follow Java's rules.

**How do I reference capture groups in a replacement?**
Use `$1`, `$2`, … for numbered groups and `${name}` for named groups in the **Replace with:** field.

**Where are history and settings kept?**
Per project: recent patterns and preferences are saved in the project's configuration and bounded by **Max history size**.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
