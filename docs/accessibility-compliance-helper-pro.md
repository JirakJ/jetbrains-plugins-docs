# Accessibility Compliance Helper Pro

> Real-time WCAG 2.0/2.1/2.2, Section 508 and ADA accessibility checking directly inside your JetBrains IDE.

## Overview

Accessibility Compliance Helper Pro catches accessibility violations as you write them. It gives instant, inline feedback for HTML, JSX, TSX, JavaScript, Vue, Svelte, Razor (`.razor`) and ASP.NET Razor views (`.cshtml`) — no external tools, no context switching. Severity-based highlighting maps to WCAG conformance: Error for Level A, Warning for AA, and Info for AAA advisories, each with a hover tooltip that references the relevant success criterion and suggests a fix.

Beyond live editing, a one-click Unified Project Audit scores the whole project 0–100 (grade A–F), exports HTML/JSON/SARIF reports, and can gate CI. The plugin covers five compliance standards — WCAG 2.0/2.1/2.2, Section 508 (Revised 2018), ADA Title III (DOJ 2024 rule), EN 301 549 V4, and the WCAG 3.0 draft. All analysis runs locally.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Accessibility Compliance Helper Pro"**
3. Click **Install** and restart the IDE

**Requirements:** IntelliJ IDEA 2024.2+ (build 242+) or any compatible JetBrains IDE, Java 17+.

## Features

### Real-time scanning
- Continuous WCAG analysis as you type across HTML, JSX, TSX, JavaScript, Vue, Svelte, Razor and `.cshtml`
- Severity highlighting — Error (Level A), Warning (AA), Info (AAA advisory) — with gutter icons
- Hover tooltips with violation detail, the WCAG success criterion, and fix guidance

### 40+ checks in 10+ categories
Images (alt-text quality, decorative vs informative, SVG), Forms (labels, fieldset/legend, error identification, autocomplete), ARIA (roles, required properties, forbidden patterns, live regions), Color Contrast (AA 4.5:1 / AAA 7:1), Keyboard (tab order, focus management, skip navigation), Navigation (heading hierarchy, landmarks), Media (captions, audio descriptions, autoplay) — plus links, tables and language.

### Unified Project Audit
- 0–100 health score with an A–F grade from all auditors (Contrast, Labels, Landmarks, Headings, Alt Text) in a single run
- Self-contained HTML report with an SVG score ring and per-category pass rates
- SARIF 2.1.0 export so findings annotate pull requests via GitHub Code Scanning / Azure DevOps
- Baseline: lock the current findings and later diff a fresh scan to surface only new regressions

### Compliance standards
- WCAG 2.0/2.1/2.2 at Levels A/AA/AAA
- Section 508 (Revised 2018) and ADA Title III (DOJ 2024 rule)
- EN 301 549 V4 and the WCAG 3.0 draft (both disabled by default)
- Generates ADA / WCAG / Section 508 assessment reports

### Quick fixes and simulation
- Intention quick fixes (Alt+Enter) add missing alt text and ARIA labels; framework-aware remediations cover React, Vue 2/3, Angular and Material-UI
- Screen-reader simulation previews how assistive technology reads your markup
- CI/CD workflow generation for GitHub Actions, GitLab CI, Jenkins and Azure DevOps, backed by a headless CLI that can fail the build below a chosen score

## Configuration

**Settings → Tools → Accessibility Helper Pro**

The settings page is a tree: a parent panel with sub-pages for WCAG Compliance, Core Checks, ARIA & Interactive, Forms, Media, Structure, Readability, Mobile & Responsive, Advanced, Testing & Frameworks, Keyboard Testing Presets, Voice Over Testing Presets, General, and US Compliance Standards. Individual checks are toggled on their respective pages; the key global options are:

| Setting | Default | Description |
|---------|---------|-------------|
| WCAG version | 2.1 | Target WCAG version (2.0, 2.1, 2.2) |
| Compliance level | AA | Conformance level (A, AA, AAA) |
| Analysis depth | Standard | Basic, Standard, or Thorough (deep analysis) |
| Analysis scope | Current Line | Current element, current line, visible area, or entire file |
| Real-time checking | Off | Analyze on the fly as you type |
| Screen reader simulation | Off | Enable the screen-reader preview |
| Section 508 | Off | Section 508 (Revised 2018) checks |
| ADA Title III | Off | ADA Title III (DOJ 2024) checks |
| EN 301 549 | Off | EU harmonized standard (emerging) |
| WCAG 3.0 draft | Off | WCAG 3.0 working-draft checks (emerging) |

Settings are stored per project. A fresh install enables the WCAG 2.1 AA check set out of the box.

## Tool Windows

### Accessibility Checker
- **Location:** bottom panel
- **Content:** scan and audit findings

## Inspections

All four inspections target HTML and are disabled by default — enable them under **Settings → Editor → Inspections → Accessibility**. Live editor hints are provided separately by the annotators. Supported highlight levels are Error, Warning, and Information only.

| Inspection | Default level | Description |
|-----------|---------------|-------------|
| Accessibility Compliance (WCAG 2.2) | Warning | General WCAG 2.2 conformance checks |
| Color Contrast (WCAG 1.4.3 / 1.4.6) | Warning | Text/background contrast ratios |
| ARIA Validation (WAI-ARIA 1.2) | Warning | Role validity and required properties |
| Keyboard Navigation (WCAG 2.1.1 / 2.4.3) | Warning | Tab order and focus order |

## Actions

All actions live under **Tools → Accessibility**; the file-level audit actions also appear in the editor context menu.

| Action | Location | Description |
|--------|----------|-------------|
| Quick Scan Current File | Tools → Accessibility | Fast accessibility scan of the current file |
| Run Accessibility Scan | Tools → Accessibility | Scan the entire project |
| Unified Project Audit (Health Score) | Tools → Accessibility | Run all auditors; 0–100 score with HTML/JSON/SARIF export |
| WCAG Color Contrast Analyzer | Tools → Accessibility | Analyze contrast across CSS, SCSS, LESS and inline HTML styles |
| Audit Screen Reader Label Coverage | Tools → Accessibility, editor menu | Find interactive elements missing an accessible name (current file) |
| Audit Screen Reader Label Coverage (Project) | Tools → Accessibility | The same audit across the whole project |
| Audit Heading Structure | Tools → Accessibility, editor menu | Check the h1–h6 outline: missing h1, skipped levels, empty headings |
| Audit Alt Text Quality | Tools → Accessibility, editor menu | Flag file-name alt, placeholder words, redundant phrases |
| Analyze ARIA Landmark Coverage | Tools → Accessibility, editor menu | Check landmark coverage (WCAG 1.3.1 / 2.4.1) |
| Screen Reader Simulation | Tools → Accessibility | Simulate screen-reader navigation |
| Create A11y Baseline | Tools → Accessibility → Baseline | Save current violations as the accepted baseline |
| Compare Against A11y Baseline | Tools → Accessibility → Baseline | Diff a fresh scan against the baseline |
| Generate Compliance Report | Tools → Accessibility | Generate a compliance report |
| Standard Compliance Assessment | Tools → Accessibility | Generate an ADA, WCAG, or Section 508 assessment |
| CI/CD Integration | Tools → Accessibility | Generate CI/CD workflows (GitHub Actions, GitLab CI, Jenkins, Azure DevOps) |

## Supported Languages / File Types

Real-time checks and quick fixes run on HTML, JSX, TSX, JavaScript, Vue, Svelte, Razor (`.razor`) and ASP.NET Razor views (`.cshtml`). The Color Contrast Analyzer additionally reads CSS, SCSS and LESS. Inspections apply to HTML.

## FAQ

**Q: Does the plugin send my code anywhere?**
A: No. All analysis runs locally in the IDE. SARIF/HTML/JSON reports are files you export and share yourself.

**Q: Which standards are supported?**
A: WCAG 2.0/2.1/2.2 (Levels A, AA, AAA), Section 508 (Revised 2018), ADA Title III (DOJ 2024 rule), EN 301 549 V4, and the WCAG 3.0 draft.

**Q: Can I run it in CI without the IDE?**
A: Yes. A standalone headless CLI runs the project audit, baseline diff, or contrast check and can fail the build below a chosen score (`--fail-below`), emitting md/json/html/SARIF output.

**Q: I don't see any live warnings — why?**
A: Real-time checking is off by default. Enable it under **Settings → Tools → Accessibility Helper Pro → General** and confirm the analysis scope.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
