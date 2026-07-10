# KubeContext Safety

> Shows your active kubectl context in the IDE status bar, color-coded by environment, and warns you when you are on production.

## Overview

KubeContext Safety keeps your active kubectl context in plain sight. A status-bar widget shows the current context name — color-coded by environment — so you always know whether the IDE is pointed at production, staging, or a local cluster. When a production context becomes active it raises a warning notification, giving you a glanceable safety net before a stray command lands on the wrong cluster.

It is aimed at developers and platform engineers who juggle several Kubernetes clusters from the IDE and want to switch contexts without dropping to a terminal.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"KubeContext Safety"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2+, Java 17+, `kubectl` installed and on your PATH, and a valid kubeconfig (`~/.kube/config`, or the `KUBECONFIG` environment variable).

## Features

### Context awareness
- Status-bar widget showing the current kubectl context name (and its namespace when it is not `default`)
- Color-coded environment indicator: 🔴 production, 🟡 staging, 🟢 development, ⚪ unknown
- Hover tooltip with the full context details — context name, cluster, namespace, and detected environment
- Automatic kubeconfig monitoring (2-second polling) that picks up context changes made outside the IDE

### Production safety
- Warning balloon notification when a production context becomes active
- Production (and any confirm-actions) contexts are flagged with a ⚠️ caution note in the widget tooltip
- 17 built-in rules auto-classify contexts by name (prod, staging, dev, minikube, kind, k3d, and more)

### Quick switching
- Switch context from a searchable popup listing every context in your kubeconfig — the current context is marked, no terminal required
- **Ctrl+Shift+K** shortcut, **Tools → Switch Kubernetes Context**, or a click on the status-bar widget
- Switching runs `kubectl config use-context` for you and refreshes the indicator

### Custom rules
- Define your own classification rules (name pattern → environment, with a confirm-actions flag) in Settings
- Custom rules are evaluated before the 17 built-in defaults, so you can match any cluster naming convention

## Configuration

**Settings → Tools → KubeContext Safety**

| Setting | Default | Description |
|---------|---------|-------------|
| Enable KubeContext Safety | On | Turn the plugin on or off (also enables or disables the switch action) |
| Show notification on production context switch | On | Show a warning notification when switching to a production context |
| Kubeconfig path override | *(empty)* | Custom path to the kubeconfig file; empty uses the default `~/.kube/config` |
| Custom Context Rules | *(empty)* | Table of your own rules — **Pattern**, **Environment**, **Confirm Actions** — evaluated before the 17 built-in defaults |

## Environment Color Coding

Each context is classified by matching its name against ordered glob rules (case-insensitive) — first match wins. Custom rules are checked before these built-in defaults.

| Indicator | Environment | Built-in name patterns |
|-----------|-------------|------------------------|
| 🔴 Red | Production | `*prod*`, `*prd*`, `*production*`, `*live*` |
| 🟡 Yellow | Staging | `*preprod*`, `*pre-prod*`, `*staging*`, `*stg*`, `*stage*`, `*uat*` |
| 🟢 Green | Development | `*dev*`, `*local*`, `*minikube*`, `*kind*`, `*docker-desktop*`, `*test*`, `*k3d*` |
| ⚪ Gray | Unknown | anything that matches no rule |

Staging patterns are evaluated before production, so names like `preprod` are not misread as production. Production patterns additionally set a *confirm-actions* flag, which adds the ⚠️ caution note to the status-bar tooltip and triggers the warning notification when the context becomes active.

## Actions

| Action | Location | Shortcut | Description |
|--------|----------|----------|-------------|
| Switch Kubernetes Context | Tools menu; click the status-bar widget | `Ctrl+Shift+K` | Open a popup of all kubeconfig contexts and switch with `kubectl config use-context` |

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
