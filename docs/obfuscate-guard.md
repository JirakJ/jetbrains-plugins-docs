# ObfuscateGuard

> Workflow, analysis, and governance for Java/Kotlin obfuscation — on top of ProGuard/R8, yGuard, and Allatori.

## Overview

ObfuscateGuard is a workflow, analysis, and governance layer for Java/Kotlin obfuscation. Rather than replacing ProGuard/R8, yGuard, or Allatori, it helps you set up, validate, run, and maintain obfuscation from inside the IDE: a guided configuration wizard, a smart editor for `.pro` files, risk analysis that catches reflection/serialization/JNI/DI breakage before it ships, and tooling to deobfuscate production crash logs.

It is aimed at teams shipping obfuscated Java or Kotlin builds who want to keep their keep-rules correct and their release pipeline reproducible.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"ObfuscateGuard"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2+, JDK 17+, and a Java or Kotlin project built with Gradle or Maven.

## Features

ObfuscateGuard is free to use; a set of advanced features unlocks with a paid license (a trial is available).

### Free
- **Configuration Wizard** — guided setup with auto-detection of build system and project type
- **Smart `.pro` editor** — syntax highlighting, code completion, and quick documentation (Ctrl+Q) for 50+ ProGuard/R8 directives
- **Config linter** — flags unknown directives (with "did you mean" typo suggestions), dangerous options (e.g. `-dontobfuscate`, `-ignorewarnings`, broad `-dontwarn`), and duplicates in the editor
- **Run obfuscation** — execute a build with the ProGuard/R8 engine, with real-time log streaming and progress
- **Safe-Mode risk analyzer** — detects reflection, serialization, JNI, dependency-injection, and dynamic-class-loading risks before you obfuscate
- **Inline inspection & gutter icons** — risk warnings in the editor with one-click quick fixes and gutter markers on risky lines
- **Dry-run validation** — simulate obfuscation for a pass/fail verdict without running a build

### Professional (paid license)
- **Stack Trace Deobfuscator** — paste an obfuscated crash log and recover original class/method names; R8 line-range entries supported, mapping file auto-detected
- **Mapping Vault** — persistent local storage of mapping files with a diff viewer and build metadata for crash symbolication
- **Keep Rules Generator** — generate keep rules and export them into `proguard-rules.pro`, preserving hand-written content
- **CI/CD export** — generate pipeline templates for GitHub Actions, GitLab CI, and Jenkins
- **Policy Engine** — team-wide rules in a VCS-shared `obfuscateguard-policy.json`, enforced by dry-run validation
- **Additional engines** — yGuard and Allatori (ProGuard/R8 is available on the free tier)
- **Custom analyzer rules** — add your own risk rules through the plugin's SPI

## Configuration

**Settings → Tools → ObfuscateGuard**

| Setting | Default | Description |
|---------|---------|-------------|
| Enable ObfuscateGuard | On | Master on/off toggle for the plugin |
| Auto-detect project configuration | On | Detect build system, project type, and existing obfuscation config on project open |
| Auto-analyze on project open | Off | Scan for obfuscation risks automatically when a project opens (Pro) |
| Default engine | ProGuard/R8 | Engine for new configurations: ProGuard/R8, yGuard, or Allatori |
| Default level | Standard | Light (rename packages), Standard (rename classes/methods/fields), or Aggressive (full + optimization) |
| Show gutter icons for risk items | On | Show warning icons in the editor gutter on risky lines |
| Max stored mappings | 20 | Mapping files retained per project (range 5–500) |

## Tool Windows

### ObfuscateGuard
- **Location:** bottom panel
- **Content:** an **Overview** tab (detected configuration status plus Configure and Analyze buttons) and an **Analysis** tab — a sortable table of detected risks by severity, category, file, line, and description, with Run Analysis and Generate Keep Rules actions

## Inspections

| Inspection | Level | Description |
|-----------|-------|-------------|
| Obfuscation risk detection | Warning | Flags code likely to break under obfuscation — reflection, serialization, JNI, DI, and dynamic class loading — with quick fixes |

## Actions

All actions live under **Tools → ObfuscateGuard**.

| Action | Description |
|--------|-------------|
| Configure Obfuscation… | Open the configuration wizard |
| Run Obfuscation | Run obfuscation with the current configuration |
| Analyze Obfuscation Risks | Scan the project for obfuscation risks |
| Dry-Run Validation | Simulate obfuscation and check for potential breakages |
| Export Keep Rules | Write generated keep rules into `proguard-rules.pro`, preserving hand-written content (Pro) |
| Deobfuscate Stack Trace… | Translate an obfuscated stack trace using mapping files (Pro) |
| Export CI/CD Template… | Generate a CI pipeline template for obfuscation (Pro) |

## Supported Files

`.pro` files (including `proguard-rules.pro` and `consumer-rules.pro`) are recognized as **ProGuard Config** and get syntax highlighting, code completion, quick documentation, and inline linting.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
