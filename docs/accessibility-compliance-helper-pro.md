# Accessibility Compliance Helper Pro

> Comprehensive WCAG 2.1/2.2 accessibility auditing directly inside your JetBrains IDE.

## Overview

Accessibility Compliance Helper Pro is the most comprehensive accessibility compliance plugin for JetBrains IDEs. It provides **40+ WCAG checks**, JIRA/Azure DevOps integration, custom `.a11y-report` file support, and over 100 registered actions to ensure your web projects meet AA/AAA accessibility standards.

## Installation

1. Open your JetBrains IDE (IntelliJ IDEA, WebStorm, PyCharm, etc.)
2. Go to **Settings → Plugins → Marketplace**
3. Search for **"Accessibility Compliance Helper Pro"**
4. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.3+, Java 17+

## Features

### Free Tier
- Basic WCAG 2.1 Level A checks
- Real-time HTML/JSX inspection
- Inline warnings with severity indicators
- Quick-fix suggestions for common issues
- Accessibility report file viewer (`.a11y-report`)

### Pro Tier
- Full WCAG 2.1 & 2.2 Level AA/AAA checks (40+ rules)
- **US Compliance Standards: Section 508 (Revised 2018) & ADA Title III (DOJ 2024 Rule)**
- **Emerging Standards: WCAG 3.0 Draft & EN 301 549 V4 (EU)** — disabled by default
- **Color Contrast Analyzer** — WCAG §1.4.3 (AA) and §1.4.6 (AAA) contrast ratio calculation with hex, rgb, rgba, and named CSS colour parsing
- **ARIA Validation Engine** — Full WAI-ARIA 1.2 validation: role validity, required attributes, deprecated attribute detection, aria-hidden misuse warnings
- **Screen Reader Simulation** — Real DOM reading order engine with accessibility tree traversal, displayed in the tool window Screen Reader tab
- **Keyboard Navigation Analyzer** — Focus trap detection, skip-link validation, tab order analysis, modal focus management
- **CI/CD Workflow Generator** — Generates real workflow files (GitHub Actions, GitLab CI, Jenkins, Azure DevOps) with configurable WCAG level and fail-on-violations
- JIRA integration — create accessibility issues directly from IDE
- Azure DevOps integration — sync findings with work items
- Batch project scanning
- Custom rule configuration
- PDF/HTML compliance report generation

## Configuration

### Settings Location
**Settings → Tools → Accessibility Compliance Helper Pro**

| Setting | Default | Description |
|---------|---------|-------------|
| WCAG Level | AA | Target compliance level (A, AA, AAA) |
| Section 508 | `false` | Enable Section 508 (Revised 2018) checks |
| ADA Title III | `false` | Enable ADA Title III (DOJ 2024) checks |
| WCAG 3.0 Draft | `false` | Enable WCAG 3.0 Working Draft checks (emerging) |
| EN 301 549 | `false` | Enable EU Accessibility Act checks (emerging) |
| Auto-scan on save | `true` | Automatically check files on save |
| Report format | HTML | Default export format (HTML, PDF, JSON) |
| JIRA URL | *(empty)* | JIRA server URL for integration |
| Azure DevOps URL | *(empty)* | Azure DevOps organization URL |
| Color contrast ratio | 4.5:1 | Minimum contrast ratio threshold |
| Custom rules path | *(empty)* | Path to custom rule definitions |

## Tool Windows

### Accessibility Compliance Panel
- **Location:** Bottom panel
- **Content:** Real-time findings table with severity, WCAG criterion, description, and quick-fix actions
- **Features:** Filter by severity, group by file, export findings

### Color Contrast Analyzer
- **Location:** Right panel (Pro)
- **Content:** Visual color pair analysis with WCAG compliance indicator

## Inspections

The plugin registers 40+ inspections covering:

| Category | Examples |
|----------|----------|
| **Images** | Missing `alt` attributes, decorative image handling |
| **Forms** | Missing `label` associations, ARIA labels |
| **Navigation** | Keyboard trap detection, skip links, tab order |
| **Color** | Insufficient contrast ratios, color-only indicators |
| **Structure** | Heading hierarchy, landmark regions, page title |
| **ARIA** | Invalid roles, missing required properties |
| **Media** | Missing captions, audio descriptions |
| **Interactive** | Focus management, click handlers on non-interactive elements |

## Supported File Types

- HTML (`.html`, `.htm`)
- JSX/TSX (React components)
- Vue (`.vue` single-file components)
- Accessibility reports (`.a11y-report`)

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Alt+A` | Run accessibility audit on current file |
| `Ctrl+Alt+A` | Open compliance panel |

## External Integrations

- **JIRA** — Create issues with WCAG reference, severity, and code snippet
- **Azure DevOps** — Sync findings as work items
- **CI/CD** — Generate real workflow files for GitHub Actions, GitLab CI, Jenkins, and Azure DevOps directly into your project; includes pa11y-ci and axe-core scanning, report generation, and artifact uploads

## FAQ

**Q: Does the plugin send my code to external servers?**
A: No. All analysis is performed locally within your IDE. Only JIRA/Azure DevOps integrations communicate with your configured servers.

**Q: Which WCAG version is supported?**
A: WCAG 2.1 and 2.2 (Levels A, AA, and AAA).

**Q: Can I create custom accessibility rules?**
A: Yes (Pro tier). Define custom rules in a JSON configuration file.

---

**Current Version:** 2026.6.26 · **Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
