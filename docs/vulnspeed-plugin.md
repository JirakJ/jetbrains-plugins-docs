# VulnSpeed — GPU-Accelerated SAST

> GPU-accelerated static application security testing that flags OWASP Top 10 and CWE Top 25 vulnerabilities inline as you type.

## Overview

VulnSpeed is a static application security testing (SAST) plugin that scans your code for vulnerabilities as you type and on demand. It covers the OWASP Top 10 and CWE Top 25 across seven languages, detects hard-coded secrets with vendor-specific token rules, and offers one-click `Alt+Enter` remediation. Findings surface as inline editor highlights and in a dedicated Security Dashboard tool window.

Results can be exported as SARIF, a CycloneDX SBOM, or a shareable HTML report, snapshotted into a baseline to track regressions, and enriched with CVSS/CWE metadata from public vulnerability databases. An optional GPU-accelerated engine (Metal, CUDA, or Vulkan) speeds up scanning of large codebases.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"VulnSpeed"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2025.1+, JDK 17+, 2 GB free RAM. GPU optional (Metal, CUDA, or Vulkan). Real-time highlighting in Kotlin requires the Kotlin plugin.

## Features

VulnSpeed is a freemium plugin. The lists below show what the free tier includes and what a Professional license unlocks; a free trial is available through the JetBrains Marketplace.

### Free

- Real-time, as-you-type detection with inline severity highlighting (Java, Kotlin, Python, JavaScript, TypeScript)
- OWASP Top 10 and CWE Top 25 rule coverage
- Secrets detection — 12 high-signal vendor rules (AWS, GitHub, GitLab, Slack, Stripe, Google, SendGrid, Twilio, npm tokens, private-key blocks, JWTs, and credentials in URLs; CWE-798)
- One-click auto-fix via `Alt+Enter`
- Inline suppression: `// vulnspeed-ignore`, `// vulnspeed-ignore: RULE_ID`, or `vulnspeed-ignore-file`
- On-demand single-file scan
- Security Dashboard tool window
- Report export: SARIF 2.1.0, CycloneDX 1.5 SBOM, and self-contained HTML
- Security baseline: snapshot accepted findings and diff later scans
- CVE enrichment from OSV.dev and NVD (CVSS, CWE, fixed versions)

### Professional

- GPU acceleration (Metal / CUDA / Vulkan) — 50–100× faster scanning
- Project-wide scanning
- Extended language scanning: C/C++ and Swift
- Taint analysis and cross-function data-flow tracking
- AI-based false-positive filtering
- Custom, organization-specific security rules
- Compliance reports (SOC 2, HIPAA, PCI DSS)
- CI/CD pipeline integration

## Configuration

VulnSpeed has an application-level and a project-level settings page, both under **Settings → Tools → VulnSpeed**.

### Application settings

| Setting | Default | Description |
|---------|---------|-------------|
| Enable real-time scanning | On | Scan files for vulnerabilities as you type |
| Enable auto-fix suggestions | On | Offer one-click remediation via `Alt+Enter` |
| Max file size (KB) | 1000 | Files larger than this are skipped during scanning |
| Send anonymous usage telemetry | Off | Helps improve detection quality; no source code leaves your machine |

### Project settings

| Setting | Default | Description |
|---------|---------|-------------|
| Scan changed file on save | Off | Run a scan automatically when a file is saved |
| Apply safe auto-fixes on save | Off | Automatically apply non-destructive remediation on save |

Project scans skip `node_modules`, `build`, and hidden (dot) directories.

## Tool Windows

### VulnSpeed

- **Location:** bottom panel
- **Content:** vulnerability list, severity breakdown, scan statistics, and quick access to fixes

## Inspections

| Inspection | Level | Description |
|-----------|-------|-------------|
| VulnSpeed Security Analysis | Warning | Global (batch) security inspection, in the **Security** group, that runs the VulnSpeed engine across scanned files |

## Real-Time Highlighting

As-you-type annotators run in **Java, Kotlin, Python, JavaScript, and TypeScript** (Kotlin requires the Kotlin plugin). Each inline highlight shows the vulnerability name, severity, CWE reference, and a suggested fix.

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

## Security Coverage

- **OWASP Top 10** — injection, broken access control, cryptographic failures, SSRF, and more
- **CWE Top 25** — SQL injection, XSS, OS command injection, and 22+ more
- **Secrets** — 12 vendor-specific token rules with near-zero false positives (CWE-798)

## GPU Acceleration (Professional)

| Backend | Platform |
|---------|----------|
| Metal | macOS |
| CUDA | NVIDIA GPU |
| Vulkan | Cross-platform |

The accelerated engine runs 50–100× faster than CPU scanning on large codebases. GPU is optional; VulnSpeed falls back to CPU scanning when no supported GPU is present.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
