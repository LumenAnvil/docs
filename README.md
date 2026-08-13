# LumenAnvil

**Rust tooling for building, deploying, and understanding Soroban smart contracts.**

LumenAnvil is a suite of three complementary open-source Rust tools for the Stellar/Soroban ecosystem, covering the contract development lifecycle: scaffold, deploy, and inspect.

## The three tools

- **[Lumenprint](lumenprint/README.md)** — a scaffolding CLI that generates correct, test-ready Soroban contract projects from templates, so you start from a compiling skeleton instead of assembling boilerplate.
- **[Lumengate](lumengate/README.md)** — a deployable, reusable payment-splitter contract that routes incoming funds among recipients by configurable shares.
- **[Lumenscan](lumenscan/README.md)** — an inspection CLI that fetches a deployed contract's WASM, decodes its interface spec and metadata, and shows what it exposes.

## How they fit together

```
   scaffold             deploy               inspect
 ┌───────────┐        ┌───────────┐        ┌───────────┐
 │ Lumenprint│ ─────▶ │ your        │ ────▶ │ Lumenscan │
 └───────────┘        │ contract    │       └───────────┘
  generate a          │ (e.g.       │        decode its
  working project     │ Lumengate)  │        interface
                      └───────────┘
```

You **scaffold** a new contract with Lumenprint, **build and deploy** it (Lumengate is a ready-made example of a real, useful contract), then **inspect** the deployed result with Lumenscan. Each tool is useful entirely on its own; together they cover the path from empty folder to understood, deployed contract.

## What they share

- **A language and foundation** — all three are Rust, built against the Soroban SDK and Stellar's XDR and RPC libraries, reusing the same patterns for contract specs, WASM handling, and ScVal types. A contributor who learns one moves easily to the others.
- **A design philosophy** — clean interfaces and data-driven extension points (a template registry, an output-format layer, per-type handling) so contributions stay small and self-contained.
- **Honest scope** — each ships a solid, tested core with extensions deliberately left as contributor issues rather than half-built.

## A note on the two kinds of tool here

Lumenprint and Lumenscan are ordinary native Rust CLIs — they run on your machine and help you work with contracts. Lumengate is a real Soroban **contract** — it compiles to WASM and runs on-chain. So two of the three are tooling *about* contracts, and one *is* a contract. They line up along a workflow rather than stacking as layers of a single app.

## Where to start

- Building a new contract? Start with [Lumenprint](lumenprint/README.md).
- Need a ready-made fund-routing contract? See [Lumengate](lumengate/README.md).
- Want to understand a deployed contract? Use [Lumenscan](lumenscan/README.md).

## Project links

- Organization: [github.com/LumenAnvil](https://github.com/LumenAnvil)
- Lumenprint · Lumenscan · Lumengate repositories, all under the same org.

All LumenAnvil tools are licensed under Apache-2.0.
