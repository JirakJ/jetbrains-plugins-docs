# GPU Dev Accelerator Ultimate

> GPU-accelerated development tools for CUDA, OpenCL, and Vulkan Compute in JetBrains IDEs.

## Overview

GPU Dev Accelerator Ultimate provides comprehensive GPU compute development support including syntax highlighting, code completion, kernel debugging, performance profiling, and memory analysis for CUDA, OpenCL, and Vulkan Compute shaders.

## Installation

1. Go to **Settings → Plugins → Marketplace**
2. Search for **"GPU Dev Accelerator Ultimate"**
3. Click **Install** and restart the IDE

**Requirements:** JetBrains IDE 2024.3+, Java 17+, GPU SDK (CUDA Toolkit, OpenCL SDK, or Vulkan SDK)

## Features

### Free Tier
- Syntax highlighting for CUDA (`.cu`, `.cuh`), OpenCL (`.cl`), and Vulkan Compute (`.comp`)
- Basic code completion for GPU API functions
- Kernel launch configuration validation
- GPU device detection and info display
- Error highlighting for common GPU programming mistakes

### Pro Tier
- Advanced code completion with parameter hints
- Kernel performance profiling (occupancy calculator)
- Memory access pattern analysis
- Warp/wavefront efficiency visualization
- Bank conflict detection
- Shared memory optimization suggestions
- GPU memory leak detection
- Multi-GPU configuration support
- Kernel launch parameter optimizer
- CUDA ↔ OpenCL code conversion hints

## Configuration

### Settings Location
**Settings → Tools → GPU Dev Accelerator Ultimate**

| Setting | Default | Description |
|---------|---------|-------------|
| CUDA Toolkit path | Auto-detect | Path to CUDA installation |
| OpenCL SDK path | Auto-detect | Path to OpenCL SDK |
| Vulkan SDK path | Auto-detect | Path to Vulkan SDK |
| Target GPU arch | Auto-detect | Target compute capability |
| Show performance hints | `true` | Display optimization suggestions |

## Tool Windows

### GPU Dashboard
- **Location:** Bottom panel
- **Content:** GPU device info, kernel profiling results, memory usage, occupancy metrics
- **Actions:** Profile kernel, analyze memory, detect conflicts

## Supported File Types

| Extension | Language |
|-----------|----------|
| `.cu`, `.cuh` | CUDA C/C++ |
| `.cl` | OpenCL C |
| `.comp` | Vulkan Compute (GLSL) |
| `.hlsl` | DirectX Compute (read-only) |

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
