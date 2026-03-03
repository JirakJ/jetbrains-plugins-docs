# Metal Shader Support

> Full Metal Shading Language support with live preview for JetBrains IDEs.

## Overview

Metal Shader Support provides a complete Metal Shading Language (MSL) development environment with a **custom language implementation** (lexer, parser, PSI tree), syntax highlighting for 300+ Metal keywords, code completion, inspections, and a live shader preview panel powered by JCEF.

## Installation

1. Open your JetBrains IDE
2. Go to **Settings → Plugins → Marketplace**
3. Search for **"Metal Shader Support"**
4. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.3+, Java 17+

## Features

### Free Tier
- Custom Metal language with full parser
- Syntax highlighting (300+ keywords: types, functions, qualifiers, attributes)
- Code completion for Metal API functions and types
- Brace matching and code folding
- File type association (`.metal`, `.metallib`)
- Basic error highlighting

### Pro Tier
- Live shader preview (JCEF-based rendering)
- Split editor with code + preview
- Advanced code completion (context-aware)
- Shader performance analysis
- Texture preview integration
- Cross-reference navigation (jump to function definitions)
- Metal Performance Shaders (MPS) API completion
- Shader compilation validation
- Export shader as SPIR-V

## Configuration

### Settings Location
**Settings → Tools → Metal Shader Support**

| Setting | Default | Description |
|---------|---------|-------------|
| Enable live preview | `true` | Show real-time shader preview |
| Preview resolution | 512×512 | Shader preview dimensions |
| Auto-compile on save | `true` | Compile shader on file save |
| Metal SDK path | Auto-detect | Path to Metal SDK (Xcode) |
| Show performance hints | `true` | Display shader optimization hints |

## Tool Windows

### Shader Preview
- **Location:** Right panel
- **Content:** Live shader rendering (JCEF), parameter sliders, texture inputs
- **Actions:** Compile, refresh preview, toggle wireframe

## Supported File Types

| Extension | Description |
|-----------|-------------|
| `.metal` | Metal Shading Language source |
| `.metallib` | Compiled Metal library (read-only) |
| `.mtl` | Material definitions (read-only) |

## Metal Language Features

The custom language implementation includes:

- **Lexer:** Tokenizes 300+ Metal keywords, operators, types
- **Parser:** Full MSL grammar with error recovery
- **PSI Tree:** Complete syntax tree for navigation and refactoring
- **Color Settings:** 19+ configurable syntax colors
- **Keywords:** `vertex`, `fragment`, `kernel`, `device`, `constant`, `threadgroup`, `float4`, `half4`, `texture2d`, etc.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
