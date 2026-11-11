# Metal Shader Support

> Metal Shading Language editing for JetBrains IDEs — highlighting, completion, documentation, static checks, and analysis tools.

**Free & open source** — source: https://github.com/JirakJ/metal-shader-support-plugin (Apache-2.0); contributions welcome.

## Overview

Metal Shader Support adds editing support for Metal Shading Language (MSL) files to JetBrains IDEs, built on a custom Metal language implementation (lexer, parser, and PSI tree). It provides syntax highlighting, completion, quick documentation, live and file templates, static checks, and a handful of analysis tools.

All analysis is static — the plugin does not compile, run, or profile shaders on a GPU.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Metal Shader Support"**
3. Click **Install** and restart the IDE

**Requirements:** Any JetBrains IDE 2024.2+.

## Features

### Editing
- Syntax highlighting for MSL keywords, types, attributes, and built-in functions (including Metal 3/4 ray tracing and mesh shader names)
- Completion for keywords, types, attributes, built-ins, and Metal Performance Shaders class names
- Quick documentation for common built-ins
- 7 live templates (vertex, fragment, and compute kernels, …) and 3 file templates (Metal Shader, Metal Kernel, Metal Header)
- Code folding, formatting, structure view, find usages, comments, brace and quote matching
- Customizable syntax colors (**Settings → Editor → Color Scheme → Metal**)

### Checks
- Annotations: threadgroup size over 1024, duplicate `[[buffer(n)]]` / `[[texture(n)]]` bindings, attribute format, invalid swizzles
- Performance hints: thread-ID-dependent branches, repeated texture reads, large threadgroup allocations, `pow(x, 2)`, `1.0/sqrt()`, expensive functions in loops

### Analysis tools
- **Analyze Shader Complexity**, **Profile Shader Performance** — static instruction counts and rough cycle estimates
- **Validate Shader** — additional static validation
- **Optimize Shader** — suggested rewrites you can apply
- **Transpile Shader** — best-effort, regex-based starting point in HLSL, WGSL, or SPIR-V assembly (always review the output)

## Inspections

| Inspection | Level | Description |
|-----------|-------|-------------|
| Metal Performance Hints (group *Metal*) | Warning | Flags shader performance issues and suggests optimizations (enabled by default) |

## Actions

| Action | Location | Description |
|--------|----------|-------------|
| Analyze Shader Complexity | Tools → Metal Shader Support; editor context menu | Analyze shader performance and complexity |
| Profile Shader Performance | Tools → Metal Shader Support | Estimate GPU cycles and identify bottlenecks (static) |
| Validate Shader | Tools → Metal Shader Support | Additional static validation |
| Optimize Shader | Tools → Metal Shader Support | Suggest optimizing rewrites |
| Transpile Shader | Tools → Metal Shader Support | Convert a Metal shader to SPIR-V, HLSL, or WGSL (best effort) |

## Supported File Types

| Extension | Notes |
|-----------|-------|
| `.metal`, `.msl` | Metal Shading Language source |

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
