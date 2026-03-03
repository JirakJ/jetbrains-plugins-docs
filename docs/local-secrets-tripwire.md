# Local Secrets Tripwire

> Detect and prevent accidental secret commits in your JetBrains IDE.

## Overview

Local Secrets Tripwire scans your code for hardcoded secrets (API keys, passwords, tokens, certificates) and prevents them from being committed to version control. It provides real-time detection with inline warnings and pre-commit hooks that block secret leaks.

## Installation

1. Go to **Settings → Plugins → Marketplace**
2. Search for **"Local Secrets Tripwire"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.3+, Java 17+

## Features

### Free Tier
- Real-time secret detection in editor (10+ patterns)
- Pre-commit scanner (blocks commits with secrets)
- Inline warnings with severity indicators
- Supported patterns: AWS keys, API tokens, passwords, private keys
- Up to 5 custom secret patterns

### Pro Tier
- 50+ secret detection patterns
- Unlimited custom patterns (regex-based)
- Entropy-based detection (high-entropy strings)
- .env file scanning
- Secret rotation reminders
- Audit log of detected secrets
- Team-shared rules via `.secrets-tripwire.yaml`
- Git history scanning (find secrets in past commits)
- Remediation suggestions (use env vars, vault references)
- CI/CD integration

## Configuration

### Settings Location
**Settings → Tools → Local Secrets Tripwire**

| Setting | Default | Description |
|---------|---------|-------------|
| Real-time scanning | `true` | Scan files as you type |
| Pre-commit check | `true` | Block commits with detected secrets |
| Entropy threshold | `4.5` | Shannon entropy threshold for detection |
| Ignore patterns | `**/test/**`, `**/*.md` | File patterns to exclude |
| Custom patterns | *(empty)* | User-defined regex patterns |

## Inspections

| Inspection | Severity | Description |
|-----------|----------|-------------|
| Hardcoded Secret | ERROR | Detected API key, password, or token in source |
| High Entropy String | WARNING | Suspicious high-entropy string found |
| .env File in VCS | ERROR | .env file not in .gitignore |

## Detected Secret Types

- AWS Access Keys (`AKIA...`)
- GitHub Tokens (`ghp_...`, `gho_...`)
- Slack Tokens (`xoxb-...`, `xoxp-...`)
- Generic API Keys (pattern-based)
- Database connection strings
- Private keys (RSA, ED25519)
- JWT tokens
- Basic Auth credentials

## External Integrations

- **Git** — Pre-commit hook integration
- Part of the **DevOps Safety Kit** bundle (with Kubernetes Context Guard, Terminal Safety Rails)

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
