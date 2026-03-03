# Obfuscate Guard

> ProGuard/R8 configuration validation and optimization for JetBrains IDEs.

## Overview

Obfuscate Guard helps developers manage and validate ProGuard/R8 obfuscation rules. It provides syntax highlighting for ProGuard configuration files, detects common misconfiguration errors, suggests optimizations, and previews obfuscation results — ensuring your code protection doesn't break at runtime.

## Installation

1. Go to **Settings → Plugins → Marketplace**
2. Search for **"Obfuscate Guard"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.3+, Java 17+

## Features

### Free Tier
- ProGuard/R8 config file syntax highlighting
- Basic rule validation (syntax errors, typos)
- Keep rule visualization (what's kept vs. obfuscated)
- Common pattern templates
- Class/method reference validation

### Pro Tier
- Advanced rule impact analysis (preview obfuscation results)
- Missing keep rule detection (runtime crash prevention)
- Rule optimization suggestions (merge redundant rules)
- Reflection usage scanning (auto-generate keep rules)
- Serialization compatibility checking
- Multi-module rule aggregation
- Rule diff between builds
- Export optimized configuration
- CI/CD rule validation

## Configuration

### Settings Location
**Settings → Tools → Obfuscate Guard**

| Setting | Default | Description |
|---------|---------|-------------|
| ProGuard config path | Auto-detect | Path to ProGuard configuration |
| R8 mode | Auto-detect | Use R8 rules instead of ProGuard |
| Validate on build | `true` | Run validation during build |
| Show keep preview | `true` | Display keep/obfuscate preview |

## Supported File Types

| Extension | Description |
|-----------|-------------|
| `.pro` | ProGuard configuration |
| `proguard-rules.pro` | Android ProGuard rules |
| `proguard.cfg` | ProGuard configuration (alt) |
| `consumer-rules.pro` | Library consumer rules |

## Inspections

| Inspection | Severity | Description |
|-----------|----------|-------------|
| Invalid Keep Rule | ERROR | Syntax error in keep rule |
| Missing Keep for Reflection | WARNING | Class used via reflection but not kept |
| Redundant Rule | WEAK WARNING | Rule has no effect (already covered) |
| Serialization Risk | WARNING | Serializable class may break after obfuscation |

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
