# Feature Flag Hygiene

> Detect stale feature flags, track their lifecycle, and safely clean up dead ones across your codebase.

## Overview

Feature Flag Hygiene finds the feature flags scattered through your project, tracks how long each one has gone untouched, and surfaces the stale and dead flags that quietly turn into technical debt. Rather than removing flags by hand, you review a health dashboard and let the plugin generate safe cleanup plans for the ones you no longer need. It is aimed at teams that ship behind flags and want to keep their flag set small, current, and understood.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Feature Flag Hygiene"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2+ (IntelliJ IDEA Community or Ultimate, and other IntelliJ-platform IDEs), JDK 17+

## Features

### Auto-detection
Scans text files across your project for feature flags using built-in regex patterns plus any custom patterns you add. Recognises common idioms such as `isFeatureEnabled("...")`, `featureFlags.get("...")`, `Feature.XXX.isEnabled()`, `if (FEATURE_XXX)`, `process.env.FEATURE_*`, `System.getenv("FEATURE_*")`, `getFeatureFlag("...")`, and `@FeatureToggle("...")`. Each scan reports a 0–100 project health score.

### Lifecycle tracking
Every detected flag is classified by how long it has been inactive:
- **ACTIVE** — recently modified and in use
- **STALE** — untouched past the stale threshold (30 days by default)
- **DEAD** — untouched past the dead threshold (90 days by default)
- **PERMANENT** — intentionally long-lived flags, excluded from cleanup

### Dashboard
A **Feature Flags** tool window with a summary bar (total / active / stale / dead / permanent counts), status filter buttons, a refresh control, and a table of every flag (name, status, occurrences, last modified, type). Double-click any row to jump straight to the flag in the editor.

### Safe cleanup
Generates cleanup plans with the precise file changes needed to remove stale and dead flags, handles `if/else` blocks and ternary expressions, validates the changes, and warns you when manual review is required. Nothing is rewritten without your review.

### Code inspection
Highlights feature-flag references in the editor in real time and offers a **Remove stale flag** quick fix.

### Free vs Professional
Feature Flag Hygiene is freemium. Core detection, lifecycle tracking, and the dashboard are free; the heavier automation belongs to the paid Professional tier.

| Capability | Free | Professional |
|------------|------|--------------|
| Flag detection | Up to 10 flags | Unlimited |
| Built-in patterns | Yes | Yes |
| Health dashboard | Yes | Yes |
| Custom regex patterns | — | Yes |
| Cleanup automation | — | Yes |
| CI report export | — | Yes |
| Priority support | — | Yes |

## Configuration

**Settings → Tools → Feature Flag Hygiene**

| Setting | Default | Description |
|---------|---------|-------------|
| Stale threshold | 30 days | Days of inactivity before a flag is marked STALE |
| Dead threshold | 90 days | Days of inactivity before a flag is marked DEAD |
| Scan on startup | Off | Automatically scan when a project opens |
| Show notifications | On | Show balloon notifications after a scan |
| Custom patterns | Empty | Additional detection regex patterns, one per line |

## Tool Windows

### Feature Flags
- **Location:** bottom panel (**View → Tool Windows → Feature Flags**)
- **Content:** a summary bar with total/active/stale/dead/permanent counts, **All / Active / Stale / Dead** filter buttons, a refresh button, and a table of detected flags. Double-click a flag to open its location in the editor.

## Inspections

| Inspection | Level | Description |
|------------|-------|-------------|
| Stale Feature Flag | Warning | Highlights feature-flag references in Java code and offers a quick fix to remove a stale flag. Grouped under **Feature Flag Hygiene**. |

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Scan Feature Flags | **Tools** menu | Scans the project for feature flags, classifies each by lifecycle status, and reports the counts and health score. |
| Clean Stale Flags | **Tools** menu | Builds cleanup plans for the stale and dead flags found by the last scan, for your review before anything changes. |

## Supported Languages / File Types

Scanning is language-agnostic: it searches text files across the whole project (skipping binaries and common build and dependency directories), with built-in patterns covering Java, JavaScript/TypeScript/Node, and Ruby. The real-time **Stale Feature Flag** inspection runs on Java files.

## FAQ

**Does "Clean Stale Flags" edit my code automatically?**
No. It generates cleanup plans describing the exact changes and any warnings so you can review them before applying. Flags on the permanent allowlist are left untouched.

**What makes a flag stale or dead?**
Inactivity: a flag whose location has not been modified within the Stale threshold (30 days by default) is marked STALE, and past the Dead threshold (90 days by default) it becomes DEAD. Both are configurable.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
