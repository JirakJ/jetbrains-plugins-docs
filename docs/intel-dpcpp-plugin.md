# Intel DPC++ Support

> SYCL 2020 / DPC++ editor helpers and Intel oneAPI tool shortcuts for CLion.

**Free & open source** — source: https://github.com/JirakJ/intel-dpcpp-plugin (Apache-2.0); contributions welcome.

## Overview

Intel DPC++ Support adds editor helpers for writing SYCL 2020 and Data Parallel C++ (DPC++) code in CLion: a dedicated file type, completion for common SYCL APIs, highlighting of `sycl::` identifiers and kernel launches, quick documentation, and live templates. A **Tools → DPC++** menu detects your oneAPI installation, builds ready-to-run command lines for VTune, Advisor, and `gdb-oneapi`, and estimates kernel occupancy for Intel Xe GPUs.

## Installation

1. Open **CLion → Settings → Plugins → Marketplace** (this plugin is CLion-specific)
2. Search for **"Intel DPC++ Support"**
3. Click **Install** and restart CLion

**Requirements:** CLion 2023.2+. The Intel oneAPI Base Toolkit is needed for compiling, profiling, and debugging.

## Features

### Editor
- File type for `.dpcpp` and `.dp.cpp` sources (handled as C++)
- Completion entries for common SYCL APIs: queues, selectors, buffers, accessors, USM allocation, ranges, device info
- Highlighting of `sycl::` identifiers and kernel launches (`parallel_for`, `single_task`)
- Quick documentation for `sycl::queue` and `parallel_for`
- Live templates for common SYCL patterns (see below)

### Tools → DPC++
- **Configure oneAPI Toolchain** — detects oneAPI installations (via `$ONEAPI_ROOT` and the default locations) that contain `icpx`
- **Profile with VTune**, **Intel Advisor Analysis**, **Debug with gdb-oneapi** — locate the tool and give you the ready-to-run command line (copied to the clipboard)
- **Kernel Occupancy Calculator** — first-order occupancy estimate for Intel Xe GPUs from work-group size, registers, and local memory
- Links to the DPC++ documentation and the oneAPI code samples

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

## Actions

All actions live under **Tools → DPC++**.

| Action | Description |
|--------|-------------|
| New DPC++ Project | Shows how to set up a CMake project for the DPC++ compiler |
| Configure oneAPI Toolchain | Detect and configure the Intel oneAPI DPC++ compiler |
| Open oneAPI Code Samples | Browse Intel oneAPI code samples |
| DPC++ Documentation | Open Intel DPC++ documentation |
| Debug with gdb-oneapi | Build the `gdb-oneapi` command line for GPU kernel debugging |
| Profile with VTune | Build the VTune Profiler GPU analysis command line |
| Kernel Occupancy Calculator | Estimate GPU occupancy and identify limiting factors |
| Intel Advisor Analysis | Build the Intel Advisor roofline / offload-modeling command line |

## Supported File Types

| Extension | Description |
|-----------|-------------|
| `.dpcpp` | DPC++ source file |
| `.dp.cpp` | DPC++ source file |

SYCL completion, highlighting, and quick documentation also apply to standard C++ files.

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
