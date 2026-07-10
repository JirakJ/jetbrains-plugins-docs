# Robot Framework

> Full Robot Framework language support — editing, navigation, inspections, formatting, test execution, debugging, and a built-in web inspector — for JetBrains IDEs.

## Overview

Robot Framework turns your JetBrains IDE into a complete Robot Framework development environment. It provides a custom language implementation for `.robot`, `.resource`, and `.txt` files with syntax highlighting for Robot Framework 7+, context-aware code completion, go-to-declaration and rename refactoring across files, a structure view, and code folding.

Beyond editing, it runs and debugs tests from the editor, offers an interactive REPL for trying keywords in real time, ships a set of code-quality inspections and a one-shot file formatter, and includes a Web Inspector tool window for generating element locators for browser-based tests.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Robot Framework"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.2+, JDK 17+, and a Python installation with Robot Framework (required to run and debug tests).

This is a commercial plugin distributed under the JetBrains Marketplace freemium model; a trial and licensing are handled by the Marketplace.

## Features

### Editing and Navigation
- Syntax highlighting for Robot Framework 7+ keywords, variables, and sections
- Context-aware code completion for keywords, variables, and library imports
- Go-to declaration for keyword definitions and find-usages across files
- Rename refactoring that safely renames keywords project-wide
- Structure view of test cases, keywords, and variables
- Code folding for sections, test cases, and keywords
- Inline parameter hints for keyword arguments
- Live templates for common Robot Framework patterns

### Code Quality
- One-shot code formatter that normalizes section headers, expands tabs to spaces, trims trailing whitespace, and tidies blank lines
- Inspections for long test names, empty test cases, undefined keywords, missing resources, duplicate test-case names, tab separators, trailing whitespace, TODO/FIXME markers, and unused suite variables
- Quick fixes to convert tabs to spaces and strip trailing whitespace
- Inline error annotations for syntax errors, undefined variables, and duplicate keywords
- Spellchecking for Robot Framework files

### Execution and Debugging
- Run tests directly from the editor via a dedicated run configuration
- Step-through debugger with breakpoints, variable inspection, and conditional breakpoints
- Interactive REPL for testing keywords without running a full suite
- Performance profiler to find slow keywords

### Web Testing
- Web Inspector tool window: a built-in browser element inspector for locator generation
- SeleniumLibrary completion and navigation

## Configuration

**Settings → Tools → Robot Framework**

| Setting | Default | Description |
|---------|---------|-------------|
| Python interpreter path | *(empty)* | Python interpreter used to run and debug tests |
| Robot Framework arguments | *(empty)* | Extra command-line arguments passed to `robot` |
| Output directory | *(empty)* | Directory for Robot Framework output and logs |
| Web inspector browser | `chrome` | Browser opened by the Web Inspector |
| Enable auto-import for libraries | On | Auto-import libraries for completion |
| Indent size (spaces) | `4` | Spaces per indent level used by the formatter (minimum 2) |
| Normalize section headers | On | Formatter rewrites section headers to canonical case |

## Tool Windows

### Robot Framework
- **Location:** Bottom panel
- **Content:** Test execution output and run results

### Web Inspector
- **Location:** Right panel
- **Content:** Browser element inspector for generating locators for web tests

## Inspections

| Inspection | Level | Description |
|-----------|-------|-------------|
| Test name too long | Warning | Flags test-case names that exceed the configured length |
| Empty test case | Warning | Flags test cases with no steps |
| Tab character used for separation | Warning | Flags tabs used as cell separators |
| Trailing whitespace | Weak Warning | Flags trailing whitespace (quick fix available) |
| Duplicate test case name | Error | Flags duplicate test-case names within a suite |
| Unresolved TODO/FIXME marker | Weak Warning | Flags leftover TODO/FIXME comments |
| Unused suite variable | Warning | Flags suite variables that are never used (off by default) |

## Actions

| Action | Location | Shortcut | Description |
|--------|----------|----------|-------------|
| Run Test | Main menu → Robot Framework | Ctrl+Shift+F10 | Run the current Robot Framework test or suite |
| Debug Test | Main menu → Robot Framework | Ctrl+Shift+F9 | Debug the test with breakpoints and variable inspection |
| Open Interactive REPL | Main menu → Robot Framework | — | Open the interactive Robot Framework console |
| Open Web Inspector | Main menu → Robot Framework | — | Open the Web Inspector for locator generation |
| Format Robot File | Main menu → Robot Framework, editor context menu | Ctrl+Alt+Shift+R | Reformat the current Robot Framework file |
| Generate Keyword | Editor context menu | — | Generate a new Robot Framework keyword |
| Settings | Main menu → Robot Framework | — | Open the plugin settings page |

## Supported File Types

| Extension | Description |
|-----------|-------------|
| `.robot` | Robot Framework test/suite files |
| `.resource` | Robot Framework resource files |
| `.txt` | Legacy Robot Framework files |

## Language Features

- **Sections:** `*** Settings ***`, `*** Variables ***`, `*** Test Cases ***`, `*** Keywords ***`, `*** Tasks ***`
- **Variables:** scalar `${var}`, list `@{list}`, dictionary `&{dict}`, environment `%{ENV}`
- **Control flow:** `FOR` loops, `IF`/`ELSE`, `TRY`/`EXCEPT`, `WHILE`
- **Keyword completion:** BuiltIn keywords, SeleniumLibrary keywords, and keywords from imported libraries and resource files

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
