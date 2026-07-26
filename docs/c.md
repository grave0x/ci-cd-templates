# C CI Template

File: [`.github/workflows/ci-c.yml`](../.github/workflows/ci-c.yml)

## What it checks

| Step | Tool | Fails on |
|------|------|----------|
| Configure | `cmake ..` | Configuration errors |
| Build | `cmake --build` or `make` | Compilation errors |
| Test | `ctest` or `make test` | Test failures |

The template tries CMake first, then falls back to a plain `Makefile`.

## Customization

- **Matrix**: The template builds with both `gcc` and `clang` by default.
- **CMake options**: Edit the `cmake ..` line in the configure step.
- **Make**: If you only use Make, remove the CMake steps and keep the Makefile fallback.

## Prerequisites

- A `CMakeLists.txt` or `Makefile` at the repo root
- Build tools: `cmake`, `build-essential`, `gcc`/`clang`
