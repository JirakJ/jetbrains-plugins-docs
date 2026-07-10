# Dependency License Lens

> Scan your project's dependencies for license types, compliance risks, and conflicts — directly in your JetBrains IDE.

## Overview

Dependency License Lens reads the dependencies declared in your Gradle and Maven build files, resolves each one's license from Maven Central metadata, and surfaces the results without leaving the editor. License types appear inline next to each dependency, incompatible combinations are flagged, and a tool window groups everything by license and risk level so you can see your project's compliance posture at a glance.

It is built for developers and teams who need to keep their dependency stack legally safe — spotting copyleft obligations, conflicts, and policy violations early, before they reach production or a legal review.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Dependency License Lens"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2+, JDK 17+, a project with Gradle or Maven build files.

## Features

### Free
- **License detection** — resolves licenses automatically from Maven Central metadata, cached locally for fast rescans
- **Inline hints** — shows the license type next to each dependency in your build files
- **Risk levels** — color-coded indicators: 🟢 Permissive, 🟡 Weak Copyleft, 🔴 Strong Copyleft
- **Conflict detection** — flags incompatible license combinations in the dependency tree
- **Compliance dashboard** — a tool window listing all dependencies grouped by license and risk level
- **Build system support** — Gradle (Kotlin and Groovy DSL) and Maven
- **Pre-commit license check** — when the Git plugin is enabled, staged build files are checked for policy violations before commit

### Professional
- **Unlimited dependencies**
- **More ecosystems** — npm / yarn / pnpm, pip / poetry, and Go modules
- **SBOM export** — generate a Software Bill of Materials in SPDX and CycloneDX formats
- **Policy enforcement** — allowed / denied license lists with editor-level violations
- **Transitive analysis** — trace license obligations through the entire dependency tree
- **CI integration** — SARIF output for build pipelines

## Configuration

**Settings → Tools → Dependency License Lens**

| Setting | Default | Description |
|---------|---------|-------------|
| Commercial project | On | Flag copyleft licenses that may conflict with commercial use |
| Enable license policy enforcement | Off | Enforce blocked-license rules and show violations in the editor |
| Blocked licenses | `GPL-2.0, GPL-3.0, AGPL-3.0` | Comma-separated SPDX identifiers to block |

## Tool Windows

### License Lens
- **Location:** Bottom panel
- **Content:** All scanned dependencies grouped by license and risk level, with conflict and policy warnings.

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Scan Dependency Licenses | **Tools** menu | Scans the project's dependencies and resolves their license information |

## FAQ

**How do I run a scan?**
Use **Tools → Scan Dependency Licenses**, or open the **License Lens** tool window at the bottom of the IDE. Results are grouped by license and risk level.

**Where does the license data come from?**
Licenses are resolved from Maven Central metadata and cached locally, so repeat scans are fast.

**Which build systems are supported?**
Gradle (Kotlin and Groovy DSL) and Maven work out of the box. npm / yarn / pnpm, pip / poetry, and Go modules are supported in the Professional tier.

**Can I block risky licenses before committing?**
Yes. With the Git plugin enabled, turn on **license policy enforcement** and set your **Blocked licenses** in settings; staged build files are then checked for violations before each commit.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
