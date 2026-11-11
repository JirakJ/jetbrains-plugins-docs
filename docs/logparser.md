# LogParser Pro

> Log analysis, filtering, and visualization directly inside your JetBrains IDE.

**Free & open source** — source: https://github.com/JirakJ/logparser-premium-plugin (Apache-2.0); contributions welcome.

## Overview

LogParser Pro brings log analysis into your JetBrains IDE, so you no longer have to switch between the editor and an external viewer. It opens `.log` and `.out` files in a dedicated table editor with colour-coded severity levels, level filtering, live search, and stack trace folding. Around that, it groups exceptions, builds an error timeline with spike detection, tracks correlation IDs across services, diffs two logs, and redacts secrets before you share a file. Structured (JSON / logfmt) and gzip-compressed logs are handled transparently.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"LogParser Pro"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2025.1+.

## Features

### Viewing & formats
- **Colour-coded levels** — ERROR, WARN, INFO, DEBUG, and TRACE highlighted for instant visibility
- **Dedicated log editor** — table view for `.log` and `.out` files, with an **Export** button for the filtered entries
- **Structured logs** — JSON and logfmt parsing that extracts timestamp, level, message, and arbitrary fields
- **Gzip support** — transparent reading of `*.log.gz` and other gzip-encoded logs
- **Pattern library** — auto-detection of Spring Boot, Node.js, Python, and Java log formats
- **Stack trace folding** — collapse exception stack traces for readability

### Filtering & search
- **Log level filtering** — toggle buttons to filter by severity
- **Keyword search** — live filtering across entries
- **Advanced search** — regex, fuzzy (Levenshtein), and plain-text search
- **Correlation ID tracking** — follow a request flow across microservices

### Analysis
- **Exception grouping** — group stack traces by normalised signature (line numbers, lambdas, hashes ignored) into a ranked report
- **Error timeline** — minute-granularity histogram with z-score spike detection
- **Log diff** — compare two logs by normalised message signature (digits, UUIDs, timestamps collapsed)
- **Anomaly detection** — statistical pattern discovery and anomaly scoring
- **Statistics dashboard** — level distribution, top loggers, and entries over time

### Sharing & export
- **Secret redaction** — mask emails, JWTs, Bearer tokens, AWS and Stripe keys, Luhn-verified credit cards, IPs, UUIDs, and password assignments before sharing a log
- **Safe export** — CSV (RFC-4180 with formula-injection mitigation), JSON, or a standalone HTML report with escaped content

## Configuration

**Settings → Tools → LogParser Pro**

| Setting | Default | Description |
|---------|---------|-------------|
| Max lines to parse | `100000` | Upper bound on the number of lines read from a file |
| Font size for log viewer | `12` | Log viewer font size (8–48) |
| Editor export format | `CSV` | Format used by the log editor's **Export** button (CSV, JSON, Plain Text) |
| Use theme-aware colors | On | Adapt level colours to the active IDE theme |

## Tool Windows

### LogParser Pro
- **Location:** Bottom panel
- **Tabs:** Log Viewer, Search, Correlation, and Statistics

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Track Transaction ID | Tools → LogParser Pro | Track a correlation ID across sources |
| Analyze Log | Tools → LogParser Pro | Run full analysis on the current log file |
| Group Exceptions | Tools → LogParser Pro | Group stack traces by normalised signature and show a ranked report |
| Show Error Timeline | Tools → LogParser Pro | Build a minute-granularity timeline with z-score spike detection |
| Export Log… | Tools → LogParser Pro | Export parsed entries to CSV, JSON, or a self-contained HTML report |
| Redact Secrets to File… | Tools → LogParser Pro | Write a copy of the log with secrets, PII, and tokens masked |
| Diff With Another Log… | Tools → LogParser Pro | Compare the current log against another file by normalised signature |
| Extract Pattern | Editor context menu → LogParser Pro | Extract a pattern from the selected text |
| Find Correlation ID | Editor context menu → LogParser Pro | Find a correlation ID in the selected text |

## Supported Files & Formats

- **File types:** `.log` and `.out` (opened in the dedicated log editor); gzip-compressed `*.log.gz`
- **Auto-detected layouts:** Spring Boot, Node.js, Python, and Java
- **Structured formats:** JSON and logfmt (timestamp / level / message / arbitrary fields)

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
