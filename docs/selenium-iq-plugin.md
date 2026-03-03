# SeleniumIQ

> AI-powered Selenium test automation with self-healing locators and flakiness prediction.

## Overview

SeleniumIQ is an AI-powered Selenium test automation plugin that eliminates test flakiness through intelligent locator generation, self-healing capabilities, and comprehensive test maintenance tools. It achieves **86% accuracy** in predicting flaky tests across 25+ health metrics.

## Installation

1. Go to **Settings → Plugins → Marketplace**
2. Search for **"SeleniumIQ"**
3. Click **Install** and restart the IDE

**Requirements:** IntelliJ IDEA 2023.2+ (or any JetBrains IDE with Java support), Selenium WebDriver in project

## Features

### Free Tier (100 AI locators/month)
- AI-powered locator generation (ID, CSS, XPath, data-testid)
- Locator stability scoring (0-100)
- Self-healing locators with one-click fixes
- Flakiness prediction (86% accuracy, 25+ metrics)
- Anti-pattern detection (Thread.sleep, absolute XPath)
- Page Object Model generation (with PageFactory)
- Code completion for WebDriver API
- 3 built-in inspections (flaky patterns, brittle locators, poor wait strategies)

### Professional Tier ($19/month)
- Unlimited AI locators
- Visual regression testing
- Performance analysis
- Cloud platform setup (BrowserStack, Sauce Labs, LambdaTest, Perfecto)
- Test management integration (JIRA/Zephyr, TestRail, qTest)
- Requirements traceability

### Team Tier ($99/month, 5-10 users)
- Team analytics dashboard
- Shared metrics
- Compliance features

### Enterprise Tier (Custom)
- SSO, audit logging
- Dedicated support

## Configuration

### Settings Location
**Settings → Tools → SeleniumIQ**

| Setting | Default | Description |
|---------|---------|-------------|
| License key | *(empty)* | SeleniumIQ license key |
| AI locator preference | CSS | Preferred locator strategy |
| Inspection severity | WARNING | Default inspection severity level |
| Cloud platform | None | Cloud testing platform credentials |
| Monthly AI limit (Free) | 100 | AI locator generation limit |

## Tool Windows

### SeleniumIQ Dashboard
- **Location:** Right panel
- **Content:** Quick-action buttons for all core features, AI locator status, usage quota
- **Icon:** Custom SeleniumIQ icon

### Team Analytics
- **Location:** Bottom panel (Premium)
- **Content:** Team-wide test health metrics, flakiness trends, locator stability
- **Icon:** Analytics icon

## Inspections

| Inspection | Severity | Description |
|-----------|----------|-------------|
| Flaky Test Pattern Detection | WARNING | Detects 25+ test health anti-patterns |
| Brittle Locator Detection | WARNING | Identifies absolute XPath, dynamic IDs |
| Poor Wait Strategy Detection | WARNING | Flags Thread.sleep, missing WebDriverWait |

## Keyboard Shortcuts

| Shortcut | Action |
|----------|--------|
| `Ctrl+Alt+L` | Generate AI Locator |
| Context Menu | Heal Broken Locators, Analyze Test Flakiness |

## Actions

| Menu Location | Actions |
|---------------|---------|
| **Editor Context Menu** | Generate AI Locator, Heal Broken Locators, Analyze Test Flakiness |
| **Main Menu → SeleniumIQ** | Open Dashboard, Generate Page Object, Generate Test Template, Upgrade License |
| **Main Menu → SeleniumIQ** (Premium) | Visual Regression Test, Cloud Platform Setup, Test Management Integration, Requirements Traceability |
| **Tools Menu** | SeleniumIQ Settings |

## Code Completion

Context-aware Selenium completions:
- `driver.findElement(By.id(""))` / `By.cssSelector("")` / `By.xpath("")`
- `new WebDriverWait(driver, Duration.ofSeconds(10))`
- Locator stability annotations (color-coded: 🟢 stable, 🟡 moderate, 🔴 brittle)

## External Integrations

| Category | Services |
|----------|----------|
| **Cloud Platforms** | BrowserStack, Sauce Labs, LambdaTest, Perfecto |
| **Test Management** | JIRA/Zephyr, TestRail, qTest |
| **CI/CD** | GitHub Actions, GitLab CI, Jenkins, CircleCI, Azure DevOps, Travis CI |
| **Browsers** | Chrome, Firefox, Safari, Edge |

## Known Limitations (v1.0)

- Shadow DOM support limited (workaround: JavaScript execution)
- Performance may degrade with 1000+ test files
- macOS keyboard shortcut conflicts possible (customize in IDE keymap)
- Selenium 4.16.1+ only (no Playwright/Cypress)

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
