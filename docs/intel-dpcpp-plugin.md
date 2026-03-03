# Intel DPC++ Plugin

> Full SYCL 2020 and Intel DPC++ language support for CLion.

## Overview

Intel DPC++ Plugin brings comprehensive SYCL 2020 and Data Parallel C++ (DPC++) language support to CLion, including syntax highlighting, code completion, 7 live templates, parallel kernel navigation, and integration with Intel oneAPI tools.

## Installation

1. Open **CLion** (required — this plugin is CLion-specific)
2. Go to **Settings → Plugins → Marketplace**
3. Search for **"Intel DPC++"**
4. Click **Install** and restart CLion

**Requirements:** CLion 2024.3+, Intel oneAPI Base Toolkit (recommended)

## Features

### Free Tier
- SYCL 2020 syntax highlighting
- DPC++ keyword recognition (`sycl::queue`, `sycl::buffer`, `sycl::handler`, etc.)
- 7 live templates for common SYCL patterns
- Basic code completion for SYCL API
- Parallel region folding

### Pro Tier
- Advanced SYCL completion with parameter documentation
- Kernel argument type checking
- Memory model validation (USM, buffers, accessors)
- Device selector optimization hints
- Parallel pattern suggestions (map, reduce, scan)
- oneAPI profiler integration
- FPGA synthesis hints
- Cross-device portability analysis

## Live Templates

Type the abbreviation and press `Tab` to expand:

| Abbreviation | Expansion |
|-------------|-----------|
| `syclq` | SYCL queue with device selector |
| `syclbuf` | SYCL buffer with host data |
| `syclsub` | Submit command group to queue |
| `syclpar` | Parallel for with range |
| `syclred` | Reduction operation |
| `syclusm` | USM allocation and kernel |
| `syclacc` | Buffer accessor pattern |

## Configuration

### Settings Location
**Settings → Tools → Intel DPC++**

| Setting | Default | Description |
|---------|---------|-------------|
| oneAPI path | Auto-detect | Path to Intel oneAPI installation |
| Default device | Auto | Target device (CPU, GPU, FPGA) |
| SYCL standard | 2020 | SYCL specification version |
| Show USM hints | `true` | Display USM vs. Buffer recommendations |

## Supported File Types

| Extension | Description |
|-----------|-------------|
| `.cpp`, `.cxx` | C++ source with SYCL |
| `.hpp`, `.hxx` | C++ headers with SYCL |
| `.dp.cpp` | DPC++ source files |

## Dependencies

- **CLion** — Required (uses `cidr.lang` dependency)
- **Intel oneAPI Base Toolkit** — Recommended for full functionality
- **SYCL-compatible compiler** — icpx, DPC++ compiler

---

**Support:** [Issue Tracker](https://github.com/JirakJ/jetbrains-plugins-docs/issues) · [Discussions](https://github.com/JirakJ/jetbrains-plugins-docs/discussions)
