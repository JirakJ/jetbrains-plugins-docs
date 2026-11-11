# GPU Dev Accelerator Ultimate

> CUDA, Metal, and OpenCL development inside JetBrains IDEs — write, compile, inspect, and analyze GPU code without leaving the editor.

**Free & open source** — source: https://github.com/JirakJ/gpu-dev-accelerator-ultimate (Apache-2.0); contributions welcome.

## Overview

GPU Dev Accelerator Ultimate adds language support for CUDA C/C++, Apple Metal Shading Language, and OpenCL C to JetBrains IDEs, together with toolchain integration (nvcc, compute-sanitizer, Nsight Compute, nvidia-smi) and deterministic static analysis of GPU kernels. Every feature is backed by a real tool integration or a readable heuristic — there is no mock data.

It targets developers building GPU-accelerated software: CUDA compute on NVIDIA hardware, Metal shaders for Apple platforms, and cross-vendor OpenCL kernels.

## Installation

1. Open **Settings → Plugins → Marketplace**
2. Search for **"GPU Dev Accelerator Ultimate"**
3. Click **Install** and restart the IDE

**Requirements:** Any IntelliJ-based IDE 2023.2+. The NVIDIA CUDA Toolkit is required for compile, profile, and sanitizer features; Apple GPU detection requires macOS.

## Features

### GPU language support
- Syntax highlighting for CUDA C/C++, Metal Shading Language, and OpenCL C (`.cu`, `.cuh`, `.metal`, `.cl`)
- Code completion with API signatures for 100+ GPU builtins across all three languages
- Quick documentation (`Ctrl+Q`) for kernel qualifiers, builtins, atomics, and warp primitives
- Line/block commenting (`Ctrl+/`) and brace matching
- Live templates: kernel skeletons, grid-stride loops, `CUDA_CHECK` macro, event timing, shared-memory tiles (see below)

### Toolchain integration
- Compile CUDA files with nvcc in the background — errors are clickable in the GPU Dev console
- Show PTX for the current file to inspect generated code
- Memory checking via compute-sanitizer (or cuda-memcheck)
- Kernel profiling via Nsight Compute (`ncu`) or nvprof
- GPU inventory from `nvidia-smi` and `system_profiler` (Apple GPUs)
- Live multi-GPU topology from `nvidia-smi topo` (NVLink/PIX/PHB/SYS links, utilization, memory)
- Configurable toolchain paths, `-arch`, and extra nvcc flags

### Static analysis
- Inspections: GPU memory leaks (`cudaMalloc` without `cudaFree`), unchecked CUDA API calls with a `CUDA_CHECK` quick fix, and kernel performance heuristics
- Kernel heuristics: strided access, warp divergence, `__syncthreads()` in divergent branches, missing bounds checks, missing `__restrict__`, device-side `malloc`, and more
- Theoretical occupancy calculator for Volta through Hopper
- Cross-platform kernel migration starting points (CUDA ⇄ Metal / OpenCL / HIP)

## Live Templates

| Abbreviation | Expands to |
|--------------|------------|
| `cukernel` | CUDA kernel with bounds check |
| `cugridstride` | Grid-stride loop |
| `cucheck` | `CUDA_CHECK` error-handling macro |
| `culaunch` | Kernel launch with computed grid |
| `cushared` | Shared-memory tile load with barrier |
| `cutime` | CUDA event timing block |
| `mtlkernel` | Metal compute kernel with bounds check |
| `clkernel` | OpenCL kernel with bounds check |

## Configuration

**Settings → Tools → GPU Dev Accelerator**

| Setting | Default | Description |
|---------|---------|-------------|
| nvcc path | *(empty — resolved from PATH)* | Path to the `nvcc` executable |
| GPU architecture (-arch) | *(empty — nvcc default)* | Passed as `-arch=<value>`, e.g. `sm_86` |
| Extra nvcc flags | *(empty)* | Appended to every nvcc invocation, e.g. `-O3 --use_fast_math` |
| compute-sanitizer path | *(empty — resolved from PATH)* | Path to the `compute-sanitizer` executable |
| Nsight Compute (ncu) path | *(empty — resolved from PATH)* | Path to the `ncu` executable |
| Metal SDK (xcrun -sdk) | `macosx` | SDK for `xcrun metal` compilation: `macosx` or `iphoneos` |
| Tool timeout (seconds) | `300` | Maximum run time for external GPU tools (10–3600) |

## Tool Windows

### GPU Dev
- **Location:** Bottom panel
- **Content:** Console where output from the GPU tools appears (compile, Show PTX, GPU information, memory check, profiling, static kernel analysis)

## Inspections

| Inspection | Level | Description |
|------------|-------|-------------|
| CUDA memory leak detection | Warning | Flags `cudaMalloc` allocations without a matching `cudaFree` |
| CUDA kernel performance heuristics | Weak Warning | Highlights kernels with performance issues found by the heuristics above |
| Unchecked CUDA API call | Weak Warning | Flags CUDA API calls whose error code is ignored; offers a `CUDA_CHECK` quick fix |

All inspections apply to CUDA files, belong to the **CUDA** group, and are enabled by default.

## Actions

All actions live in the **GPU Dev** menu on the main menu bar.

| Action | Shortcut | Description |
|--------|----------|-------------|
| Compile CUDA File | `Ctrl+Alt+C` | Compile the current CUDA file with nvcc |
| Show PTX | — | Compile the current CUDA file to PTX and open it |
| GPU Information | — | Show detected GPU devices and toolchain versions |
| Analyze Kernel (Static Heuristics) | `Ctrl+Alt+O` | Run deterministic performance heuristics on the current file |
| Occupancy Calculator | — | Theoretical SM occupancy calculator |
| Migrate Kernel to Another Platform | — | Generate a CUDA/Metal/OpenCL/HIP port of the current kernel |
| Memory Check (compute-sanitizer) | `Ctrl+Alt+M` | Run compute-sanitizer against a CUDA executable |
| Profile Executable (Nsight Compute) | `Ctrl+Shift+P` | Profile a CUDA executable with `ncu` or nvprof |
| Multi-GPU Topology | `Ctrl+Alt+G` | Visualize the GPU topology reported by `nvidia-smi` |

## Supported Languages & File Types

| Language | Extensions |
|----------|------------|
| CUDA C/C++ | `.cu`, `.cuh` |
| Metal Shading Language | `.metal` |
| OpenCL C | `.cl` |

## FAQ

**Does the plugin support Vulkan compute or HLSL?**
No. It provides language support for CUDA, Metal, and OpenCL only.

**Do I need an NVIDIA GPU?**
Editing, completion, inspections, static analysis, and the occupancy calculator work anywhere. Compiling, profiling, and memory checking need the CUDA Toolkit, and running them needs a CUDA-capable GPU.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
