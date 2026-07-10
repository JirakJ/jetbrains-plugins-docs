# Run Config Drift Detector

> Validate your IDE run configurations against a `.run-requirements.yaml` manifest before you hit Run — and eliminate "works on my machine."

## Overview

Run Config Drift Detector compares your IDE run configurations against a `.run-requirements.yaml` manifest checked into your project. It catches JDK mismatches, missing environment variables, wrong working directories, port conflicts, and missing command-line tools before they cause mysterious runtime failures.

The manifest is committed to version control, so every team member validates against the same requirements. When drift is found, the plugin reports each issue with a pass/fail/warning status and offers a one-click quick-fix.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Run Config Drift Detector"**
3. Click **Install** and restart the IDE

**Requirements:** IntelliJ IDEA, PyCharm, WebStorm, or a compatible JetBrains IDE 2024.3+, JDK 17+, and a `.run-requirements.yaml` file in your project root.

## The manifest (`.run-requirements.yaml`)

Declare your project's expected environment in a `.run-requirements.yaml` file at the project root:

```yaml
jdk:
  version: "17"
  vendor: "temurin"    # optional
env:
  - name: DATABASE_URL
    required: true
    description: "PostgreSQL connection string"
  - name: API_KEY
    required: false
tools:
  - name: docker
    version: "20+"
  - name: node
    version: "18+"
ports:
  - 8080
  - 5432
```

You can also generate a starter manifest from your existing run configurations (see Team Features).

## Features

### Environment Validation
- **JDK validation** — checks the project SDK version and vendor against requirements
- **Environment variable checks** — verifies required env vars are present with the correct values
- **Working directory validation** — confirms the configured working directory resolves correctly
- **Port conflict detection** — probes required ports and flags any already in use before you run
- **Missing tool detection** — resolves required command-line tools (docker, node, …) against your `PATH` and reports any that are missing

### Drift Reporting
- **Health check dashboard** — a drift report with pass, fail, and warning status for each requirement, plus a health score
- **Quick-fix suggestions** — actionable one-click corrections for each issue (set an env var, download a JDK, kill the process holding a port)
- **Auto-scan on startup** — automatically validates the environment when the project opens
- **Manual re-scan** — trigger a scan anytime from the Tools menu

### Team Features
- **Auto-generate manifest** — create `.run-requirements.yaml` from your existing run configurations
- **Team config sync** — share the same environment requirements across the team via the committed manifest
- **Onboarding mode** — a step-by-step setup guide with a progress tracker for new team members
- **Common issues dashboard** — surfaces the most frequent drift issues

## Configuration

**Settings → Tools → Run Config Drift Detector**

| Setting | Default | Description |
|---------|---------|-------------|
| Enable drift detection | On | Master toggle for drift detection between run configurations and the manifest |
| Auto-scan on project open | On | Automatically scan for drift when a project is opened |
| Requirements file path | `.run-requirements.yaml` | Path to the YAML manifest that defines expected run configuration requirements |

## Tool Windows

### Drift Report
- **Location:** Bottom panel (open via **View → Tool Windows → Drift Report**)
- **Content:** The health-check dashboard. Each requirement shows a status — OK, MISSING, WARNING, or INCOMPATIBLE — alongside an overall health score.
- **Quick fixes:** Click a failed check to apply its suggested fix (set environment variable, download JDK, kill process on port).

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Re-scan for Drift | **Tools** menu | Re-run drift detection after changing your environment or manifest |

## FAQ

**Is there a keyboard shortcut for re-scanning?**
No shortcut is assigned by default. You can add one for "Re-scan for Drift" via **Settings → Keymap**.

**Where do results appear?**
In the **Drift Report** tool window at the bottom of the IDE. The plugin also scans automatically when the project opens (if auto-scan is enabled).

**What if there is no manifest?**
Without a `.run-requirements.yaml` file there is nothing to validate against. Create one manually, or auto-generate it from your existing run configurations.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
