# SeleniumIQ

> AI for Selenium WebDriver: stable locator generation, self-healing selectors, flakiness prediction, and time-travel debugging.

## Overview

SeleniumIQ brings AI to Selenium WebDriver test automation. It generates stable element locators with stability scoring, automatically repairs broken selectors when the DOM changes, predicts flaky tests, and replays executions with full DOM snapshots at each step.

The plugin targets Java developers writing Selenium WebDriver tests in IntelliJ IDEA. It layers editor inspections, code completion, inline locator-stability annotations, and one-click generators (Page Objects, test templates) on top of an existing Selenium project.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"SeleniumIQ"**
3. Click **Install** and restart the IDE

**Requirements:** IntelliJ IDEA 2024.3+ (or any JetBrains IDE with Java support), JDK 17+, Selenium WebDriver in your project dependencies.

## Features

### AI-Powered Locators
- **AI locator generation** — stable locators with stability scoring across ID, CSS, XPath, and data-testid
- **Self-healing locators** — detect and repair broken selectors when the DOM changes
- **Locator stability annotations** — inline stability scores for every locator in your code

### Test Quality
- **Flakiness prediction** — 86% accuracy across 25+ test-health metrics
- **Intelligent wait strategies** — replace `Thread.sleep` with `WebDriverWait`, including AJAX/SPA detection
- **Code inspections** — flag flaky patterns, brittle locators, and poor wait strategies inline
- **Selenium code completion** — context-aware completion for the WebDriver API

### Test Generation
- **Page Object generator** — generate Page Object Model classes with PageFactory integration
- **Test template generator** — scaffold Selenium test templates with best practices built in
- **Data-driven testing** — load test data from CSV and JSON files

### Debugging and Analysis
- **Time-travel debugging** — replay test executions with DOM snapshots at each step
- **Visual regression testing** — pixel-perfect screenshot comparison with baseline management
- **Performance analyzer** — identify slow locators and operations

### Integration
- **Cloud platforms** — BrowserStack, Sauce Labs, LambdaTest
- **Test management** — Jira/Zephyr, TestRail, qTest
- **CI/CD** — GitHub Actions, GitLab CI, Jenkins, CircleCI, Azure DevOps
- **Cross-browser** — Chrome, Firefox, Safari, Edge

## Licensing

SeleniumIQ is free to install and use. A paid **Team tier** (listed at $99/month on the Marketplace) unlocks the team and integration features: full Team Analytics, Cloud Platform Setup, Test Management Integration, Requirements Traceability, and CI/CD configuration generation. Everything else — locators, healing, flakiness prediction, inspections, generators, and visual regression — is free.

## Configuration

The plugin registers a settings page at **Settings → Tools → SeleniumIQ**. This build exposes no user-adjustable fields there; feature options are set in the individual action dialogs.

## Tool Windows

### SeleniumIQ
- **Location:** right panel
- **Content:** a dashboard of quick-action buttons grouped into Locator Tools (Generate AI Locator, Heal Broken Locators), Analysis (Analyze Flakiness), and Generation (Generate Page Object, Visual Regression Test)

### Team Analytics
- **Location:** bottom panel
- **Content:** aggregated team test-health metrics; full analytics unlock with the paid Team tier

## Inspections

| Inspection | Level | Description |
|-----------|-------|-------------|
| Flaky Test Pattern Detection | Warning | Detects test-health anti-patterns that lead to flakiness |
| Brittle Locator Detection | Warning | Flags fragile locators such as absolute XPath and dynamic IDs |
| Poor Wait Strategy Detection | Warning | Flags `Thread.sleep` and missing `WebDriverWait` |

All three inspections run on Java sources and are enabled by default.

## Actions

| Action | Location | Shortcut | Description |
|--------|----------|----------|-------------|
| Generate AI Locator | Editor / Project View context menu | `Ctrl+Alt+L` | Generate a stable Selenium locator with stability scoring |
| Heal Broken Locators | Editor context menu | — | Automatically repair broken locators |
| Analyze Test Flakiness | Editor context menu | — | Predict and identify flaky test patterns |
| Open Dashboard | Main menu → SeleniumIQ | — | Open the SeleniumIQ dashboard tool window |
| Generate Page Object | Main menu → SeleniumIQ | — | Generate a Page Object Model class |
| Generate Test Template | Main menu → SeleniumIQ | — | Generate a Selenium test template |
| Visual Regression Test | Main menu → SeleniumIQ | — | Compare screenshots for visual regressions |
| Cloud Platform Setup | Main menu → SeleniumIQ | — | Generate cloud platform configuration (Team tier) |
| Test Management Integration | Main menu → SeleniumIQ | — | Integrate with test management systems (Team tier) |
| Requirements Traceability | Main menu → SeleniumIQ | — | Generate a requirements traceability matrix (Team tier) |
| SeleniumIQ Settings | Main menu → SeleniumIQ | — | Open the plugin settings page |

## Supported Languages

SeleniumIQ works on **Java** test sources. Inspections, code completion, and locator-stability annotations are all Java-only and assume the Selenium WebDriver Java API.

## FAQ

**Does it support languages other than Java?**
No. All inspections, completion, and annotations target Java and the Selenium WebDriver Java API.

**Do I need Selenium in my project?**
Yes. SeleniumIQ analyzes and generates against Selenium WebDriver, which must be on your project's dependencies.

**What does the paid Team tier add?**
Full Team Analytics plus the Cloud Platform, Test Management, Requirements Traceability, and CI/CD integration features. The rest of the plugin is free.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
