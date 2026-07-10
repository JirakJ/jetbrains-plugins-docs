# Env Drift Detector

> Compare environment configuration files and catch missing keys, value mismatches, and configuration drift before they break a deploy.

## Overview

Env Drift Detector compares environment configurations across `.env` files, YAML configs, and `.properties` files, then surfaces the differences in a color-coded, side-by-side dashboard. It automatically discovers the configuration files in your project and flags keys that are missing from one environment or whose values have drifted apart.

It is built for developers who juggle multiple environment files — local, staging, production — and need a fast way to confirm they stay in sync.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Env Drift Detector"**
3. Click **Install** and restart the IDE

**Requirements:** IntelliJ IDEA 2023.2+ (any edition), JDK 17+

## Features

Env Drift Detector is a freemium plugin. The core comparison workflow is free; additional formats, file watching, and reporting are part of the Professional tier.

### Free Tier
- Side-by-side comparison dashboard (up to two files)
- Auto-discovery of environment files in the project
- `.env` (dotenv) file format support
- Color-coded drift results — green (match), red (missing key), yellow (value mismatch)

### Professional Tier
Everything in Free, plus:
- Unlimited files in the comparison dashboard
- YAML and `.properties` format support
- Real-time file-change watching with drift notifications
- Text and HTML drift reports

## Configuration

**Settings → Tools → Env Drift Detector**

| Setting | Default | Description |
|---------|---------|-------------|
| File patterns | `.env`, `.env.local`, `.env.development`, `.env.staging`, `.env.production`, `.env.test`, `.env.example`, `application.yml`, `application.yaml`, `application.properties` | Comma-separated file names used to auto-discover environment files. |
| Ignored keys | *(none)* | Comma-separated keys to exclude from the comparison. |
| Comparison mode | `strict` | `strict` requires an exact value match; `relaxed` ignores case and surrounding whitespace. |

Settings are stored per project.

## Tool Windows

### Env Drift
- **Location:** Bottom panel
- **Content:** The drift dashboard. Pick two discovered files from the selectors and click **Compare** to see a side-by-side, color-coded diff of their keys and values.

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Compare Environments | Tools menu | Runs a drift comparison on the project's environment configuration files. |

## Supported File Formats

| Format | Extensions | Example |
|--------|------------|---------|
| dotenv | `.env`, `.env.*` | `DB_HOST=localhost` |
| YAML | `.yml`, `.yaml` | `database.host: localhost` |
| Properties | `.properties` | `db.host=localhost` |

dotenv parsing handles `KEY=VALUE` pairs, comment lines, single- and double-quoted values, inline comments, `${VAR}` interpolation markers, and escaped characters. YAML keys are flattened to dot-notation, with array index notation and boolean/null handling.

## FAQ

**Why aren't my YAML or `.properties` files being compared?**
YAML and `.properties` support is a Professional-tier feature. On the Free tier, only `.env` files are compared.

**What is the difference between strict and relaxed comparison?**
`strict` treats two values as different unless they match exactly. `relaxed` ignores letter case and leading/trailing whitespace, so `Localhost` and `localhost ` are treated as a match.

**A file is not showing up in the dashboard — why?**
Auto-discovery only matches the names listed under **File patterns** in settings. Add the file name (or a matching pattern) there to include it.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
