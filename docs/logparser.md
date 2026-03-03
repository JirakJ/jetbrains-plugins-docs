# LogParser

> Advanced log file analysis and visualization in your JetBrains IDE.

## Overview

LogParser provides powerful log file parsing, filtering, and visualization capabilities directly in the IDE. It supports multiple log formats (JSON, logback, log4j, syslog), provides real-time log tailing, and offers pattern-based highlighting with search and filtering.

## Installation

1. Go to **Settings → Plugins → Marketplace**
2. Search for **"LogParser"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.3+, Java 17+

## Features

### Free Tier
- Log file syntax highlighting (auto-detect format)
- Log level coloring (ERROR=red, WARN=yellow, INFO=blue, DEBUG=gray)
- Basic search and filter by log level
- Timestamp parsing and sorting
- Real-time file tailing (like `tail -f`)
- Up to 3 saved filter presets

### Pro Tier
- Unlimited filter presets
- Multi-file log correlation (merge logs from multiple sources)
- Regex-based filtering
- Log timeline visualization
- Exception/stack trace grouping
- Frequency analysis (errors per minute)
- Log diff (compare two log files)
- Custom log format definitions
- JSON log pretty-printing and field extraction
- Export filtered logs (CSV, JSON)
- Bookmark and annotate log lines

## Configuration

### Settings Location
**Settings → Tools → LogParser**

| Setting | Default | Description |
|---------|---------|-------------|
| Auto-detect format | `true` | Automatically detect log format |
| Tail buffer size | `10000` | Number of lines to keep in tail mode |
| Timestamp format | Auto | Custom timestamp format pattern |
| Color scheme | Default | Log level color scheme |
| Max file size (MB) | `100` | Maximum file size to open |

## Tool Windows

### Log Viewer
- **Location:** Bottom panel
- **Content:** Log file viewer with level filter, search bar, timeline, and tail controls
- **Actions:** Open log file, start tail, filter by level/regex, export

## Supported Log Formats

- JSON structured logs
- Logback/Log4j pattern layouts
- Syslog (RFC 3164, RFC 5424)
- Apache/Nginx access logs
- Custom formats (user-defined regex)

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
