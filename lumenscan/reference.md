# Output & reference

> Names and shapes reflect the intended design; confirm against your build's `--help` and README.

## Commands

### `lumenscan <contract_id> [--rpc-url <url>]`
Fetch a deployed contract's WASM and print its interface: functions (names, argument types, return types) and user-defined types (structs, unions, enums).

### `lumenscan --wasm <path>`
Same, from a local `.wasm` file — no network.

### `lumenscan meta <contract_id | --wasm path>`
Print the contract's metadata, including the SDK version it was built with and any custom meta it embedded.

### `--json`
Available on every command. Emits the interface as JSON instead of a human-readable table.

## The JSON output shape

The `--json` output describes each function with its name, ordered inputs (name and type), and return type, plus any user-defined types the interface references. This shape is intended to be stable and consumable by other tooling — a code generator, a validator, or a UI could build on it. The exact schema is documented in the repository so downstream tools can rely on it.

## Default network

The default RPC endpoint is Stellar testnet; override with `--rpc-url` (or the configured environment variable) to inspect contracts on other networks.

## Offline use

Because `--wasm` reads a local file and needs no network, Lumenscan fits naturally into CI — for example, asserting that a freshly built contract exposes the interface you expect before deploying it.
