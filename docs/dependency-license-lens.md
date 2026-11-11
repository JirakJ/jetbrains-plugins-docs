# Dependency License Lens

> List the dependencies declared in your build files with their license and a risk rating — directly in your JetBrains IDE.

**Free & open source** — source: https://github.com/JirakJ/dependency-license-lens (Apache-2.0); contributions welcome.

## Overview

Dependency License Lens reads the dependencies declared in your project's root build files, looks up each one's license in a built-in offline mapping, and rates the risk. Copyleft and policy-blocked licenses become visible in a tool window before they reach a release, and an optional pre-commit check asks before you commit a build file that declares a blocked license.

It is built for developers and teams who need to keep their dependency stack legally safe — spotting copyleft obligations and policy violations early, before they reach a legal review.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Dependency License Lens"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2+. The pre-commit check needs the bundled Git plugin.

## Features

- **Build file parsing** — Gradle Kotlin DSL (`build.gradle.kts`), Gradle Groovy DSL (`build.gradle`), Maven (`pom.xml`), and npm (`package.json`) in the project root
- **Offline license lookup** — a built-in mapping of widely used libraries to SPDX identifiers and a built-in SPDX database (permissive, weak copyleft, strong copyleft); no network access
- **Risk levels** — Safe, Caution, Warning, and Blocked, taking into account whether the project is commercial
- **License policy** — block a configurable list of SPDX identifiers (default `GPL-2.0, GPL-3.0, AGPL-3.0`)
- **Pre-commit check** — when the policy is enabled and a commit touches a build file that declares a dependency with a blocked license, the IDE asks before committing
- **License Lens tool window** — table of dependencies with version, license, category, and risk, plus a summary

Dependencies the built-in mapping does not know are listed as *Unknown* with risk *Caution*.

## Configuration

**Settings → Tools → Dependency License Lens**

| Setting | Default | Description |
|---------|---------|-------------|
| Commercial project | On | Flag copyleft licenses that may conflict with commercial use |
| Enable license policy enforcement | Off | Mark blocked licenses in scan results and ask before committing a build file that declares them |
| Blocked licenses | `GPL-2.0, GPL-3.0, AGPL-3.0` | Comma-separated SPDX identifiers to block |

## Tool Windows

### License Lens
- **Location:** Bottom panel
- **Content:** Table of scanned dependencies with version, license, category, and risk, plus a summary.

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Scan Dependency Licenses | **Tools** menu | Scan the project's dependencies for license information |

## FAQ

**How do I run a scan?**
Use **Tools → Scan Dependency Licenses**, or open the **License Lens** tool window at the bottom of the IDE.

**Where does the license data come from?**
From a mapping and SPDX database built into the plugin. No network requests are made; libraries the mapping does not know are shown as *Unknown*.

**Which build files are read?**
`build.gradle.kts`, `build.gradle`, `pom.xml`, and `package.json` in the project root.

**Can I block risky licenses before committing?**
Yes. With the Git plugin enabled, turn on **Enable license policy enforcement** and set your **Blocked licenses**; the IDE then asks before committing a build file that declares a blocked license.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
