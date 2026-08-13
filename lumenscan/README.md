# Lumenscan

**A contract inspection CLI for Soroban.**

Lumenscan fetches a deployed contract's WASM, decodes its interface spec and metadata, and prints a clear description of what the contract exposes — its functions, their arguments and types, and its user-defined types.

## Why Lumenscan exists

A deployed Soroban contract's interface is embedded in its WASM, but reading it means knowing how to fetch the WASM and decode the spec data inside it. Lumenscan does it in one command: point it at a contract ID (or a local `.wasm`), and get its full interface, as a readable table or as JSON other tools can consume.

> Lumenscan is an ordinary native Rust CLI — it reads and describes contracts; it doesn't deploy or modify them.

## Where it fits in LumenAnvil

Lumenscan is the **inspect** stage. After scaffolding with [Lumenprint](../lumenprint/README.md) and deploying a contract (such as [Lumengate](../lumengate/README.md)), Lumenscan tells you exactly what the deployed contract exposes.

## Next

- [Quickstart](quickstart.md) — inspect a contract
- [Output & reference](reference.md) — commands and the JSON shape
- [Contributing](contributing.md)
