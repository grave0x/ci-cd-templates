# Rust CI Template

File: [`.github/workflows/ci-rust.yml`](../.github/workflows/ci-rust.yml)

## What it checks

| Step | Command | Fails on |
|------|---------|----------|
| Format | `cargo fmt --check` | Unformatted code |
| Lint | `cargo clippy --all-targets --all-features -- -D warnings` | Any clippy warning |
| Test | `cargo test --all-features` | Test failures |
| Build | `cargo build --release --all-features` | Compilation errors |

## Customization

- **MSRV**: Add your minimum supported Rust version to the matrix:
  ```yaml
  toolchain: [stable, "1.82.0"]
  ```
- **Features**: Change `--all-features` to `--features foo,bar` if you don't want all features tested.
- **No default features**: Change to `--no-default-features` if your crate needs that tested.

## Prerequisites

- A `Cargo.toml` at the repo root
- For the release template: a `CARGO_REGISTRY_TOKEN` secret
