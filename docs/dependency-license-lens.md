# Dependency License Lens

> Audit and manage third-party dependency licenses in your JetBrains IDE.

## Overview

Dependency License Lens scans your project's dependencies (Maven, Gradle, npm, pip) and provides a comprehensive view of all third-party licenses. It detects license incompatibilities, flags risky licenses, and generates compliance reports for legal teams.

## Installation

1. Go to **Settings → Plugins → Marketplace**
2. Search for **"Dependency License Lens"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.3+, Java 17+

## Features

### Free Tier
- Automatic dependency license detection (Maven, Gradle)
- License type identification (MIT, Apache-2.0, GPL, BSD, etc.)
- Visual license overview in tool window
- Basic incompatibility warnings (GPL in commercial projects)
- Up to 50 dependencies analyzed

### Pro Tier
- Unlimited dependency analysis
- npm, pip, Go modules support
- License compatibility matrix
- Custom license policies (allowed/denied lists)
- SBOM (Software Bill of Materials) generation
- SPDX format export
- Transitive dependency license tracking
- License change detection across versions
- Compliance report for legal teams (PDF/HTML)
- CI/CD integration (fail on policy violation)

### Enterprise Tier
- Organization-wide license policies
- Automated legal review workflow
- Multi-project license aggregation

## Configuration

### Settings Location
**Settings → Tools → Dependency License Lens**

| Setting | Default | Description |
|---------|---------|-------------|
| Allowed licenses | MIT, Apache-2.0, BSD | Whitelist of acceptable licenses |
| Denied licenses | GPL-3.0, AGPL | Blacklist of prohibited licenses |
| Scan transitive deps | `true` | Include transitive dependencies |
| Build system | Auto-detect | Override build system detection |
| Report format | HTML | Default compliance report format |

## Tool Windows

### License Overview
- **Location:** Bottom panel
- **Content:** Dependency table with name, version, license, compatibility status
- **Actions:** Generate report, export SBOM, configure policies

## Inspections

| Inspection | Severity | Description |
|-----------|----------|-------------|
| Incompatible License | ERROR | Dependency license conflicts with project |
| Unknown License | WARNING | License type could not be determined |
| Risky License | WARNING | License in caution list (LGPL, MPL) |

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
