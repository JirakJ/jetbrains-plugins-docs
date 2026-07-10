# Metal Shader Support

> Full Metal Shading Language support for JetBrains IDEs — editing, inspections, live preview, and GPU profiling.

## Overview

Metal Shader Support is a complete Metal Shading Language (MSL) development environment for JetBrains IDEs, built on a custom Metal language implementation (lexer, parser, and PSI tree). It provides syntax highlighting, context-aware code completion across 300+ built-in functions, live templates, real-time error detection, and inspections.

Beyond editing, it adds a live shader preview, a debugger and GPU profiler, a one-click shader optimizer, a complexity analyzer, and a cross-platform transpiler that converts Metal to SPIR-V, HLSL, or WGSL. It targets Metal 3.2 and Metal 4.0 for iOS, macOS, and visionOS development.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"Metal Shader Support"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2023.2+ (IntelliJ IDEA, CLion, and other IntelliJ-based IDEs), JDK 21+. macOS is recommended — Metal is an Apple-only framework.

## Features

### Language Support
- Metal 3.2 and Metal 4.0 syntax highlighting
- Keywords (`kernel`, `vertex`, `fragment`, `device`, `threadgroup`) and types (`float4`, `texture2d`, `sampler`, matrices, vectors)
- Attribute qualifiers: `[[texture(0)]]`, `[[buffer(0)]]`, `[[stage_in]]`
- 300+ built-in functions with inline (quick) documentation
- Raytracing and mesh shader support (Metal 4.0)
- Customizable syntax colors (**Settings → Editor → Color Scheme → Metal**)

### Code Editing
- Context-aware code completion with parameter hints
- Metal Performance Shaders (MPS) API completion
- Live templates for vertex, fragment, and compute shaders
- Code folding, formatting, and structure view
- Comment/uncomment, brace matching, and quote handling
- Find usages

### Error Detection & Analysis
- Real-time threadgroup size validation (configurable max, default 1024 threads)
- Texture access bounds checking
- Attribute format validation
- Vector swizzle validation
- Performance inspection with optimization hints

### Shader Preview & GPU Tools
- Live shader preview at up to 60 FPS in a dedicated tool window
- Metal debugger panel with variable inspection
- GPU profiler with cycle estimation and bottleneck detection
- One-click shader optimizer
- Shader complexity analyzer
- Cross-platform transpiler: Metal → SPIR-V, HLSL, or WGSL

## Configuration

**Settings → Tools → Metal Shader Support**

| Setting | Default | Description |
|---------|---------|-------------|
| Max threadgroup size | `1024` | Maximum threads per threadgroup used during validation |
| Enable real-time shader preview | On | Render shaders live in the preview tool window |
| Preview FPS cap | `60` | Upper frame-rate limit for the live preview |
| Transpiler target | `SPIR-V` | Output language for the transpiler (SPIR-V, HLSL, or WGSL) |
| Enable performance inspections | On | Toggle Metal performance/optimization hints |

## Tool Windows

### Metal Shader Preview
- **Location:** Right panel
- **Content:** Live shader rendering

### Metal Debugger
- **Location:** Bottom panel
- **Content:** Variable inspection during shader debugging

### Metal Profiler
- **Location:** Bottom panel
- **Content:** GPU performance metrics, cycle estimates, and bottleneck detection

## Inspections

| Inspection | Level | Description |
|-----------|-------|-------------|
| Metal Performance Hints | Warning | Flags shader performance issues and suggests optimizations (enabled by default) |

## Actions

Available under **Tools → Metal Shader Support**.

| Action | Location | Description |
|--------|----------|-------------|
| Analyze Shader Complexity | Tools menu; editor context menu | Analyze shader performance and complexity |
| Profile Shader Performance | Tools menu | Estimate GPU cycles and identify bottlenecks |
| Validate Shader | Tools menu | Advanced shader validation and error detection |
| Optimize Shader | Tools menu | Automatic shader optimization suggestions |
| GPU Profiler | Tools menu | Detailed GPU performance analysis |
| Transpile Shader | Tools menu | Convert Metal shaders to SPIR-V, HLSL, or WGSL |

## Supported File Types

| Extension | Notes |
|-----------|-------|
| `.metal`, `.msl` | Metal Shading Language source |
| `.mm`, `.h`, `.hpp` | Objective-C++ and header files containing Metal code |

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
