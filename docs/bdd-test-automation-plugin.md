# BDD Test Automation

> Fast step-definition navigation, AI-assisted scenario generation, and BDD analytics for Gherkin feature files.

## Overview

BDD Test Automation speeds up Behavior-Driven Development in JetBrains IDEs. It provides sub-200ms navigation between Gherkin steps and their step definitions using a three-tier caching system built for large suites (10,000+ scenarios), plus code completion, find usages, and rename refactoring that spans feature files and step definition code.

Beyond editing, it adds real-time inspections for undefined and duplicate scenarios, a tag-aware test runner, semantic scenario search via vector embeddings, ML-based flaky test detection, living HTML documentation, and a BDD analytics dashboard. AI scenario generation runs against a local **Ollama** model, so your code never leaves your machine.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"BDD Test Automation"**
3. Click **Install** and restart the IDE

**Requirements:** IntelliJ IDEA 2023.2+ (or another JetBrains IDE with Java support), Java 17+. Optional: [Ollama](https://ollama.ai) with the `codellama:7b` model for AI scenario generation.

## Features

### Speed
- **Step definition navigation in under 200ms** — three-tier caching optimized for 10,000+ scenarios
- **Smart code completion** — context-aware step suggestions ranked by usage statistics
- **Find usages** — locate all references to any step definition

### Editing & Refactoring
- **Rename refactoring** — rename a step across feature files and step definition code in one action
- **Gherkin syntax highlighting** — with line markers and gutter icons
- **Undefined step detection** — real-time ERROR-level inspection flags steps missing implementations
- **Duplicate scenario detection** — WARNING-level inspection catches duplicated scenarios

### AI & Intelligence
- **AI scenario generation** — generate edge cases and negative scenarios with a local Ollama LLM; code stays on your machine
- **Semantic search** — find scenarios by meaning using vector embeddings, not just text matching
- **Flaky test detection** — ML-based analysis surfaces inconsistent tests with stabilization recommendations

### Testing & Documentation
- **BDD test runner** — run scenarios with tag-based filtering and context-menu integration
- **Boolean tag filtering** — select scenarios with expressions like `@smoke and not @slow`
- **Living documentation** — auto-generate HTML docs from feature files
- **Analytics dashboard** — track coverage, step reuse, and test health

## Configuration

**Settings → Tools → BDD Settings**

| Setting | Default | Description |
|---------|---------|-------------|
| Ollama server URL | `http://localhost:11434` | Endpoint of the local Ollama API |
| Ollama model | `codellama:7b` | Model used for AI scenario generation |
| Step definition language | `Java` | Target language for generated step definitions |
| Enable flaky test detection | `true` | Turn ML-based flaky test analysis on or off |
| Flaky test threshold (%) | `20` | Failure rate above which a test is flagged as flaky |

## Tool Windows

### BDD Analytics
- **Location:** Right panel
- **Content:** BDD metrics and insights — coverage, step reuse, and test health for your suite

## Inspections

| Inspection | Level | Description |
|-----------|-------|-------------|
| Undefined Step Definition | Error | Flags Gherkin steps that have no matching step definition |
| Duplicate Scenario | Warning | Flags scenarios duplicated across feature files |

## Actions

| Action | Location | Shortcut | Description |
|--------|----------|----------|-------------|
| Generate BDD Scenario with AI | Generate popup | `Alt+G` | Generate Gherkin scenarios using the local Ollama model |
| Generate Step Definition | Generate popup | — | Generate a step definition for an undefined step |
| Find Similar Scenarios | Tools → BDD Tools | — | Find semantically similar scenarios via embeddings |
| Detect Duplicate Scenarios | Tools → BDD Tools | — | Identify duplicate test scenarios |
| Export Living Documentation | Tools → BDD Tools | — | Generate HTML documentation from feature files |
| BDD Settings | Tools → BDD Tools | — | Open the BDD settings page |
| Run Scenario | Editor context menu | — | Run the selected BDD scenario |

Navigation, Find Usages, and Rename are bound to the IDE's standard shortcuts (for example **Ctrl+B** / **Ctrl+Click** to jump to a step definition).

## Supported File Types

- Gherkin feature files (`.feature`)
- Step definition files (Java, Kotlin)

## FAQ

**Q: Is Ollama required?**
A: No. Navigation, completion, inspections, refactoring, the test runner, and analytics all work without it. Ollama is only needed for AI scenario generation.

**Q: Which AI model does it use?**
A: `codellama:7b` by default, served locally by Ollama. You can point the plugin at a different Ollama model and endpoint in **Settings → Tools → BDD Settings**.

**Q: Does my code get sent to a cloud service?**
A: No. AI generation runs entirely against your local Ollama instance, so source and scenarios never leave your machine.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
