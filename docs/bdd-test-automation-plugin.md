# BDD Test Automation Plugin

> AI-powered BDD scenario generation and execution with local Ollama integration.

## Overview

BDD Test Automation Plugin streamlines Behavior-Driven Development by providing AI-generated test scenarios (via local **Ollama** LLM), custom run configurations for BDD frameworks, 3-tier caching for fast scenario lookup, and seamless integration with Cucumber, JBehave, and other BDD tools.

## Installation

1. Go to **Settings → Plugins → Marketplace**
2. Search for **"BDD Test Automation"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.3+, Java 17+, Ollama (optional, for AI features)

## Features

### Free Tier
- Gherkin syntax highlighting and completion
- Basic BDD scenario templates (Given/When/Then)
- Step definition navigation (jump to implementation)
- Custom run configuration for feature files
- Up to 10 AI-generated scenarios per day (requires Ollama)

### Pro Tier
- Unlimited AI scenario generation via Ollama
- 3-tier caching system (in-memory → disk → LRU eviction)
- Smart step suggestion based on existing step library
- Data table generation with realistic test data
- Scenario outline generation from examples
- Cross-feature step reuse analysis
- Test coverage mapping (scenario → code)
- Parallel scenario execution support
- Export to Cucumber JSON/JUnit XML

### Enterprise Tier
- Team-shared step library
- Living documentation generation
- Scenario versioning and comparison

## Configuration

### Settings Location
**Settings → Tools → BDD Test Automation**

| Setting | Default | Description |
|---------|---------|-------------|
| Ollama URL | `http://localhost:11434` | Ollama API endpoint |
| Ollama Model | `llama3` | AI model for scenario generation |
| Feature directory | `src/test/resources/features` | Default feature file location |
| Cache enabled | `true` | Enable 3-tier caching |
| Cache TTL (hours) | `24` | Cache time-to-live |
| Max scenarios/day (Free) | `10` | Daily AI generation limit |

## Tool Windows

### BDD Explorer
- **Location:** Right panel
- **Content:** Feature file tree, scenario list, step definition index
- **Actions:** Run scenario, generate AI scenario, navigate to step

## Actions

| Action | Shortcut | Description |
|--------|----------|-------------|
| Generate AI Scenario | `Ctrl+Alt+G` | Generate BDD scenario using Ollama |
| Run Feature File | — | Execute BDD feature via custom run config |
| Navigate to Step | `Ctrl+Click` | Jump to step definition implementation |

## Supported File Types

- Gherkin feature files (`.feature`)
- Step definition files (Java, Kotlin)
- Cucumber configuration files

## External Integrations

- **Ollama** — Local AI model for privacy-preserving scenario generation
- **Cucumber** — Feature file execution and reporting
- **JBehave** — Alternative BDD framework support
- **Git** — Feature file versioning

## FAQ

**Q: Is Ollama required?**
A: No. The plugin works without Ollama for manual BDD authoring. Ollama is only needed for AI-generated scenarios.

**Q: Which AI models work best?**
A: `llama3`, `codellama`, and `mistral` provide the best results for BDD scenarios.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
