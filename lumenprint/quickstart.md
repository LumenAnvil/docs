# Quickstart

Generate a Soroban contract project and build it. You need the Rust toolchain and the Stellar CLI installed.

> Commands and flags below reflect the intended design; confirm against your build's `--help` and README.

## Prerequisites

- Rust (a recent stable toolchain) and the WASM contract build target
- The Stellar CLI (`stellar`), used to build contract projects
- Verify with:

```bash
rustc --version
stellar --version
```

## 1. Install Lumenprint

```bash
git clone https://github.com/LumenAnvil/Lumenprint.git
cd Lumenprint
cargo install --path .
```

## 2. Generate a project

```bash
lumenprint new my-contract --template minimal
```

This creates a `my-contract/` directory with a Cargo.toml (correct SDK version and build target), a minimal working contract in `src/lib.rs`, a test module, a README, a `.gitignore`, and a CI workflow.

## 3. Build and test the generated project

```bash
cd my-contract
stellar contract build
cargo test
```

Both should succeed out of the box — a generated project that compiles and passes its tests is the whole point.

## 4. See available templates

```bash
lumenprint list
```

## Next steps

- [Templates](templates.md) — the template catalog and how to add your own
- [Contributing](contributing.md)
