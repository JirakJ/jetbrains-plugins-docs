# GPU Dev Accelerator Ultimate

> Cross-platform CUDA, Metal, and OpenCL development inside JetBrains IDEs — write, debug, profile, and optimize GPU code without leaving the editor.

## Overview

GPU Dev Accelerator Ultimate brings GPU compute development to IntelliJ IDEA and CLion. It adds dedicated language support for CUDA C/C++, Apple Metal Shading Language, and OpenCL C, together with in-kernel debugging, performance profiling, memory analysis, and AI-assisted kernel optimization — in a single plugin.

It targets developers building GPU-accelerated software: CUDA compute on NVIDIA hardware, Metal shaders for iOS and macOS, and cross-vendor OpenCL kernels. The plugin is published on the JetBrains Marketplace under a freemium licensing model (product code `PGPUDEVACCELERA`).

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"GPU Dev Accelerator Ultimate"**
3. Click **Install** and restart the IDE

**Requirements:** IntelliJ IDEA or CLion 2024.3+, Java 17+. The NVIDIA CUDA Toolkit is required for CUDA features; Metal features require macOS.

## Features

### GPU Language Support
- CUDA C/C++ syntax highlighting with kernel launch assistance
- Metal Shading Language support for iOS and macOS
- OpenCL C syntax highlighting and kernel compilation
- Context-aware code completion for CUDA, Metal, and OpenCL
- Dedicated file types: `.cu`, `.cuh`, `.metal`, `.cl`

### Debugging & Profiling
- Integrated cuda-gdb debugger with breakpoints inside GPU kernels
- Thread-level inspection and memory-error detection
- nvprof and Nsight Compute profiling integration
- Flame-graph visualization for performance hotspots
- Metal Performance Shaders integration

### Optimization & Analysis
- AI-powered kernel optimization suggestions
- GPU memory-leak detection via cuda-memcheck
- Occupancy analysis and warp-divergence detection
- Multi-GPU topology visualization and workload distribution
- Real-time inspections for common GPU programming mistakes

### Productivity
- CUDA and Metal run configurations
- GPU device information panel
- Keyboard shortcuts for compile, profile, and optimize (see [Actions](#actions))

## Configuration

**Settings → Tools → GPU Dev Accelerator**

This page is informational: it confirms the plugin is active with all features enabled. There are no per-field options to configure.

## Tool Windows

### GPU Profiler
- **Location:** Bottom panel
- **Content:** Profiling status and results for CUDA and Metal kernels, surfacing nvprof, Nsight Compute, Metal Performance Shaders, and real-time metrics. Run a GPU kernel to start profiling.

## Inspections

| Inspection | Level | Description |
|------------|-------|-------------|
| CUDA memory leak | Warning | Detects GPU memory leaks in CUDA code |
| CUDA kernel optimization | Weak Warning | Highlights kernels with optimization opportunities |

Both inspections apply to CUDA files, belong to the **CUDA** group, and are enabled by default.

## Actions

All actions live in the **GPU Dev** menu on the main menu bar.

| Action | Shortcut | Description |
|--------|----------|-------------|
| Compile CUDA | `Ctrl+Alt+C` | Compile CUDA source files |
| GPU Information | — | Show available GPU devices |
| Advanced CUDA Debug | `Ctrl+Shift+Alt+D` | Start advanced debugging with cuda-gdb |
| Profile with Flame Graph | `Ctrl+Alt+P` | Real-time profiling with flame graphs |
| AI Optimize Kernel | `Ctrl+Alt+O` | Get AI-powered optimization suggestions |
| Multi-GPU Topology | `Ctrl+Alt+G` | Visualize GPU topology and workload distribution |
| Advanced Memory Analysis | `Ctrl+Alt+M` | Detect memory leaks and race conditions |
| Memory Check | — | Run cuda-memcheck |
| Kernel Optimization | `Ctrl+Shift+O` | Get optimization suggestions |
| Profiling | `Ctrl+Shift+P` | Profile GPU kernel performance |

## Supported Languages & File Types

| Language | Extensions |
|----------|------------|
| CUDA C/C++ | `.cu`, `.cuh` |
| Metal Shading Language | `.metal` |
| OpenCL C | `.cl` |

## FAQ

**Does the plugin support Vulkan compute or HLSL?**
No. It provides language support for CUDA, Metal, and OpenCL only.

**Why aren't Metal features working on my machine?**
Metal support requires macOS. On other platforms, use the CUDA and OpenCL features instead.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
