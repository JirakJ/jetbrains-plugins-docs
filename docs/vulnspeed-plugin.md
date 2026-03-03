# VulnSpeed SAST

> GPU-accelerated Static Application Security Testing with real-time vulnerability detection.

## Overview

VulnSpeed is a GPU-accelerated SAST (Static Application Security Testing) plugin that detects vulnerabilities in real-time as you write code. It covers **OWASP Top 10** and **CWE Top 25** across 7+ programming languages, provides one-click auto-fixes, and supports GPU acceleration via Metal, CUDA, or Vulkan for 50-100× faster scanning.

## Installation

1. Go to **Settings → Plugins → Marketplace**
2. Search for **"VulnSpeed"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.3+, JDK 11+, 2 GB RAM minimum, GPU optional

## Features

### Free Tier (50 scans/day, 100K LOC)
- Real-time vulnerability detection (Java, Python, JavaScript, TypeScript)
- 4 core security rules (SQL Injection, XSS, Hardcoded Credentials, Insecure Random)
- Inline severity highlighting
- One-click auto-fixes via `Alt+Enter`
- Security Dashboard tool window
- Global inspection integration

### Professional Tier
- GPU acceleration (Metal/CUDA/Vulkan)
- 3,500+ security rules across all languages
- Advanced pattern detection (taint analysis, data flow)
- AI-powered false positive filtering
- Dependency scanning
- Threat modeling
- 14-day free trial

## Configuration

### Application Settings
**Settings → Tools → VulnSpeed**

| Setting | Default | Description |
|---------|---------|-------------|
| Real-time scanning | `true` | Detect vulnerabilities as you type |
| Auto-fix enabled | `true` | Show automated fix suggestions |
| Max file size (KB) | `1000` | Maximum file size to scan |
| Telemetry | `false` | Anonymous usage data |

### Project Settings
**Project Settings → Tools → VulnSpeed**

| Setting | Default | Description |
|---------|---------|-------------|
| Exclude patterns | `**/node_modules/**`, `**/build/**`, `**/.git/**` | Paths to skip |
| Scan on save | `false` | Scan files on save |
| Auto-fix on save | `false` | Apply auto-fixes on save (Premium) |

## Tool Windows

### VulnSpeed Dashboard
- **Location:** Bottom panel
- **Content:** Vulnerability list, severity breakdown (Critical/High/Medium/Low/Info), statistics, quick-fix access
- **Columns:** File, Line, Severity, CWE, Rule Name, Suggestion

## Inspections

| Inspection | Level | Description |
|-----------|-------|-------------|
| VulnSpeed Security Analysis | WARNING | Global security inspection across all scanned files |

## Real-Time Annotators

Active for: **Java**, **Python**, **JavaScript**, **TypeScript**

Annotations show:
- Vulnerability name and severity
- CWE reference number
- Fix suggestion with code example
- Mapped to IDE highlight levels (ERROR → CRITICAL, WARNING → HIGH, etc.)

## Supported Languages

| Language | Real-Time | Project Scan |
|----------|-----------|-------------|
| Java | ✅ | ✅ |
| Python | ✅ | ✅ |
| JavaScript | ✅ | ✅ |
| TypeScript | ✅ | ✅ |
| Kotlin | — | ✅ |
| C/C++ | — | ✅ |
| Swift | — | ✅ |
| Go | — | ⚠️ Partial |
| Rust | — | ⚠️ Partial |

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Scan File | Editor right-click | Scan current file |
| Scan Project | Project view right-click | Full project scan |
| Activate License | Tools → VulnSpeed | Enter license key |
| Start Free Trial | Tools → VulnSpeed | Begin 14-day Professional trial |
| Manage Subscription | Tools → VulnSpeed | Open JetBrains Marketplace |

## Security Coverage

**Categories include:**
- Injection (SQL, LDAP, XPath, Command, NoSQL)
- Cryptography & Secrets (weak algorithms, hardcoded keys)
- Access Control (IDOR, privilege escalation)
- API Security (rate limiting, CORS, validation)
- Container Security (Docker, Kubernetes, Helm)
- Framework-Specific (Spring, React, Angular, Vue)
- Cloud/Serverless (AWS Lambda, S3, Terraform)

## GPU Acceleration

| Backend | Platform | Speedup |
|---------|----------|---------|
| Metal | macOS | 50-100× |
| CUDA | NVIDIA GPU | 50-100× |
| Vulkan | Cross-platform | 50-100× |

GPU is optional — falls back to CPU multi-threaded scanning.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
