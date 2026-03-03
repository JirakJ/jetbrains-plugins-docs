# API-First Mocking Studio

> Design APIs and run mock servers directly from your JetBrains IDE.

## Overview

API-First Mocking Studio enables an API-first development workflow by letting you design OpenAPI specifications and instantly spin up a fully functional mock server (powered by **embedded Ktor**) — all without leaving your IDE. It supports Postman collection import, WebSocket mocking, GraphQL endpoints, and dynamic response generation.

## Installation

1. Go to **Settings → Plugins → Marketplace**
2. Search for **"API-First Mocking Studio"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.3+, Java 17+

## Features

### Free Tier
- OpenAPI spec editor with validation
- Embedded Ktor mock server (start/stop from IDE)
- Static response mocking from OpenAPI examples
- Up to 5 mock endpoints
- Basic request/response logging

### Pro Tier
- Unlimited mock endpoints
- Dynamic response generation (Faker data, templates)
- Postman collection import
- WebSocket endpoint mocking
- GraphQL mock server with schema-first design
- Request recording & replay
- Response delay simulation (latency testing)
- Custom response scripts (Kotlin DSL)
- CORS configuration
- Mock server sharing (team URLs)

### Enterprise Tier
- Contract testing integration
- Multi-service mock orchestration
- Team-shared mock configurations

## Configuration

### Settings Location
**Settings → Tools → API-First Mocking Studio**

| Setting | Default | Description |
|---------|---------|-------------|
| Server port | `8080` | Mock server listening port |
| Auto-start server | `false` | Start mock server on project open |
| Response delay (ms) | `0` | Simulated response latency |
| CORS enabled | `true` | Enable CORS headers |
| Log requests | `true` | Log incoming requests to console |
| Faker locale | `en` | Locale for generated fake data |
| GraphQL enabled | `false` | Enable GraphQL mock endpoint |
| WebSocket enabled | `false` | Enable WebSocket mock endpoints |

## Tool Windows

### Mock Server Dashboard
- **Location:** Bottom panel
- **Content:** Server status, endpoint list, request log, response editor
- **Actions:** Start/Stop server, add endpoint, import Postman collection

### API Designer
- **Location:** Editor (split view)
- **Content:** OpenAPI spec editor with live preview of available endpoints

## Actions

| Action | Description |
|--------|-------------|
| Start Mock Server | Launch embedded Ktor server |
| Stop Mock Server | Shut down mock server |
| Import Postman Collection | Import endpoints from Postman JSON |
| Add Mock Endpoint | Create a new mock endpoint |
| Export OpenAPI Spec | Export current mock configuration as OpenAPI |

## Supported File Types

- OpenAPI: `.yaml`, `.yml`, `.json`
- Postman Collections: `.postman_collection.json`
- GraphQL Schemas: `.graphql`, `.gql`
- Mock Configurations: `.mock.json`

## External Integrations

- **Ktor** — Embedded HTTP/WebSocket server
- **Postman** — Import collections for instant mocking
- **GraphQL** — Full schema-first mock support
- **Faker** — Dynamic data generation for realistic responses

## FAQ

**Q: Can I run multiple mock servers simultaneously?**
A: Yes (Pro tier). Each project can have its own server on different ports.

**Q: Does the mock server support HTTPS?**
A: Not in the current version. HTTPS support is planned.

**Q: Can I share mock configurations with my team?**
A: Yes. Export mock configs as JSON files and commit them to version control.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
