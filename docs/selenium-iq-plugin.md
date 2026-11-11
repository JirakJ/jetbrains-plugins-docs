# SeleniumIQ

> Selenium WebDriver helpers for Java tests: stable-locator suggestions, locator repair, flaky-pattern detection, inspections, and code generators.

**Free & open source** — source: https://github.com/JirakJ/selenium-iq-plugin (Apache-2.0); contributions welcome.

## Overview

SeleniumIQ adds offline, heuristic tooling for Selenium WebDriver tests written in Java. It suggests stable element locators ranked by a stability score, proposes more stable replacements for fragile selectors, scores test methods by flaky patterns, and generates Page Objects and test skeletons.

Everything runs locally and is rule-based — no network services or machine-learning models are involved, and every check is a deterministic rule you can read in the source. The only network access is fetching a page URL you enter when generating a Page Object.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"SeleniumIQ"**
3. Click **Install** and restart the IDE

**Requirements:** IntelliJ IDEA 2024.3+ (or another JetBrains IDE with Java support) and Selenium WebDriver in your project dependencies.

## Features

### Locators
- **Generate Locator** (`Ctrl+Alt+L`) — ranked locator suggestions (data-testid, id, name, CSS, XPath) with a stability score
- **Heal Broken Locators** — for the selected `By.xxx("...")`, proposes more stable replacements (for example dynamic id → `data-testid`/`aria-label`, absolute XPath → relative)
- **Locator stability annotations** — inline warnings on string literals passed to `By.id/xpath/cssSelector/...` that look fragile (absolute XPath, generated ids, indexes)

### Test quality
- **Analyze Test Flakiness** — scores a test method by flaky patterns (`Thread.sleep()`, hard-coded waits, missing explicit waits, brittle locators) with recommendations
- **Inspections** — flaky test patterns, brittle locators, and `Thread.sleep()` in Selenium tests
- **Completion** — common `driver.findElement(By...)` and WebDriver API entries

### Code generation
- **Generate Page Object** — fetches a page URL with Jsoup and creates a Page Object with `@FindBy` fields, or a template when no URL is given
- **Generate Test Template** — a JUnit 5, JUnit 4, or TestNG test class with WebDriver setup/teardown, copied to the clipboard
- **Cloud Platform Setup** — a RemoteWebDriver starter class for BrowserStack, Sauce Labs, or LambdaTest, copied to the clipboard
- **Test Management Integration** — a TestNG listener skeleton for Jira or TestRail, copied to the clipboard

## Tool Windows

### SeleniumIQ
- **Location:** Right panel (secondary)
- **Content:** Buttons grouped into Locator Tools (Generate Locator, Heal Broken Locators), Analysis (Analyze Flakiness), and Generation (Generate Page Object)

## Inspections

| Inspection | Level | Description |
|-----------|-------|-------------|
| Flaky Test Pattern Detection | Warning | Detects test patterns that lead to flakiness |
| Brittle Locator Detection | Warning | Flags fragile locators such as absolute XPath and long numeric ids |
| Poor Wait Strategy Detection | Warning | Flags `Thread.sleep()` in Selenium tests |

All three inspections (group *SeleniumIQ*) run on Java sources and are enabled by default.

## Actions

| Action | Location | Shortcut | Description |
|--------|----------|----------|-------------|
| Generate Locator | Editor / Project View context menu | `Ctrl+Alt+L` | Suggest stable Selenium locators ranked by stability |
| Heal Broken Locators | Editor context menu | — | Propose more stable replacements for the selected locator |
| Analyze Test Flakiness | Editor context menu | — | Score the test method by flaky patterns |
| Open Dashboard | Main menu → SeleniumIQ | — | Open the SeleniumIQ tool window |
| Generate Page Object | Main menu → SeleniumIQ | — | Generate a Page Object Model class |
| Generate Test Template | Main menu → SeleniumIQ | — | Generate a Selenium test template |
| Cloud Platform Setup | Main menu → SeleniumIQ | — | Generate a RemoteWebDriver starter for a cloud grid |
| Test Management Integration | Main menu → SeleniumIQ | — | Generate a TestNG listener skeleton for Jira or TestRail |

## Supported Languages

SeleniumIQ works on **Java** test sources. Inspections, completion, and locator-stability annotations target the Selenium WebDriver Java API.

## FAQ

**Does it use AI or a cloud service?**
No. All scores and suggestions come from deterministic local rules.

**Do I need Selenium in my project?**
Yes. SeleniumIQ analyzes and generates code against Selenium WebDriver, which must be on your project's dependencies.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
