# VulnSpeed — GPU-Accelerated SAST

> Static application security testing that flags OWASP Top 10 and CWE Top 25 vulnerabilities inline as you type.

**Free & open source** — source: https://github.com/JirakJ/vulnspeed-plugin (Apache-2.0); contributions welcome.

## Overview

VulnSpeed is a static application security testing (SAST) plugin that scans your code for vulnerabilities as you type and on demand. It covers the OWASP Top 10 and CWE Top 25 across seven languages, detects hard-coded secrets with vendor-specific token rules, and attaches a fix suggestion with OWASP/CWE references to every finding. Findings surface as inline editor highlights and in a dedicated Security Dashboard tool window.

Results can be exported as SARIF, a CycloneDX SBOM, or a shareable HTML report, snapshotted into a baseline to track regressions, and enriched with CVSS/CWE metadata from public vulnerability databases.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"VulnSpeed"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2025.1+. Real-time highlighting in Kotlin requires the Kotlin plugin.

## Features

### Real-time detection
- As-you-type detection with inline severity highlighting (Java, Kotlin, Python, JavaScript, TypeScript)
- OWASP Top 10 coverage — injection, broken access control, cryptographic failures, SSRF, and more
- CWE Top 25 coverage — SQL injection, XSS, OS command injection, and more

### Secrets detection
- 12 high-signal vendor rules — AWS, GitHub, GitLab, Slack, Stripe, Google, SendGrid, Twilio, npm tokens, private-key blocks, JWTs, and credentials in URLs (CWE-798)
- Vendor-specific token formats rather than noisy entropy heuristics

### Remediation & workflow
- Fix suggestion (description, example code, references) on every finding — fixes are applied by you, not automatically
- Inline suppression: `// vulnspeed-ignore` (same line or the comment line directly above), `// vulnspeed-ignore: RULE_ID, RULE_ID`, or `// vulnspeed-ignore-file` within the first five lines
- On-demand file scan and project scan (C/C++ and Swift are covered by on-demand scans)
- Optional scan on save, per project
- Security Dashboard tool window
- Report export: SARIF 2.1.0, CycloneDX 1.5 SBOM, and self-contained HTML

### CI/CD
- Security baseline: snapshot accepted findings into `.vulnspeed-baseline.json` and surface only new regressions
- CVE enrichment from OSV.dev and NVD (CVSS, CWE, fixed versions)
- Baseline compare and CVE enrichment also have CLI entry points for gated pipeline checks

## Configuration

VulnSpeed has an application-level and a project-level settings page, both under **Settings → Tools → VulnSpeed**.

### Application settings

| Setting | Default | Description |
|---------|---------|-------------|
| Enable real-time scanning | On | Turns the as-you-type editor highlighting on or off. Manual and on-save scans keep working when it is off. |
| Max file size (KB) | 1000 | Files larger than this are skipped by editor highlighting, Scan File, Scan Project and scan on save |

### Project settings

| Setting | Default | Description |
|---------|---------|-------------|
| Scan changed file on save | Off | Scans a supported file each time it is saved; results update the VulnSpeed tool window without taking focus and become the input for report exports |

Project scans skip `node_modules`, `build`, and hidden (dot) directories.

### Privacy

VulnSpeed collects no telemetry and never uploads source code. The only network access is the CVE enrichment action, which you run explicitly; it sends CVE identifiers to OSV.dev and NVD.

## Tool Windows

### VulnSpeed
- **Location:** Bottom panel
- **Content:** Vulnerability list, severity breakdown and scan statistics from the latest file, project or on-save scan

## Actions

Every action is available from the **Tools → VulnSpeed** menu; the two scan actions also appear in context menus.

| Action | Location | Description |
|--------|----------|-------------|
| Scan File with VulnSpeed | Editor right-click; Tools → VulnSpeed | Scan the current file |
| Scan Project with VulnSpeed | Project view right-click; Tools → VulnSpeed | Scan the entire project |
| Export SARIF Report | Tools → VulnSpeed | Export the latest results as SARIF 2.1.0 (GitHub Code Scanning / GitLab SAST) |
| Export HTML Report | Tools → VulnSpeed | Export the latest results as a self-contained HTML report |
| Export CycloneDX SBOM | Tools → VulnSpeed | Export a CycloneDX 1.5 SBOM for Dependency-Track / Sonatype / FOSSA |
| Create Security Baseline | Tools → VulnSpeed | Snapshot current findings as accepted into `.vulnspeed-baseline.json` |
| Compare Against Security Baseline | Tools → VulnSpeed | Run a differential scan against the baseline to surface regressions |
| Enrich Vulnerabilities (OSV / NVD) | Tools → VulnSpeed | Add CVSS, CWE, and fixed-version metadata from OSV.dev and NVD |

## Supported Languages

| Language | Real-time (as-you-type) | On-demand scan |
|----------|:-----------------------:|:--------------:|
| Java | Yes | Yes |
| Kotlin | Yes (Kotlin plugin) | Yes |
| Python | Yes | Yes |
| JavaScript | Yes | Yes |
| TypeScript | Yes | Yes |
| C/C++ | — | Yes |
| Swift | — | Yes |

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
