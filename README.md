# TLPI Code Examples (CMake Build Support)

This repository contains the source code examples from the book **"The Linux Programming Interface"** (TLPI) by Michael Kerrisk.

## Origin & Modification

- **Original Source**: Copied from the official book distribution ([man7.org/tlpi](https://man7.org/tlpi/)).
- **Modification**: Added a complete **CMake build system** to facilitate easier usage and learning.

## Build Instructions

### Requirements
- CMake 3.10 or later
- GCC or Clang compiler

### Quick Start

```bash
mkdir build
cd build
cmake ..
cmake --build .
```

## Platform Support

- **Linux**: Full support for all examples.
- **FreeBSD/BSD**: The CMake configuration automatically detects the platform and builds only the compatible examples (excluding Linux-specific features like `cgroups`, `namespaces`, or specific syscalls).

## License

Please refer to the source code headers and the original distribution for license information.

