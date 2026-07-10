# Endpoint Map

> Discover, index, and navigate every HTTP API endpoint in your project — then jump straight to the code that defines it.

## Overview

Endpoint Map scans your project for HTTP route definitions and collects them into a single, searchable index. It recognizes endpoints across five popular web frameworks — Spring / Spring Boot, JAX-RS, Express.js, Flask, and FastAPI — so Java, JavaScript/TypeScript, and Python services in the same repository all show up in one place.

Once scanned, endpoints appear in a dedicated tool window where you can search by path, filter by HTTP method, and group routes by controller, path prefix, or method. Double-click any endpoint (or use the **Navigate to Endpoint** popup) to open the exact source file and line where the route is declared. Detection is extensible: add your own regular-expression patterns to cover frameworks that aren't built in.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Endpoint Map"**
3. Click **Install** and restart the IDE

**Requirements:** any IntelliJ-based IDE (IntelliJ IDEA, WebStorm, PyCharm, GoLand, …), version **2023.2 or later**. The plugin depends only on the core platform, so it runs in every IntelliJ-based product.

## Features

### Free Tier
- Project-wide endpoint scanning (**Tools → Scan Endpoints**), run as a background task
- **Endpoint Map** tool window with live search and an HTTP-method filter
- Jump-to-source navigation — double-click an endpoint, or use **Navigate to Endpoint** (Ctrl+Alt+E)
- Endpoint grouping by controller, path prefix, or HTTP method

### Pro Tier ($5.90/month)
- Unlimited endpoint indexing
- Multi-framework detection patterns
- Advanced grouping
- Endpoint export

## Supported Frameworks & File Types

Built-in detection patterns:

| Framework | Detects |
|-----------|---------|
| Spring / Spring Boot | `@GetMapping`, `@PostMapping`, `@PutMapping`, `@DeleteMapping`, `@PatchMapping`, `@RequestMapping` |
| JAX-RS | `@GET` / `@POST` / `@PUT` / `@DELETE` paired with `@Path` |
| Express.js | `app.get(...)` / `router.post(...)` and other `.get` / `.post` / `.put` / `.delete` / `.patch` calls |
| Flask | `@app.route("...", methods=[...])` |
| FastAPI | `@app.get(...)` / `.post` / `.put` / `.delete` / `.patch` |

Recognized HTTP methods (used for the tool-window filter): GET, POST, PUT, DELETE, PATCH, HEAD, OPTIONS.

The scanner reads `.java`, `.kt`, `.kts`, `.js`, `.ts`, `.mjs`, `.py`, `.go`, and `.rb` source files. Frameworks without a built-in pattern (for example Go or Ruby routers) can be detected by adding **Custom Patterns** in settings.

## Configuration

**Settings → Tools → Endpoint Map**

| Setting | Default | Description |
|---------|---------|-------------|
| Enabled Frameworks | Spring, JAX-RS, Express, Flask, FastAPI | Which built-in pattern sets are used when scanning |
| Grouping Mode | Group by Controller | How endpoints are grouped in the tool window: Controller, Path Prefix, or HTTP Method |
| Excluded Directories | `node_modules, build, dist, target, .gradle, .git, __pycache__, venv` | Comma-separated directory names skipped during scanning |
| Custom Patterns | (empty) | Extra detection rules, one per line, in the format `regex\|HTTP_METHOD\|framework` |
| Automatically scan on project open | Enabled | Run a scan automatically when the project is opened |

## Tool Windows

### Endpoint Map
- **Location:** right tool-window panel
- **Content:** a search field, an HTTP-method filter dropdown, a grouped tree of endpoints, and a status bar showing how many endpoints are displayed out of the total. Double-click an endpoint node to open its source location.

## Actions

| Action | Location | Shortcut | Description |
|--------|----------|----------|-------------|
| Scan Endpoints | Tools menu | — | Scans the whole project for API endpoints in the background and reports how many were found |
| Navigate to Endpoint | Navigate menu | Ctrl+Alt+E | Opens a searchable popup of all indexed endpoints; choosing one jumps to its source |

## FAQ

**A scan finished but the tool window is empty — why?**
Make sure the relevant framework is checked under **Settings → Tools → Endpoint Map → Enabled Frameworks**, and that your source folder isn't listed in **Excluded Directories**. Only the five built-in frameworks are detected automatically.

**How do I detect a framework that isn't built in?**
Add a **Custom Pattern** in settings using the format `regex|HTTP_METHOD|framework`. The pattern's capture group should contain the endpoint path.

**Nothing happens when I press Ctrl+Alt+E.**
The Navigate popup lists already-indexed endpoints, so run **Tools → Scan Endpoints** first. If none exist yet, the plugin prompts you to scan.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
