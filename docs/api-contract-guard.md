# Kei - API Contract Testing

> Check the `fetch` and `axios` calls in your JavaScript and TypeScript code against your project's OpenAPI and Swagger contracts while you edit.

**Free & open source** — source: https://github.com/JirakJ/api-contract-guard (Apache-2.0); contributions welcome.

## Overview

Kei finds the OpenAPI 3.x and Swagger 2.0 contracts in your project and validates `fetch` and `axios` calls in JavaScript and TypeScript against them. Contract violations — an unknown endpoint, a missing required body field, a wrong literal type, an invalid enum value — appear as inline editor errors, so drift between your code and your API is caught while you write the call rather than in a failing integration test.

Discovered contracts are listed in the **Kei Contracts** tool window, and an Alt+Enter quick fix adds missing required fields for you.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Kei - API Contract Testing"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2+. Call validation needs the bundled **JavaScript** plugin (available in IntelliJ IDEA Ultimate, WebStorm, and other IDEs with JavaScript support).

## Features

### Contract discovery
- Indexes YAML/JSON files whose name contains `openapi`, `swagger`, or `api` and that declare an `openapi` or `swagger` version
- Skips `node_modules`, `build`, `dist`, `target`, and similar folders
- Re-indexes contract files automatically when they change; **Tools → Refresh Contracts** re-scans on demand

### Contract Explorer
- **Kei Contracts** tool window listing each contract's endpoints, request body fields (required fields marked with `*`), and responses

### Call validation (JavaScript / TypeScript)
- Validates `fetch(url, { method, body })` and `axios.get/post/put/patch/delete(url, body)` calls with a string-literal URL
- Path templates such as `/users/{id}` match concrete URLs such as `/users/42`; host, query string, and a base-path prefix are ignored
- Checks object-literal request bodies (also inside `JSON.stringify`) for missing required fields, literal type mismatches, and invalid enum values
- Optional weak warning for calls with no matching contract endpoint (reported only when the project contains at least one contract)

### Quick fix
- **Alt+Enter** on a missing-field violation adds the required field with a placeholder value

## Configuration

**Settings → Tools → Kei API Contract Testing** (per project, stored in `.idea/kei.xml`)

| Setting | Default | Description |
|---------|---------|-------------|
| Validate fetch/axios calls in JavaScript and TypeScript | On | Run contract validation on API calls |
| Warn about calls with no matching contract endpoint | On | Report calls whose endpoint is not described by any indexed contract |
| Re-index contract files when they change | On | Re-index contracts automatically when files change on disk |

## Tool Windows

### Kei Contracts
- **Location:** Right panel
- **Content:** Discovered OpenAPI/Swagger contracts with their endpoints, request body fields, and responses

## Inspections

| Inspection | Level | Description |
|-----------|-------|-------------|
| API Contract Validation (group *Kei*) | Error | Flags JavaScript/TypeScript `fetch`/`axios` calls that violate their OpenAPI contract |

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Refresh Contracts | Tools menu | Re-scan the project for OpenAPI/Swagger contracts |

## Supported Languages & File Types

- **Code validated:** JavaScript, TypeScript (`fetch` and `axios` calls)
- **Contracts:** OpenAPI 3.x and Swagger 2.0 in `.yaml`, `.yml`, or `.json`

## FAQ

**Q: Which contract formats are supported?**
A: OpenAPI 3.x and Swagger 2.0, written in YAML or JSON.

**Q: I don't see any violations — why?**
A: Make sure the JavaScript plugin is enabled, that validation is on in **Settings → Tools → Kei API Contract Testing**, that the call uses a string-literal URL, and that your contract file name contains `openapi`, `swagger`, or `api`. Run **Tools → Refresh Contracts** to rebuild the index.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
