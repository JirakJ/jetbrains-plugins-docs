# API Contract Guard (Kei)

> Validate OpenAPI & GraphQL schemas for breaking changes directly in your IDE.

## Overview

API Contract Guard (internally known as **Kei**) validates your API contracts (OpenAPI/Swagger and GraphQL schemas) against previous versions to detect breaking changes before they reach production. It uses the Swagger Parser library for deep schema validation and provides real-time feedback as you edit API specifications.

## Installation

1. Go to **Settings → Plugins → Marketplace**
2. Search for **"API Contract Guard"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.3+, Java 17+

## Features

### Free Tier
- OpenAPI 3.x schema validation
- Basic breaking change detection (removed endpoints, changed types)
- Inline warnings in YAML/JSON spec files
- Schema syntax validation via Swagger Parser

### Pro Tier
- GraphQL schema validation
- Full breaking change analysis (added required fields, type narrowing, enum removal)
- Version comparison (diff between spec versions)
- Git integration — compare current spec vs. committed version
- API compatibility report generation
- Custom breaking change rules
- CI/CD export (JSON report for pipelines)

### Enterprise Tier
- Team-wide API governance policies
- Cross-service contract testing
- API changelog generation

## Configuration

### Settings Location
**Settings → Tools → API Contract Guard**

| Setting | Default | Description |
|---------|---------|-------------|
| Spec directories | `src/main/resources` | Directories to scan for API specs |
| Severity level | WARNING | Default severity for breaking changes |
| Auto-validate on save | `true` | Validate specs automatically on save |
| Baseline branch | `main` | Git branch to compare against |
| GraphQL enabled | `true` | Enable GraphQL schema validation |

## Tool Windows

### API Contract Panel
- **Location:** Bottom panel
- **Content:** Breaking change list with severity, description, spec location, and suggested fix
- **Features:** Group by endpoint, filter by severity, export report

## Inspections

| Inspection | Severity | Description |
|-----------|----------|-------------|
| Breaking Change Detection | WARNING | Detects backward-incompatible API changes |
| Schema Validation Error | ERROR | Invalid OpenAPI/GraphQL syntax |
| Deprecated Endpoint Usage | WEAK WARNING | Endpoints marked as deprecated |

## Supported File Types

- OpenAPI/Swagger: `.yaml`, `.yml`, `.json`
- GraphQL: `.graphql`, `.gql`

## External Integrations

- **Swagger Parser** — Deep OpenAPI schema parsing and validation
- **Git** — Compare spec versions across branches/commits
- **CI/CD** — Export JSON compatibility reports

## FAQ

**Q: Which OpenAPI versions are supported?**
A: OpenAPI 3.0.x and 3.1.x, plus Swagger 2.0.

**Q: Does it support AsyncAPI?**
A: Not yet. AsyncAPI support is planned for a future release.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
