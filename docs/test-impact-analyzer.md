# Test Impact Analyzer

> Detect which tests are affected by your current code changes and run only those, instead of the whole suite.

## Overview

Test Impact Analyzer works out which tests are impacted by your uncommitted changes so you can skip the rest of the suite. It reads your project's local Git state to find changed files, maps each source file to the tests that cover it, and follows dependencies so indirectly-affected tests are still caught. On large codebases this turns a full test run into a short, focused one and tightens your feedback loop.

Results appear in a dedicated **Test Impact** tool window, and both analysis and a focused test run can be triggered straight from the **Tools** menu.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Test Impact Analyzer"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2 or later, and a project under Git version control (change detection relies on the bundled Git integration).

## Features

### Free Tier
- **Convention-based mapping** — automatically maps a source file to its test by naming convention (for example, `UserService` → `UserServiceTest`).
- **Basic impact analysis** — detects changed and uncommitted files from your local Git state and lists the tests directly associated with them.

### Professional Tier
- **Import analysis** — analyzes import statements to discover which tests depend on the code you changed.
- **Transitive dependency tracking** — follows the dependency graph to find tests affected through indirect dependencies.
- **Multi-language support** — Java, Kotlin, Python, JavaScript, and TypeScript.
- **Advanced reports** — richer impact reporting, including the share of the suite affected by a change.

## Configuration

Test Impact Analyzer's options live on its own settings page at **Settings → Tools → Test Impact Analyzer**.

## Tool Windows

### Test Impact
- **Location:** Bottom panel
- **Content:** The impact dashboard — a visual overview of the tests affected by your current changes, with quick navigation to each affected test.

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Analyze Test Impact | Tools menu | Analyze which tests are impacted by changes |
| Run Impacted Tests | Tools menu | Run only tests impacted by current changes |

## Supported Languages / File Types

Test Impact Analyzer maps sources to tests across:

- Java
- Kotlin
- Python
- JavaScript
- TypeScript

Multi-language coverage is a Professional Tier capability.

## FAQ

**Which changes does it analyze?**
Changes are read from your local Git state — both the git diff and uncommitted modifications — so you don't have to pick files by hand.

**Why are tests included that don't reference my change directly?**
With import and transitive dependency analysis, tests that reach your changed code indirectly (through the dependency graph) are also flagged, so nothing relevant is skipped.

**Do I need a Git repository?**
Yes. Change detection uses the IDE's Git integration, so the project must be under Git version control.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
