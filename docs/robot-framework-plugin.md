# Robot Framework

> Robot Framework 7.4 language support — editing, navigation, inspections with migration fixes, formatting, and test execution — for JetBrains IDEs.

**Free & open source** — source: https://github.com/JirakJ/robot-framework-plugin (Apache-2.0); contributions welcome.

## Overview

Robot Framework turns your JetBrains IDE into a Robot Framework development environment. It provides a custom language implementation for `.robot` and `.resource` files with syntax support up to Robot Framework 7.4, context-aware code completion, go-to-declaration and rename refactoring across files, a structure view, and code folding.

Beyond editing, it ships code-quality inspections with one-click migration fixes, a one-shot file formatter, and test execution from the gutter through a dedicated run configuration.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Robot Framework"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.2+ (IntelliJ IDEA, PyCharm, or another compatible IDE). Python with Robot Framework installed is needed to run tests.

## Features

### Robot Framework 7.4 syntax
- **GROUP blocks** (RF 7.2) — highlighting, folding, completion, live template, and END matching
- **Variable type conversion** (RF 7.3) — `${amount: int}`, `@{ids: list[int]}`, and `${dir: Literal["UP", "DOWN"]}` are highlighted, completed, and validated
- **Secret variables** (RF 7.4) — completion, live template, and a check that rejects literal secrets
- **VAR statement** (RF 7.0/7.1) — completion for every scope including `SUITES`
- **Inline IF, `[Setup]` on user keywords, `-tag` removal, WHILE limits** (RF 7.0) — understood by the editor and the inspections
- **Migration help** — one-click fixes for `[Return]`, `Force Tags`, `WITH NAME`, singular section headers, and the deprecated loop keywords

### Editing and navigation
- Syntax highlighting for Robot Framework markers, typed variables, tags, and sections
- Context-aware completion for keywords, variables, and library imports
- Go-to declaration for keyword definitions and find usages across files
- Rename refactoring that renames keywords across all project files
- Structure view of test cases, keywords, and variables; breadcrumbs
- Code folding for sections, test cases, and keywords
- Inline `arg0:`, `arg1:` hints for positional keyword arguments
- Live templates and file templates (test suite, resource)
- Customizable colors (**Settings → Editor → Color Scheme**)

### Code quality
- One-shot formatter (`Ctrl+Alt+Shift+R`) that normalizes section headers, expands tabs to spaces, trims trailing whitespace, and tidies blank lines
- Inspections for long test names, empty test cases, tab separators, trailing whitespace, duplicate test-case names, TODO/FIXME markers, unused suite variables, deprecated syntax, unbalanced blocks, malformed variable types, literal secrets, and data before the first section
- Quick fixes to convert tabs to spaces, strip trailing whitespace, and migrate deprecated syntax
- Inline error annotations for undefined keywords and variables, duplicate keywords, missing resources, and embedded arguments
- Spellchecking for Robot Framework files

### Test execution
- **Run from the gutter** — every test case gets a Run icon; one click executes just that test
- **Run configurations** — suite or directory, `--test`, `--include`/`--exclude` tags, `--outputdir`, extra arguments, interpreter, and working directory
- **Run with DEBUG log** — re-run with `--loglevel DEBUG` when a failure needs the detail
- **Safe invocation** — Robot is started as `<interpreter> -m robot` with an argument list, never through a shell

## Live Templates

| Abbreviation | Expands to |
|--------------|------------|
| `test` | Test case |
| `keyword` | User keyword with documentation and arguments |
| `for` | `FOR` loop |
| `if` | `IF` block |
| `try` | `TRY` / `EXCEPT` block |
| `group` | `GROUP` block |
| `var` | `VAR` statement with scope |
| `while` | `WHILE` loop with limit |
| `typedvar` | Typed variable |
| `secret` | Secret variable from an environment variable |

## Configuration

**Settings → Tools → Robot Framework** (per project)

| Setting | Default | Description |
|---------|---------|-------------|
| Python interpreter path | *(empty)* | Python interpreter used to run tests |
| Robot Framework arguments | *(empty)* | Extra command-line arguments passed to `robot` |
| Output directory | *(empty)* | Directory for Robot Framework output and logs |
| Indent size (spaces) | `4` | Spaces per indent level used by the formatter |
| Normalize section headers | On | Formatter rewrites section headers to canonical case (e.g. `*** test cases ***` → `*** Test Cases ***`) |

## Inspections

All inspections are in the **Robot Framework** group.

| Inspection | Level | Description |
|-----------|-------|-------------|
| Test name too long | Warning | Flags long test-case names |
| Empty test case | Warning | Flags test cases with no steps |
| Tab character used for separation | Warning | Flags tabs used as cell separators (quick fix available) |
| Trailing whitespace | Weak Warning | Flags trailing whitespace (quick fix available) |
| Duplicate test case name | Error | Flags duplicate test-case names within a suite |
| Unresolved TODO/FIXME marker | Weak Warning | Flags leftover TODO/FIXME comments |
| Unused suite variable | Warning | Flags suite variables that are never used (off by default) |
| Deprecated Robot Framework syntax | Warning | Flags syntax deprecated in newer Robot Framework versions, with migration fixes |
| Unbalanced IF/FOR/WHILE/TRY/GROUP block | Error | Flags blocks without a matching `END` |
| Malformed variable type | Error | Flags invalid typed-variable declarations |
| Literal value for a Secret variable | Error | Rejects literal values assigned to `Secret` variables |
| Data before the first section header | Warning | Flags content outside any section |

## Actions

| Action | Location | Shortcut | Description |
|--------|----------|----------|-------------|
| Run Test | Main menu → Robot Framework | `Ctrl+Shift+F10` | Run the test under the caret, or the whole suite |
| Run Test with DEBUG Log | Main menu → Robot Framework | `Ctrl+Shift+F9` | Run with `--loglevel DEBUG` |
| Generate Keyword | Main menu → Robot Framework; editor context menu | — | Generate a user keyword skeleton in the Keywords section |
| Format Robot File | Main menu → Robot Framework; editor context menu | `Ctrl+Alt+Shift+R` | Reformat the current Robot Framework file |
| Settings | Main menu → Robot Framework | — | Open the plugin settings page |

## Supported File Types

| Extension | Description |
|-----------|-------------|
| `.robot` | Robot Framework test/suite files |
| `.resource` | Robot Framework resource files |

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
