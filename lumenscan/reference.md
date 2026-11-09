# Output & reference

> Names and shapes reflect the intended design; confirm against your build's `--help` and README.

## Commands

### `lumenscan <contract_id> [--rpc-url <url>]`
Fetch a deployed contract's WASM and print its interface: functions (names, argument types, return types) and user-defined types (structs, unions, enums).

### `lumenscan --wasm <path>`
Same, from a local `.wasm` file — no network.

### `lumenscan meta <contract_id | --wasm path>`
Print the contract's metadata, including the SDK version it was built with and any custom meta it embedded.

### `--format <human | json | markdown>`
Available on every command. Chooses the output format:
- `human` (default) — a readable table.
- `json` — a stable, documented shape for other tooling.
- `markdown` — a document you can paste into a README, pull request, or generated API docs: a heading per section, functions as code, and tables for fields, variants and metadata.

### `--json`
A shorthand for `--format json`. The two flags cannot be combined.

## The JSON output shape

The `--json` output describes each function with its name, ordered inputs (name and type), and return type, plus any user-defined types the interface references. This shape is intended to be stable and consumable by other tooling — a code generator, a validator, or a UI could build on it. The exact schema is documented in the repository so downstream tools can rely on it.

## Default network

The default RPC endpoint is Stellar testnet; override with `--rpc-url` (or the configured environment variable) to inspect contracts on other networks.

## Offline use

Because `--wasm` reads a local file and needs no network, Lumenscan fits naturally into CI — for example, asserting that a freshly built contract exposes the interface you expect before deploying it.

## In the browser

Lumenscan also ships as a static web app (TypeScript + React) under [`web/`](https://github.com/LumenAnvil/lumenscan/tree/main/web) in the repository: paste a contract ID or drop in a `.wasm` file and see the same decoded interface, with no install. It names types identically to the CLI.
