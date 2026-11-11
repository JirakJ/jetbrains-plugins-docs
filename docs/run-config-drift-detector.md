# Run Config Drift Detector

> Check your local setup against a `.run-requirements.yaml` manifest before you hit Run — and eliminate "works on my machine."

**Free & open source** — source: https://github.com/JirakJ/run-config-drift-detector (Apache-2.0); contributions welcome.

## Overview

Run Config Drift Detector checks your local setup against a `.run-requirements.yaml` manifest committed with the project. It catches JDK mismatches, missing environment variables, and a wrong working directory before they cause mysterious runtime failures.

Because the manifest lives in version control, every team member validates against the same requirements. Issues are listed in a **Drift Report** tool window with a severity, a fix suggestion, and an overall health score.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Run Config Drift Detector"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2+ and a `.run-requirements.yaml` file in your project root (path configurable).

## The manifest (`.run-requirements.yaml`)

Declare your project's expected environment in a `.run-requirements.yaml` file at the project root:

```yaml
jdk: 17
env_vars:
  - DATABASE_URL
  - API_KEY
working_dir: ./server
```

## Features

### Checks
- **JDK** — the project SDK's major version is compared with the required `jdk` (a missing SDK is flagged too)
- **Environment variables** — every name under `env_vars` must be set in the IDE's environment
- **Working directory** — `working_dir` must exist and be a directory

### Reporting
- **Drift Report tool window** — issues with severity, fix suggestion, and a health score
- **Auto-scan on startup** — a notification appears when drift is found
- **Manual re-scan** — **Tools → Re-scan for Drift** or the tool window button

## Configuration

**Settings → Tools → Run Config Drift Detector**

| Setting | Default | Description |
|---------|---------|-------------|
| Enable drift detection | On | Master toggle for drift detection |
| Auto-scan on project open | On | Automatically scan for drift when a project is opened |
| Requirements file path | `.run-requirements.yaml` | Path to the YAML manifest; relative paths resolve against the project root |

## Tool Windows

### Drift Report
- **Location:** Bottom panel (secondary)
- **Content:** Drift issues with severity and fix suggestion, the health score, the last scan time, and a **Re-scan** button

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Re-scan for Drift | **Tools** menu | Re-run drift detection after changing your environment or manifest |

## FAQ

**Where do results appear?**
In the **Drift Report** tool window. With auto-scan enabled, the plugin also scans when the project opens and notifies you when drift is found.

**What if there is no manifest?**
Without a `.run-requirements.yaml` file there is nothing to validate against; the plugin suggests creating one.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
