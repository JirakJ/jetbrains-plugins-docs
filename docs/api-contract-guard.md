# Kei - API Contract Testing

> Validate your API calls against OpenAPI contracts as you type, and catch breaking changes before they reach production.

## Overview

Kei checks the API calls in your JavaScript and TypeScript code against the OpenAPI contracts discovered in your project. Contract violations appear as inline editor errors — the same way a compiler flags a type mistake — so drift between your code and your API is caught while you write the call, not in a failing integration test or a production incident.

Kei discovers OpenAPI contracts automatically, lists every endpoint and type in a Contract Explorer tool window, and offers Alt+Enter quick fixes for common violations. It is a freemium plugin: the discovery-and-validation workflow is free, and a paid tier adds advanced analysis, mocking, and collaboration features.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Kei - API Contract Testing"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2+, JDK 17+

## Features

### Free Tier
- **OpenAPI contract discovery** — automatic detection of OpenAPI (v2/v3) contracts from local files, remote URLs, and schema registries
- **Contract Explorer** — a tool window with a tree view of every discovered contract, endpoint, and type
- **Real-time validation** — API calls in JavaScript and TypeScript are validated against their contract as you type, with inline error underlines
- **Breaking-change detection** — violations are reported with severity levels (critical, warning, info)
- **Quick fixes** — press **Alt+Enter** on a violation for suggestions such as renaming fields, updating types, or adding missing parameters

### Professional Tier
Kei is freemium; the paid tier adds:
- Analytics dashboard for contract health and violation trends
- Version management — pin, compare, and roll back contract versions, with a side-by-side diff viewer
- Advanced mocking — one-click mock server generation with custom rules, delays, and error simulation
- Test generation from schemas
- Security analyzer for API contract patterns
- AI-powered contract suggestions
- Team collaboration with shared registries and review workflows
- CI/CD integration for pipeline-level contract validation

## Configuration

**Settings → Tools → Kei API Contract Testing**

| Setting | Default | Description |
|---------|---------|-------------|
| Enable real-time validation | On | Validate API calls against contracts as you type |
| Show warnings for missing contracts | On | Warn when an API call has no matching contract |
| Auto-refresh contracts on file changes | On | Re-index contracts automatically when files change |
| Contract file patterns | `**/openapi.{yaml,yml,json}, **/swagger.{yaml,yml,json}` | Glob patterns used to discover contract files (shown read-only) |

## Tool Windows

### Kei Contracts
- **Location:** Right panel
- **Content:** Contract Explorer — a tree of discovered OpenAPI contracts with their endpoints and types

## Inspections

| Inspection | Level | Description |
|-----------|-------|-------------|
| API Contract Validation | Error | Flags JavaScript/TypeScript API calls that violate their OpenAPI contract |

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Refresh Contracts | Find Action (⌘⇧A / Ctrl+Shift+A) | Rebuilds the API contract index |

## Supported Languages & File Types

- **Code validated:** JavaScript, TypeScript
- **Contracts:** OpenAPI / Swagger (v2 and v3) in `.yaml`, `.yml`, or `.json`, discovered via the patterns `**/openapi.*` and `**/swagger.*`

## FAQ

**Q: Which contract formats are supported?**
A: OpenAPI/Swagger version 2 and version 3, written in YAML or JSON.

**Q: I don't see any violations — why?**
A: Confirm that real-time validation is enabled in **Settings → Tools → Kei API Contract Testing**, that your contract file names match the discovery patterns (`openapi.*` / `swagger.*`), and run **Refresh Contracts** to rebuild the index.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
