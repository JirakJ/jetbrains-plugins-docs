# Code Ownership Lens

> Visualize code ownership from Git history and CODEOWNERS files to spot bus-factor risk, orphaned code, and knowledge gaps.

## Overview

Code Ownership Lens answers "who owns what" in your codebase. It reads Git blame data (and CODEOWNERS rules) to map files and directories to the people who wrote them, then surfaces the results in a dashboard inside the IDE.

It is built for teams that want to understand how knowledge is distributed: which directories depend on a single person, where code has gone stale or orphaned, and how contribution is spread across the project. Ownership, contributor rankings, and a per-scope bus factor are computed on demand and shown with color-coded risk indicators.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Code Ownership Lens"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2+, and a project under Git (the bundled Git integration must be enabled).

## Features

### Free Tier

- Project-level ownership overview: total contributors, total files, and the project bus factor
- Top contributors, ranked by lines written and contribution percentage
- Basic risk indicators (Healthy / Moderate / Low / Critical)

### Professional Tier ($4.90/month)

- Full directory-level ownership breakdown, with the dominant owner shown per directory and per file
- CODEOWNERS file correlation
- Per-directory bus-factor analytics
- Orphaned and stale code detection
- Export and reporting

## Configuration

**Settings → Tools → Code Ownership Lens**

| Setting | Default | Description |
|---------|---------|-------------|
| Exclude patterns (comma-separated) | `node_modules,vendor,.gradle,build,dist,.git` | Path fragments to skip. Any tracked file whose path contains one of these fragments is left out of the analysis. |
| Stale threshold (days) | `180` | Age after which a file with no recent contribution is treated as stale/orphaned (1–3650). |
| Min contribution (%) | `1.0` | Minimum share of lines for a contributor to be counted as a meaningful owner (0–100). |

## Tool Windows

### Code Ownership

- **Location:** right panel
- **Overview strip:** summary cards for Contributors, Bus Factor, Files, and Risk (the risk value is color-coded).
- **Directory Ownership:** a tree of directories and files, each labeled with its dominant owner, ownership percentage, and file count.
- **Top Contributors:** a table of Contributor, Lines, Percentage, and Last Active.

The dashboard is empty until you run an analysis. Once a report exists, it is cached for the project and reloaded automatically the next time the tool window opens.

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Analyze Code Ownership | **Tools** menu | Lists Git-tracked files (minus your exclude patterns), runs `git blame` on each, computes ownership and bus factor, stores the report, and populates the Code Ownership tool window. Runs in the background with a progress bar and posts a completion notification. |

## FAQ

**The tool window is empty — what do I do?**
Run **Tools → Analyze Code Ownership**. The dashboard stays blank until the first analysis; after that the report is cached per project and reloads automatically.

**Do I need a Git repository?**
Yes. Ownership is derived from `git blame`, so the project must be under Git and the bundled Git integration must be enabled.

**What does "bus factor" mean here?**
It is the minimum number of contributors who, if they left, would leave more than half of the code with no recent owner. A low bus factor signals that knowledge is concentrated in a few people.

**How do I limit what gets analyzed?**
Add comma-separated path fragments to **Exclude patterns** in **Settings → Tools → Code Ownership Lens** (for example `build`, `dist`, `node_modules`).

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
