# API First & Mocking Studio

> Design, test, and mock HTTP APIs from an OpenAPI spec without leaving your JetBrains IDE.

## Overview

API First & Mocking Studio is a native API client and mocking tool for JetBrains IDEs. It parses OpenAPI 3.0/3.1 and Swagger 2.0 specifications, turns them into runnable requests, and can spin up an embedded Ktor mock server directly from the spec. Around that spec-driven core it provides a full request builder — environments, authentication, scripting, assertions, collections, and history — comparable to a standalone REST client, plus WebSocket support and client-code generation.

It is aimed at developers who follow an API-first workflow and want to design, exercise, and mock endpoints inside the editor instead of switching to an external tool.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"API First & Mocking Studio"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2025.1+ with Java support (IntelliJ IDEA or Android Studio) — the plugin depends on the platform Java module.

## Features

- **Spec parsing** — read OpenAPI 3.0/3.1 and Swagger 2.0 documents (YAML or JSON).
- **API Explorer tool window** — compose and send HTTP requests with method, URL, params, headers, and body.
- **Request bodies** — Raw, Form-Data, x-www-form-urlencoded, and GraphQL (query + variables).
- **Authentication** — None, Bearer Token, Basic Auth, API Key, and OAuth 2.0 (with token fetch).
- **Environments** — named variable sets with an active-environment selector.
- **Cookie management** — a per-project cookie jar.
- **Pre-request & post-response scripting** — inject variables before a request and extract values from the response into variables.
- **Tests / assertions** — assert on response fields such as status code, with a dedicated Test Results view.
- **Collections & history** — save requests into collections and browse past requests in History.
- **Import / export** — import OpenAPI specs, Postman v2.1 collections, cURL commands, and previously exported collections; export collections to JSON.
- **Code generation** — produce request snippets (cURL, Python Requests, JavaScript Fetch) and a JetBrains `.http` client file from a spec.
- **Embedded mock server** — start a Ktor mock server generated from the loaded OpenAPI spec.
- **WebSocket client** — connect to a WebSocket endpoint and send/receive messages.

## Configuration

**Settings → Tools → API First & Mocking Studio**

| Setting | Default | Description |
|---------|---------|-------------|
| Request timeout (ms) | `30000` | Timeout for outgoing HTTP requests, in milliseconds |
| Follow redirects | On | Automatically follow HTTP redirect responses |
| Verify SSL certificates | On | Validate TLS/SSL certificates when sending requests |
| Max history size | `100` | Maximum number of requests retained in History |
| Mock server port | `8085` | Port for the embedded mock server |

## Tool Windows

### API Explorer
- **Location:** right panel
- **Content:** a complete API client. A request bar (method selector, URL, **Send**) sits above the request tabs — **Params, Auth, Pre-Script, Body, Headers, Tests, Snippets, Post-Script** — and the response tabs — **Body, Tree, Headers, Test Results**. A sidebar holds **History** and **Collections**, and a WebSocket panel provides Connect/Disconnect and message sending.

## Actions

Available from the API Explorer tool window (toolbar buttons; no default keyboard shortcuts).

| Action | Location | Description |
|--------|----------|-------------|
| Import OpenAPI | Collections toolbar | Import requests from an OpenAPI/Swagger file |
| Import Postman Collection | Collections toolbar | Import a Postman v2.1 collection (JSON) |
| Import Collection | Collections toolbar | Import a previously exported collection (JSON) |
| Export Collection | Collections toolbar | Export the selected collection to JSON |
| Import cURL | Request bar | Create a request by pasting a cURL command |
| Manage Environments | Request bar | Create and edit environment variable sets |
| Cookies | Request bar | Open the cookie jar manager |
| Generate HTTP File | API Explorer | Generate a JetBrains `.http` file from the loaded spec |
| Start / Stop Mock Server | API Explorer | Start or stop the embedded Ktor mock server built from the loaded spec |

## Supported Formats

- **OpenAPI 3.0 / 3.1 and Swagger 2.0** specs (YAML or JSON) — import
- **Postman v2.1 collections** (JSON) — import
- **Collections** (JSON) — import and export
- **cURL** commands — import
- **JetBrains HTTP Client** (`.http`) — generated
- Snippet output: **cURL**, **Python (Requests)**, **JavaScript (Fetch)**

## FAQ

**Q: Which IDEs can run the plugin?**
A: Any JetBrains IDE on 2025.1 or newer that includes Java support, such as IntelliJ IDEA (Community or Ultimate) and Android Studio. The plugin depends on the platform Java module.

**Q: Can I reuse an existing API definition?**
A: Yes. Import an OpenAPI/Swagger spec or a Postman v2.1 collection from the Collections toolbar, or generate a JetBrains `.http` file from a loaded spec.

**Q: How do I mock an API?**
A: Load an OpenAPI spec, then use **Start Mock Server** to run an embedded Ktor server generated from it. The port is set under Settings → Tools → API First & Mocking Studio.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
