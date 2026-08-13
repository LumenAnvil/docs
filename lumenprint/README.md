# Lumenprint

**A scaffolding CLI for Soroban smart contracts.**

Lumenprint generates a correct, documented, test-ready Soroban contract project from a template, so you start from a working skeleton instead of assembling boilerplate by hand.

## Why Lumenprint exists

Starting a Soroban contract means getting a pile of details right: the correct soroban-sdk version, the right build target, a proper Cargo.toml, a test skeleton using the SDK's test utilities, and CI that builds with the Stellar CLI. Newcomers get these wrong constantly, and even experienced developers copy-paste from an old project. Lumenprint generates a known-good starting point from a chosen template, with everything wired correctly.

> Lumenprint is an ordinary native Rust CLI — it *generates* contract projects; it is not itself a contract.

## Where it fits in LumenAnvil

Lumenprint is the **scaffold** stage. After generating a project, you build your contract (see [Lumengate](../lumengate/README.md) for a real example) and later inspect the deployed result with [Lumenscan](../lumenscan/README.md).

## Next

- [Quickstart](quickstart.md) — generate and build your first project
- [Templates](templates.md) — what's available and how to add one
- [Contributing](contributing.md)
