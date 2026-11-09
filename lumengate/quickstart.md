# Quickstart

Build Lumengate, deploy it to testnet, and split some funds. You need the Rust toolchain, the WASM contract build target, and the Stellar CLI.

> Commands below reflect the intended design; confirm exact invocations and function signatures against the repository README, which documents the versions this contract targets.

## Prerequisites

```bash
rustc --version
stellar --version
```

You also need a funded testnet identity configured in the Stellar CLI, and a token (for example, a testnet asset's contract) to distribute.

## 1. Build

Soroban contracts build with the Stellar CLI, not plain cargo:

```bash
git clone https://github.com/LumenAnvil/Lumengate.git
cd Lumengate
stellar contract build
```

Run the test suite (native test target):

```bash
cargo test
```

## 2. Deploy to testnet

```bash
stellar contract deploy \
  --wasm target/wasm32v1-none/release/lumengate.wasm \
  --network testnet \
  --source <your-identity>
```

This returns the deployed contract ID.

## 3. Initialize

Set the token to distribute and the recipients with their shares (exact argument shapes are in the repo README):

```bash
stellar contract invoke --id <contract-id> --network testnet --source <identity> -- \
  initialize --token <token-contract-id> --recipients '[...]'
```

## 4. Fund and release

Send the token to the contract address, then release:

```bash
stellar contract invoke --id <contract-id> --network testnet --source <identity> -- \
  release --recipient <recipient-address>
```

Each recipient receives their share of what the contract has received.

## Checking what is owed

Two read-only views report pending payouts without moving anything — useful for a dashboard or a check before releasing:

```bash
# What every recipient is owed right now, in one call:
stellar contract invoke --id <contract-id> --network testnet --source <identity> -- \
  releasable_all

# The total that release_all would move right now:
stellar contract invoke --id <contract-id> --network testnet --source <identity> -- \
  pending_total
```

## Next steps

- [How it works](how-it-works.md) — the payout math
- [Security](security.md) — before using real value
