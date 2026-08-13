# Contributing

Lumenprint is built so that its most valuable contributions — new templates — are data-only additions. The project participates in **Drips Wave**, where merged PRs on tagged issues earn points toward rewards.

## Where contributions land

- **New templates** — the primary extension point. Add a template's files plus a manifest entry; it must compile and pass its generated tests. Examples worth adding: multisig, oracle-consumer, cross-contract-call patterns.
- **Template updates** — tracking new soroban-sdk versions and build-target changes as the toolchain moves.
- **CLI features** — new flags, template options, better output.
- **The generate-and-verify CI** — improvements that catch template rot earlier.
- **Docs** — clearer setup guides, per-template explanations.

## How to contribute

1. Pick an open issue — each carries context, requirements, a suggested approach, and a definition of done.
2. Get assigned before starting.
3. Fork, branch, build. `cargo build`, `cargo test`, clippy, and rustfmt must pass — and any template you add or change must generate, build, and test cleanly.
4. Open a PR with `Closes #<issue>`, and evidence that generated templates still compile.

## Standards

- Adding a template must be a data-only contribution (files + manifest entry), never a change to core generation logic.
- A template that doesn't compile is worse than no template — the generate-and-build check is non-negotiable.
- Idiomatic Rust, clippy-clean, rustfmt-formatted.
- Be honest in PRs about limitations and untested edges.
