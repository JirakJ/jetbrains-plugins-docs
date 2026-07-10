# Intel DPC++ Support

> SYCL 2020 and Intel oneAPI development for CLion — write, debug, and profile CPU, GPU, and FPGA code from a single codebase.

## Overview

Intel DPC++ Support brings comprehensive SYCL 2020 and Data Parallel C++ (DPC++) development to CLion. Develop for CPUs, GPUs, and FPGAs from one codebase, with context-aware code completion, semantic highlighting, GPU kernel debugging via `gdb-oneapi`, and Intel VTune / Advisor profiling integration.

The plugin is distributed as freemium: core SYCL language and editor features are free, while the advanced debugging, profiling, and optimization tools are part of a paid Professional tier.

## Installation

1. Open **CLion → Settings → Plugins → Marketplace** (this plugin is CLion-specific)
2. Search for **"Intel DPC++ Support"**
3. Click **Install** and restart CLion

**Requirements:** CLion 2023.2+, Intel oneAPI Base Toolkit 2024.0+ (for build, debug, and profiling), CMake 3.20+, Linux / Windows / macOS

## Features

### Language Support
- Full SYCL 2020 syntax highlighting with keyword and type recognition
- Dedicated `.dpcpp` and `.dp.cpp` file types
- Context-aware completion for `sycl::queue`, `sycl::buffer`, accessors, and kernels
- Documentation on hover for SYCL APIs
- Semantic highlighting via the DPC++ annotator, plus a dedicated color settings page

### Toolchain & Build
- Automatic Intel oneAPI toolchain detection
- CMake integration with DPC++ compiler configuration
- Live templates for common SYCL patterns (see below)

### Debugging & Profiling
- `gdb-oneapi` integration for GPU kernel debugging, thread visualization, and stepping
- Intel VTune Profiler integration (GPU hotspots, offload, memory analysis)
- Intel Advisor roofline analysis and offload modeling
- Kernel occupancy calculator and bandwidth estimator

### Advanced Tools
- Device Explorer tool window for browsing CPU, GPU, and FPGA devices
- FPGA optimization analyzer with resource estimation
- Multi-device orchestrator for workload distribution
- Auto-tuning of work-group size
- AI-powered optimization suggestions
- Live kernel editing with hot-reload
- Intel DevCloud integration for cloud compilation and testing

## Live Templates

Type the abbreviation in a C++ file and press `Tab` to expand:

| Abbreviation | Expands to |
|--------------|------------|
| `syclqueue` | Create a SYCL queue |
| `syclbuffer` | Create a SYCL buffer |
| `syclsubmit` | Submit a command group to a queue |
| `syclparallel` | `parallel_for` kernel over a range |
| `syclaccess` | Get a buffer accessor |
| `syclusm` | USM allocation (and free) |
| `syclmain` | DPC++ `main()` with queue and exception handling |

## Inspections

Both inspections are enabled by default and grouped under **DPC++ / SYCL**.

| Inspection | Level | Description |
|-----------|-------|-------------|
| SYCL Code Quality | Warning | Flags common SYCL/DPC++ correctness and code-quality issues |
| SYCL Performance Optimization | Weak Warning | Highlights SYCL patterns with performance-optimization opportunities |

## Tool Windows

### DPC++ Devices
- **Location:** right panel
- **Content:** Device Explorer for browsing available CPU, GPU, and FPGA devices

## Actions

Available from the **Tools → DPC++** menu (one debugger action is also added to the **Run** menu):

| Action | Location | Description |
|--------|----------|-------------|
| New DPC++ Project | Tools → DPC++ | Create a new Intel DPC++ project |
| Configure oneAPI Toolchain | Tools → DPC++ | Detect and configure the Intel oneAPI DPC++ compiler |
| Open oneAPI Code Samples | Tools → DPC++ | Browse Intel oneAPI code samples |
| DPC++ Documentation | Tools → DPC++ | Open Intel DPC++ documentation |
| Debug with gdb-oneapi | Tools → DPC++ | GPU debugging with the Intel oneAPI debugger |
| Profile with VTune | Tools → DPC++ | Performance analysis with Intel VTune Profiler |
| Kernel Occupancy Calculator | Tools → DPC++ | Estimate GPU occupancy and identify limiting factors |
| Intel Advisor Analysis | Tools → DPC++ | Roofline analysis and optimization recommendations |
| FPGA Optimization Analyzer | Tools → DPC++ | FPGA-specific optimization and resource estimation |
| Multi-Device Orchestrator | Tools → DPC++ | Distribute workloads across multiple devices |
| Auto-Tune Parameters | Tools → DPC++ | Automatic work-group size optimization |
| AI Optimization Assistant | Tools → DPC++ | AI-powered optimization suggestions |
| Live Kernel Editor | Tools → DPC++ | Hot-reload kernels without restarting |
| Intel DevCloud | Tools → DPC++ | Cloud compilation and testing |
| Performance Dashboard | Tools → DPC++ | Visualize performance metrics |
| Debug with gdb-oneapi | Run | Launch the Intel oneAPI debugger from the Run menu |

## Supported File Types

| Extension | Description |
|-----------|-------------|
| `.dpcpp` | Dedicated DPC++ source file |
| `.dp.cpp` | DPC++ source file |

SYCL-aware completion, hover documentation, semantic highlighting, and inspections also apply to standard C++ files, not only to the dedicated DPC++ file types.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
