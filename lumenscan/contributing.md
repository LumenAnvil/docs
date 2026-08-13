# Contributing

Lumenscan is a read-only inspection tool built around clean seams — WASM fetching, spec decoding, and output rendering are separable — so contributions stay well scoped. The project participates in **Drips Wave**, where merged PRs on tagged issues earn points toward rewards.

## Where contributions land

- **Spec decoding** — broader and deeper coverage of interface-spec and user-defined-type shapes.
- **Output formats** — new renderers beyond the table and JSON output (the rendering layer is a clean extension point).
- **Features** — diffing two contracts' interfaces, and generating client bindings from the decoded interface, are high-value additions.
- **Metadata** — richer reporting of contract meta.
- **Docs** — the documented JSON/ABI shape and usage guides.

## How to contribute

1. Pick an open issue — each carries context, requirements, a suggested approach, and a definition of done.
2. Get assigned before starting.
3. Fork, branch, build. `cargo build`, `cargo test`, clippy, and rustfmt must pass. Tests run against a checked-in `.wasm` fixture, so no live network is needed.
4. Open a PR with `Closes #<issue>` and test output.

## Standards

- Keep WASM fetching behind its interface so the decoder is tested against the fixture, not the network.
- Put new output formats behind the rendering interface rather than branching through the core.
- Keep Lumenscan read-only: it inspects, it never deploys or modifies.
- Be honest in PRs about limitations and untested edges.
