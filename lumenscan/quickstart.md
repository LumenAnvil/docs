# Quickstart

Inspect a deployed contract's interface. You need the Rust toolchain; no network is needed for local `.wasm` inspection.

> Commands and flags below reflect the intended design; confirm against your build's `--help` and README.

## 1. Install

```bash
git clone https://github.com/LumenAnvil/Lumenscan.git
cd Lumenscan
cargo install --path .
```

## 2. Inspect a deployed contract

```bash
lumenscan <contract-id> --rpc-url https://soroban-testnet.stellar.org
```

Lumenscan fetches the contract's WASM over RPC, decodes its interface, and prints every function with its argument names and types and its return type, plus any user-defined types.

## 3. Inspect a local WASM file (offline)

```bash
lumenscan --wasm ./path/to/contract.wasm
```

Same output, no network — useful in CI or when you already have the built WASM.

## 4. Read contract metadata

```bash
lumenscan meta <contract-id>
# or
lumenscan meta --wasm ./path/to/contract.wasm
```

## 5. Machine-readable output

Add `--json` to any command to get the interface as JSON — a usable ABI dump other tools can consume:

```bash
lumenscan <contract-id> --json
```

## Next steps

- [Output & reference](reference.md) — the full command set and JSON shape
