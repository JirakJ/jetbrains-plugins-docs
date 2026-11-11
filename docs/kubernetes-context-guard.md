# KubeContext Safety

> Shows your active kubectl context in the IDE status bar, color-coded by environment, and asks for confirmation before you switch to production.

**Free & open source** — source: https://github.com/JirakJ/kubernetes-context-guard (Apache-2.0); contributions welcome.

## Overview

KubeContext Safety keeps your active kubectl context in plain sight. A status-bar widget shows the current context name — color-coded by environment — so you always know whether the IDE is pointed at production, staging, or a local cluster. Switching to a production context from the IDE asks for confirmation first, and a warning notification appears whenever the active context becomes a production one — including when it was changed outside the IDE.

It is aimed at developers and platform engineers who juggle several Kubernetes clusters from the IDE and want to switch contexts without dropping to a terminal.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"KubeContext Safety"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2+ and a valid kubeconfig (`~/.kube/config`, the `KUBECONFIG` environment variable, or a path set in Settings). `kubectl` on your PATH is needed only for switching contexts from the IDE.

## Features

### Context awareness
- Status-bar widget showing the current kubectl context name (and its namespace when it is not `default`)
- Color-coded environment indicator: 🔴 production, 🟡 staging, 🟢 development, ⚪ unknown
- Hover tooltip with the full context details — context name, cluster, namespace, user, and detected environment
- Automatic kubeconfig monitoring (2-second polling) that picks up context changes made outside the IDE
- Multiple `KUBECONFIG` files are merged the way kubectl does (first `current-context` wins; first definition of a context name wins)

### Production safety
- Confirmation dialog before switching to a production context (or any context whose rule has *Confirm Actions* set) — **Continue** or **Switch Away**
- Warning balloon notification when the active context becomes a production one
- Contexts that require confirmation are flagged with a ⚠️ note in the widget tooltip
- 17 built-in rules auto-classify contexts by name (prod, staging, dev, minikube, kind, k3d, and more)

### Quick switching
- Switch context from a searchable popup listing every context in your kubeconfig — no terminal required
- **Ctrl+Shift+K** shortcut, **Tools → Switch Kubernetes Context**, or a click on the status-bar widget
- Switching runs `kubectl config use-context` for you and refreshes the indicator

### Custom and team rules
- Define your own classification rules (name pattern → environment, with a confirm-actions flag) in Settings
- Share rules with your team via a `.k8s-guard.yaml` file in the project root
- Rules are evaluated in order: your Settings rules, then team rules, then the 17 built-in defaults

## Configuration

**Settings → Tools → KubeContext Safety**

| Setting | Default | Description |
|---------|---------|-------------|
| Enable KubeContext Safety | On | Turn the plugin on or off (also enables or disables the switch action) |
| Show notification on production context switch | On | Show a warning notification when the active context becomes a production one |
| Path override | *(empty)* | Custom path to the kubeconfig file; empty uses the default `~/.kube/config` |
| Custom Context Rules | *(empty)* | Table of your own rules — **Pattern**, **Environment**, **Confirm Actions** — evaluated before team rules and the built-in defaults |

### Team rules file

Place `.k8s-guard.yaml` in the project root:

```yaml
rules:
  - pattern: "*eu-prod*"
    environment: production
    confirmActions: true
  - pattern: "*sandbox*"
    environment: development
```

`environment` is one of `production`, `staging`, `development`, `unknown`. `confirmActions` (or `confirm_actions`) defaults to `true` for production rules and `false` otherwise. A top-level `contexts:` list is accepted as an alternative to `rules:`.

## Environment Color Coding

Each context is classified by matching its name against ordered glob rules (case-insensitive) — first match wins. Custom and team rules are checked before these built-in defaults.

| Indicator | Environment | Built-in name patterns |
|-----------|-------------|------------------------|
| 🔴 Red | Production | `*prod*`, `*prd*`, `*production*`, `*live*` |
| 🟡 Yellow | Staging | `*preprod*`, `*pre-prod*`, `*staging*`, `*stg*`, `*stage*`, `*uat*` |
| 🟢 Green | Development | `*dev*`, `*local*`, `*minikube*`, `*kind*`, `*docker-desktop*`, `*test*`, `*k3d*` |
| ⚪ Gray | Unknown | anything that matches no rule |

Staging patterns are evaluated before production, so names like `preprod` are not misread as production. Production patterns additionally set the *confirm-actions* flag, which triggers the confirmation dialog when switching to that context.

## Actions

| Action | Location | Shortcut | Description |
|--------|----------|----------|-------------|
| Switch Kubernetes Context | Tools menu; click the status-bar widget | `Ctrl+Shift+K` | Open a popup of all kubeconfig contexts and switch with `kubectl config use-context` (with confirmation for production contexts) |

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
