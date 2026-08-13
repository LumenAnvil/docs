# Lumengate

**A deployable payment-splitter contract for Soroban.**

Lumengate is a reusable Soroban smart contract that routes incoming funds among a set of recipients according to configured shares. Send a token to the contract, and each recipient can claim their portion.

## Why Lumengate exists

Splitting incoming funds among multiple parties by fixed shares — revenue sharing, team payouts, royalty splits, DAO distributions — is a common need with no simple, reusable, deployable contract for it on Soroban. Lumengate is that contract: configure recipients and shares once, then it routes funds accordingly.

> Lumengate is a real Soroban **contract**: it compiles to WASM and runs on-chain. This is the one project in LumenAnvil that is a contract rather than a CLI tool.

## What it does

- Initialize once with a token to distribute and a fixed list of recipients, each with an integer share.
- Anyone can send the configured token to the contract.
- Each recipient (or anyone acting on their behalf) can `release` their owed portion; `release_all` pays everyone.
- View functions expose each recipient's shares and released amounts, and totals.

## Where it fits in LumenAnvil

Lumengate is the **deploy** stage and a concrete example of a real contract: you might scaffold a project like it with [Lumenprint](../lumenprint/README.md), and inspect its deployed interface with [Lumenscan](../lumenscan/README.md).

## Important

Lumengate is **unaudited**. It moves funds, so read the [Security](security.md) page before using it with real value.

## Next

- [Quickstart](quickstart.md) — build, deploy, and use it on testnet
- [How it works](how-it-works.md) — the distribution model and math
- [Security](security.md) — assumptions and cautions
- [Contributing](contributing.md)
