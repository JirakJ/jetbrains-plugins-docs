# Kubernetes Context Guard

> Prevent accidental kubectl commands against wrong clusters in your IDE terminal.

## Overview

Kubernetes Context Guard protects against accidentally running destructive kubectl commands on production clusters. It intercepts terminal commands, checks the active Kubernetes context, and displays confirmation dialogs with risk-level indicators before executing potentially dangerous operations.

## Installation

1. Go to **Settings → Plugins → Marketplace**
2. Search for **"Kubernetes Context Guard"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.3+, Java 17+, kubectl installed

## Features

### Free Tier
- Active context display in IDE status bar
- Production context warning (visual indicator)
- Dangerous command interception (delete, scale, drain, cordon)
- Confirmation dialogs with context name and risk level
- Up to 5 custom context rules

### Pro Tier
- Unlimited custom context rules
- Context-based command policies (allow/deny per context)
- Namespace protection rules
- Audit log of intercepted commands
- Team-shared rules via `.kube-guard.yaml`
- Context switching notifications
- Multi-cluster context groups
- Dry-run enforcement for production contexts

## Configuration

### Settings Location
**Settings → Tools → Kubernetes Context Guard**

| Setting | Default | Description |
|---------|---------|-------------|
| Production patterns | `*prod*`, `*production*` | Regex patterns for production contexts |
| Dangerous commands | `delete`, `scale`, `drain`, `cordon`, `taint` | Commands requiring confirmation |
| Block production deletes | `false` | Completely block `kubectl delete` on production |
| Show status bar | `true` | Display active context in status bar |
| Confirmation timeout (s) | `30` | Auto-cancel confirmation after timeout |

## Tool Windows

### Context Guard
- **Location:** Status bar widget + right panel
- **Content:** Active context, namespace, cluster info, recent command audit
- **Actions:** Switch context, view audit log, manage rules

## Risk Levels

| Level | Color | Trigger |
|-------|-------|---------|
| 🔴 CRITICAL | Red | `kubectl delete` on production |
| 🟠 HIGH | Orange | `kubectl scale`, `kubectl drain` on production |
| 🟡 MEDIUM | Yellow | Any write command on staging |
| 🟢 LOW | Green | Read-only commands (get, describe, logs) |

## External Integrations

- **kubectl** — Command interception via IDE terminal
- **kubeconfig** — Context detection and switching
- Part of the **DevOps Safety Kit** bundle (with Terminal Safety Rails, Local Secrets Tripwire)

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
