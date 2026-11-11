# API First & Mocking Studio

> Design, test, and mock HTTP APIs from an OpenAPI spec without leaving your JetBrains IDE.

**Free & open source** — source: https://github.com/JirakJ/api-first-mocking-studio (Apache-2.0); contributions welcome.

## Overview

API First & Mocking Studio is a native API client and mocking tool for JetBrains IDEs. Its **API Explorer** tool window lets you compose and send HTTP requests with environments, authentication, scripts, assertions, collections, and history. From an OpenAPI 3.0/3.1 or Swagger 2.0 file it can import requests, serve every operation from a local mock server, and generate a JetBrains HTTP Client (`.http`) file.

It is aimed at developers who follow an API-first workflow and want to design, exercise, and mock endpoints inside the editor instead of switching to an external tool.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"API First & Mocking Studio"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2025.1+ with Java support (for example IntelliJ IDEA or Android Studio) — the plugin depends on the platform Java module.

## Features

- **API Explorer tool window** — compose requests with method, URL, query params, headers, and body, and view the response as text, a JSON tree, and headers.
- **Request bodies** — Raw, Form-Data (multipart), x-www-form-urlencoded, and GraphQL (query + variables).
- **Authentication** — None, Bearer Token, Basic Auth, API Key, and OAuth 2.0.
- **Environments & variables** — `{{variable}}` placeholders resolved from global variables and the active environment (*Dev* and *Prod* are created by default). Values are stored as plain text in the project's `.idea` settings, so keep real secrets out of them.
- **Cookies** — a per-project cookie jar with a manager dialog.
- **Pre-request scripts** — set variables with `name=value` lines, including `{{$timestamp}}` and `{{$guid}}`.
- **Post-response scripts** — extract values from the response into variables with `name=$.json.path`.
- **Tests / assertions** — status code, body contains, and JSONPath match, with a Test Results view.
- **Collections & history** — save requests into collections and browse past requests in History.
- **Import / export** — import OpenAPI 3.0/3.1 and Swagger 2.0 specs (JSON or YAML), Postman v2.x collections (folders are flattened), cURL commands, and the plugin's own collection JSON; export collections to JSON.
- **Code snippets** — cURL, Python (Requests), and JavaScript (Fetch) for the current request.
- **WebSocket client** — enter a `ws://` or `wss://` URL to connect and send/receive messages.
- **Mock server** — serves every operation of an OpenAPI/Swagger file on `127.0.0.1`, responding with the spec's examples or schema-generated sample JSON.
- **HTTP Client file generation** — creates a JetBrains `.http` file with one request per operation.

## Configuration

**Settings → Tools → API First & Mocking Studio** (per project)

| Setting | Default | Description |
|---------|---------|-------------|
| Request timeout (ms) | `30000` | Timeout for outgoing HTTP requests, in milliseconds |
| Follow redirects | On | Automatically follow HTTP redirect responses |
| Max history size | `100` | Maximum number of requests retained in History (oldest are dropped first) |
| Mock server port (127.0.0.1) | `8085` | Port for the local mock server |

## Tool Windows

### API Explorer
- **Location:** Right panel
- **Content:** A request bar (environment selector, **Manage Environments**, **Cookies**, method, URL, **Send**) above the request tabs — **Params, Auth, Pre-Script, Body, Headers, Tests, Snippets, Post-Script** — and the response tabs — **Body, Tree, Headers, Test Results**. A sidebar holds **History** and **Collections**.

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Start Mock Server… / Stop Mock Server | Tools → API First | Serve sample responses for every operation of an OpenAPI/Swagger file on `127.0.0.1` |
| Generate HTTP Client File… | Tools → API First | Generate a JetBrains HTTP Client (`.http`) file from an OpenAPI/Swagger file |
| Import OpenAPI | API Explorer → Collections | Import requests from an OpenAPI/Swagger file |
| Import Postman Collection | API Explorer → Collections | Import a Postman v2.x collection (JSON) |
| Import Collection | API Explorer → Collections | Import a previously exported collection (JSON) |
| Export Collection | API Explorer → Collections | Export the selected collection to JSON |
| Import cURL | API Explorer request bar | Create a request by pasting a cURL command |

## Supported Formats

- **OpenAPI 3.0 / 3.1 and Swagger 2.0** specs (YAML or JSON) — import, mock server, `.http` generation
- **Postman v2.x collections** (JSON) — import
- **Collections** (JSON) — import and export
- **cURL** commands — import
- Snippet output: **cURL**, **Python (Requests)**, **JavaScript (Fetch)**

## FAQ

**Q: Which IDEs can run the plugin?**
A: Any JetBrains IDE on 2025.1 or newer that includes Java support, such as IntelliJ IDEA and Android Studio.

**Q: How do I mock an API?**
A: Choose **Tools → API First → Start Mock Server…** and pick an OpenAPI/Swagger file. Every operation is served on `127.0.0.1` at the port set in Settings → Tools → API First & Mocking Studio. Run the action again to stop the server.

**Q: Are environment variables stored securely?**
A: No — they are saved as plain text in the project's `.idea` settings. Do not put real secrets in them.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
