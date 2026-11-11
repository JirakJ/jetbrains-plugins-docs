# ObfuscateGuard

> Workflow, analysis, and governance for Java/Kotlin obfuscation — on top of ProGuard/R8.

**Free & open source** — source: https://github.com/JirakJ/obfuscate-guard (Apache-2.0); contributions welcome.

## Overview

ObfuscateGuard is a workflow, analysis, and governance layer for Java/Kotlin obfuscation. Rather than replacing ProGuard/R8, it helps you set up, validate, run, and maintain obfuscation from inside the IDE: a guided configuration wizard, a smart editor for `.pro` files, risk analysis that catches reflection/serialization/JNI/DI breakage before it ships, and tooling to deobfuscate production crash logs.

It is aimed at teams shipping obfuscated Java or Kotlin builds who want to keep their keep-rules correct and their release pipeline reproducible.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"ObfuscateGuard"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2+ and a Java or Kotlin project built with Gradle or Maven.

## Features

### Setup and configuration
- **Configuration Wizard** — guided setup with auto-detection of build system and project type
- **Smart `.pro` editor** — syntax highlighting, code completion, and quick documentation for 50+ ProGuard/R8 directives
- **Config linter** — flags unknown directives (with typo suggestions), dangerous options, and duplicates right in the editor
- **Run configuration** — runs the R8 minify task with its output streamed to the Run console

### Risk analysis
- **Safe-Mode analyzer** — detects reflection, serialization, JNI, dependency-injection, and dynamic-class-loading risks before obfuscation
- **Inline inspection** — risk warnings directly in the editor with one-click quick fixes
- **Gutter icons** — visual markers on risky lines (`Class.forName`, native methods, DI annotations)
- **Dry-run validation** — simulate obfuscation for a pass/fail verdict without running it

### Mapping and debugging
- **Stack Trace Deobfuscator** — paste an obfuscated crash log and get original class and method names (R8 line ranges supported, mapping file auto-detected)
- **Keep Rules Generator** — automatic keep rules with one-click export into `proguard-rules.pro` that preserves hand-written content

### Team and CI/CD
- **CI/CD export** — generate pipeline templates for GitHub Actions, GitLab CI, and Jenkins
- **Policy engine** — team-wide rules in a VCS-shared `obfuscateguard-policy.json` in the project root, enforced by dry-run validation

```json
{
  "minLevel": "STANDARD",
  "requireMappingOutput": true,
  "requiredKeepAttributes": ["SourceFile", "LineNumberTable"],
  "forbiddenDirectives": ["-dontobfuscate", "-ignorewarnings"]
}
```

## Configuration

**Settings → Tools → ObfuscateGuard**

| Setting | Default | Description |
|---------|---------|-------------|
| Enable ObfuscateGuard | On | Master on/off toggle for the plugin |
| Default level | Standard | Level pre-selected in the wizard: Light (shrink/optimize only), Standard (rename), or Aggressive (rename + repackage) |
| Show gutter icons for risk items | On | Show warning icons in the editor gutter on lines with obfuscation risks |

## Tool Windows

### ObfuscateGuard
- **Location:** Bottom panel
- **Content:** An **Overview** tab (configuration status plus **Configure Obfuscation...** and **Analyze Risks** buttons) and an **Analysis** tab — a table of detected risks with **Run Analysis** and **Generate Keep Rules** buttons

## Inspections

| Inspection | Level | Description |
|-----------|-------|-------------|
| Obfuscation risk detection (group *ObfuscateGuard*) | Warning | Flags code likely to break under obfuscation — reflection, serialization, JNI, DI, and dynamic class loading — with quick fixes |

## Actions

All actions live under **Tools → ObfuscateGuard**.

| Action | Description |
|--------|-------------|
| Configure Obfuscation... | Open the configuration wizard |
| Run Obfuscation | Run obfuscation with the current configuration |
| Analyze Obfuscation Risks | Scan the project for obfuscation risks |
| Dry-Run Validation | Simulate obfuscation and check for potential breakages |
| Export Keep Rules | Write generated keep rules into `proguard-rules.pro`, preserving hand-written content |
| Deobfuscate Stack Trace... | Translate an obfuscated stack trace using mapping files |
| Export CI/CD Template... | Generate a CI pipeline template for obfuscation |

## Supported Files

`.pro` files (including `proguard-rules.pro` and `consumer-rules.pro`) are recognized as **ProGuard Config** and get syntax highlighting, code completion, quick documentation, and inline linting.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
