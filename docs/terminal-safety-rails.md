# Terminal Safety Rails

> Intercept dangerous terminal commands before execution with risk-level confirmations.

## Overview

Terminal Safety Rails protects against accidental destructive commands by intercepting dangerous terminal inputs (`rm -rf`, `kubectl delete`, `terraform destroy`, database drops) and displaying **color-coded confirmation dialogs** with risk levels before execution. It includes 23 built-in rules across 8 categories.

## Installation

1. Go to **Settings → Plugins → Marketplace**
2. Search for **"Terminal Safety Rails"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.3+, Java 17+, Terminal plugin (bundled)

## Features

### Free Tier
- 23 built-in dangerous command rules
- 4 risk levels (🔴 CRITICAL, 🟠 HIGH, 🟡 MEDIUM, 🟢 LOW)
- Color-coded confirmation dialogs
- Up to 5 custom rules
- Enable/disable toggle

### Pro Tier
- Unlimited custom rules
- Context-aware detection
- Audit log (track all intercepted commands with ALLOWED/BLOCKED status)
- Team-shared rules via `.terminal-safety-rules.yaml`
- Statistics and analytics

## Built-in Rules (23 Total)

### 🔴 CRITICAL (8 rules)
| Pattern | Category |
|---------|----------|
| `rm -rf /` | Filesystem |
| `rm -rf ~` | Filesystem |
| `rm -rf *` | Filesystem |
| `mkfs` | System |
| `dd if=` | System |
| `DROP TABLE` | Database |
| `DROP DATABASE` | Database |
| `TRUNCATE` | Database |

### 🟠 HIGH (4 rules)
| Pattern | Category |
|---------|----------|
| `kubectl delete` | Kubernetes |
| `kubectl apply --force` | Kubernetes |
| `terraform apply` | Terraform |
| `terraform destroy` | Terraform |

### 🟡 MEDIUM (9 rules)
- `docker system prune`, `docker rm -f $(docker ps` — Docker
- `git push --force`, `git push -f`, `git reset --hard` — Git
- `chmod 777` — Permissions
- `systemctl stop`, `service ... stop` — System

## Configuration

### Settings Location
**Settings → Tools → Terminal Safety Rails**

| Setting | Default | Description |
|---------|---------|-------------|
| Enable Terminal Safety Rails | `true` | Toggle plugin on/off |
| Custom Rules | *(table)* | User-defined command patterns |

### Custom Rule Fields

| Field | Description |
|-------|-------------|
| Pattern | Glob or regex pattern |
| Risk Level | CRITICAL, HIGH, MEDIUM, or LOW |
| Category | FILESYSTEM, KUBERNETES, TERRAFORM, DOCKER, GIT, DATABASE, SYSTEM, PERMISSIONS, CUSTOM |
| Description | Human-readable explanation |
| Is Regex | Use regex instead of glob matching |

## Confirmation Dialog

When a dangerous command is detected:
- **Title:** "⚠️ Dangerous Command Detected"
- **Shows:** Risk level (color-coded), full command, matched rule description, category
- **Buttons:** "Execute Anyway" | "Cancel"
- **Size:** 500×300px modal

## Team-Shared Rules

Create `.terminal-safety-rules.yaml` in your project root:

```yaml
- pattern: "rm -rf /opt/critical"
  risk: CRITICAL
  category: FILESYSTEM
  description: "Custom destructive pattern"
  regex: false
```

Rules are automatically loaded and merged with built-in + custom rules.

## Rule Matching

1. Custom rules checked first
2. Built-in rules checked second
3. First match wins
4. Patterns support glob (`*`, `?`) or regex (when `isRegex: true`)
5. Case-insensitive matching

## External Integrations

- Part of the **DevOps Safety Kit** bundle with:
  - [Kubernetes Context Guard](kubernetes-context-guard.md)
  - [Local Secrets Tripwire](local-secrets-tripwire.md)

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
