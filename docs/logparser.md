# LogParser Pro

> Advanced log analysis, filtering, and visualization directly inside your JetBrains IDE.

## Overview

LogParser Pro brings professional log analysis into your JetBrains IDE, so you no longer have to switch between the editor and an external viewer. It renders `.log` and `.out` files in a dedicated editor and tool window with colour-coded severity levels, live filtering and search, pattern auto-detection, correlation-ID tracing, latency and exception analysis, and statistical anomaly detection. Structured (JSON / logfmt), gzip-compressed, and ANSI-coloured logs are all handled.

The plugin is published on the JetBrains Marketplace as a freemium listing (product code `PLOGPARSERPRO`).

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"LogParser Pro"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2025.1+ · JDK 17+

## Features

### Viewing & formats
- **ANSI colour rendering** — the *ANSI View* tab replays CI, Docker, npm, and pytest logs with their terminal colours resolved (16/256-colour, 24-bit truecolour, bold, italic, underline)
- **Colour-coded levels** — ERROR, WARN, INFO, DEBUG, and TRACE highlighted in the editor
- **Dedicated log editor** — table view for `.log` and `.out` files
- **Structured logs** — JSON and logfmt parsing that extracts timestamp, level, message, and arbitrary fields
- **Gzip support** — transparent reading of `*.log.gz` (by name or magic number)
- **Pattern library** — auto-detection of Spring Boot, Node.js, Python, and Java log formats
- **Stack trace folding** — collapse exception stack traces for readability

### Filtering & search
- **Log level filtering** — toggle buttons to filter by severity
- **Keyword search** — live filtering across entries
- **Advanced search** — regex, fuzzy, and proximity search backed by a log index
- **Correlation ID tracking** — follow a request flow across microservices and sources

### Analysis
- **Exception grouping** — group stack traces by normalised signature (line numbers, lambdas, hashes ignored) into a ranked report
- **Error timeline** — minute-granularity histogram with z-score spike detection
- **Latency analysis** — extract durations (e.g. `123ms`, `1.2s`, `900µs`) and report p50/p90/p95/p99 plus the slowest entries, using deterministic nearest-rank percentiles
- **Log diff** — compare two logs by normalised signature (digits, UUIDs, timestamps collapsed)
- **Anomaly detection** — statistical pattern discovery and anomaly scoring
- **Statistics dashboard** — level distribution, top loggers, and entries over time

### Sharing & export
- **Secret redaction** — mask emails, JWTs, Bearer tokens, AWS/Stripe keys, Luhn-verified credit cards, IPs, UUIDs, and password assignments before sharing a log
- **Strip ANSI to file** — write a clean, paste-friendly plain-text copy
- **Safe export** — CSV (RFC-4180 with formula-injection mitigation), JSON, or a self-contained HTML report with escaped content
- **Grok pattern compiler** — compile an Elastic Grok subset to native regex for custom extractors

## Configuration

**Settings → Tools → LogParser Pro**

| Setting | Default | Description |
|---------|---------|-------------|
| Max lines to parse | `100000` | Upper bound on the number of lines read from a file |
| Default filter level | `ALL` | Initial severity filter (ALL, ERROR, WARN, INFO, DEBUG, TRACE) |
| Date format pattern | `yyyy-MM-dd HH:mm:ss.SSS` | Pattern used to parse and display timestamps |
| Font size for log viewer | `12` | Log viewer font size (8–48) |
| Export format preference | `CSV` | Default export format (CSV, JSON, Plain Text) |
| Show line numbers | `On` | Show line numbers in the log viewer |
| Auto-refresh on file change | `Off` | Reload the view when the file changes on disk |
| Use theme-aware colors | `On` | Adapt level colours to the active IDE theme |
| Wrap long lines in editor | `Off` | Soft-wrap long log lines |
| Custom correlation ID patterns | *(empty)* | Comma-separated regexes used to detect correlation IDs |

## Tool Windows

### LogParser Pro
- **Location:** bottom panel
- **Tabs:** Log Viewer, Search, Correlation, Statistics, and ANSI View

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Track Transaction ID | Tools → LogParser Pro | Track a correlation ID across sources |
| Analyze Log | Tools → LogParser Pro | Run full analysis on the current log file |
| Group Exceptions | Tools → LogParser Pro | Group stack traces by normalised signature into a ranked report |
| Show Error Timeline | Tools → LogParser Pro | Build a minute-granularity timeline with z-score spike detection |
| Analyze Latency | Tools → LogParser Pro | Extract durations and report p50/p90/p95/p99 plus the slowest entries |
| Export Log… | Tools → LogParser Pro | Export parsed entries to CSV, JSON, or a self-contained HTML report |
| Redact Secrets to File… | Tools → LogParser Pro | Write a copy of the log with secrets, PII, and tokens masked |
| Strip ANSI to File… | Tools → LogParser Pro | Write a copy of the log with all ANSI escape sequences removed |
| Diff With Another Log… | Tools → LogParser Pro | Compare the current log against another file by normalised signature |
| Extract Pattern | Editor right-click menu | Extract a pattern from the selected text |
| Find Correlation ID | Editor right-click menu | Find a correlation ID in the selected text |

## Supported Files & Formats

- **File types:** `.log` and `.out` (opened in the dedicated log editor); gzip-compressed `*.log.gz`
- **Auto-detected layouts:** Spring Boot, Node.js, Python, and Java
- **Structured formats:** JSON and logfmt (timestamp / level / message / arbitrary fields)

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
