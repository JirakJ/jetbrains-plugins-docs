# Robot Framework Plugin

> Full Robot Framework language support with Web Inspector for JetBrains IDEs.

## Overview

Robot Framework Plugin provides comprehensive Robot Framework support including a **custom language implementation** for `.robot` and `.resource` files, syntax highlighting, code completion, keyword navigation, test execution, and a built-in **Web Inspector** tool for web test element selection.

## Installation

1. Go to **Settings → Plugins → Marketplace**
2. Search for **"Robot Framework"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.3+, Java 17+, Python with Robot Framework (for execution)

## Features

### Free Tier
- Custom Robot Framework language (full lexer/parser)
- Syntax highlighting for `.robot` and `.resource` files
- Keyword completion (built-in + library keywords)
- Variable completion (`${var}`, `@{list}`, `&{dict}`)
- Test case/keyword navigation (Ctrl+Click)
- Section folding (Settings, Test Cases, Keywords, Variables)
- Basic test execution via run configuration

### Pro Tier
- Web Inspector tool window (pick elements from browser)
- Advanced keyword completion (cross-file, library imports)
- Variable scope analysis
- Test suite management and execution
- Keyword documentation viewer
- Selenium/Browser library integration
- Data-driven test support
- Test execution history and flakiness tracking
- HTML report viewer in IDE
- Remote library keyword import

## Configuration

### Settings Location
**Settings → Tools → Robot Framework**

| Setting | Default | Description |
|---------|---------|-------------|
| Python interpreter | Auto-detect | Path to Python with Robot Framework |
| Library paths | *(empty)* | Additional library search paths |
| Output directory | `output/` | Test execution output directory |
| Browser for Web Inspector | Chrome | Default browser for element inspection |
| Log level | INFO | Robot Framework log level |

## Tool Windows

### Robot Test Runner
- **Location:** Bottom panel
- **Content:** Test suite tree, execution log, pass/fail results
- **Actions:** Run test, run suite, view report

### Web Inspector
- **Location:** Right panel (Pro)
- **Content:** Browser element picker, locator generator, element tree
- **Actions:** Pick element, generate locator, validate selector

## Supported File Types

| Extension | Description |
|-----------|-------------|
| `.robot` | Robot Framework test files |
| `.resource` | Robot Framework resource files |
| `.py` | Python keyword libraries (navigation support) |

## Language Features

- **Sections:** `*** Settings ***`, `*** Variables ***`, `*** Test Cases ***`, `*** Keywords ***`, `*** Tasks ***`
- **Keywords:** Built-in, SeleniumLibrary, Browser, Collections, String, OperatingSystem
- **Variables:** Scalar `${var}`, List `@{list}`, Dictionary `&{dict}`, Environment `%{ENV}`
- **Control Flow:** FOR loops, IF/ELSE, TRY/EXCEPT, WHILE

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
