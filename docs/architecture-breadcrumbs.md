# Architecture Breadcrumbs

> Visualize and navigate your project's architectural layers directly in the IDE.

## Overview

Architecture Breadcrumbs provides visual navigation breadcrumbs that show which architectural layer (Controller, Service, Repository, Domain, etc.) your current file belongs to. It enforces architectural boundaries by detecting layer violations and helps teams maintain clean architecture patterns.

## Installation

1. Go to **Settings → Plugins → Marketplace**
2. Search for **"Architecture Breadcrumbs"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.3+, Java 17+

## Features

### Free Tier
- Automatic layer detection from package/directory names
- Breadcrumb display showing current architectural context
- 6 built-in architecture patterns (Layered, Hexagonal, Clean, Onion, MVC, MVVM)
- Color-coded layer indicators in editor gutter

### Pro Tier
- Layer violation detection (e.g., Controller accessing Repository directly)
- Custom architecture pattern definitions
- Dependency flow visualization (which layers talk to which)
- Architecture compliance report generation
- Git integration — track architectural drift over time
- Team-shared architecture rules (`.arch-rules.yaml`)

## Configuration

### Settings Location
**Settings → Tools → Architecture Breadcrumbs**

| Setting | Default | Description |
|---------|---------|-------------|
| Architecture pattern | Layered | Active architecture pattern |
| Show breadcrumbs | `true` | Display layer breadcrumbs in editor |
| Show gutter icons | `true` | Show layer icons in gutter |
| Layer mapping | *(auto-detect)* | Custom package-to-layer mappings |
| Violation severity | WARNING | Severity level for layer violations |

## Tool Windows

### Architecture Overview
- **Location:** Right panel
- **Content:** Project layer map, dependency arrows, violation list
- **Actions:** Configure layers, run compliance check, export report

## Inspections

| Inspection | Severity | Description |
|-----------|----------|-------------|
| Layer Violation | WARNING | Detects cross-layer dependency violations |
| Circular Dependency | ERROR | Detects circular layer dependencies |
| Orphan Class | INFO | Classes not matching any layer pattern |

## Supported Architectures

1. **Layered** — Controller → Service → Repository → Domain
2. **Hexagonal** — Ports & Adapters pattern
3. **Clean Architecture** — Use Cases, Entities, Interfaces, Frameworks
4. **Onion** — Domain Core → Application → Infrastructure
5. **MVC** — Model, View, Controller
6. **MVVM** — Model, View, ViewModel

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
