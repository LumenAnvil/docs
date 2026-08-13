# Contributing

Lumengate is a fund-moving contract, so contributions center on correctness, tests, and carefully-scoped extensions. The project participates in **Drips Wave**, where merged PRs on tagged issues earn points toward rewards.

## Where contributions land

- **Tests** — the most important category. A contract that moves funds needs exhaustive coverage: payout correctness, no double-payment, uneven-share and dust math, storage-lifetime edge cases, unauthorized-access attempts, and full-lifecycle scenarios. Strengthening the suite is always valuable.
- **Feature extensions (carefully scoped)** — mutable recipient sets, weighted governance over shares, multi-token support, pull-vs-push payout modes. Each is a significant, well-defined piece of work.
- **Documentation** — clearer explanations of the distribution math, deployment guides, and security notes.

## How to contribute

1. Pick an open issue — each carries context, requirements, a suggested approach, and a definition of done.
2. Get assigned before starting.
3. Fork, branch, build. The contract must build with `stellar contract build`, and the full `cargo test` suite must pass.
4. Open a PR with `Closes #<issue>`, test output, and — for anything touching fund movement — tests proving the invariants still hold.

## Standards

- Correctness over features. This contract moves money; a plausible-looking change without tests proving the payout invariants is not acceptable.
- Manage storage lifetime correctly for any new persistent state.
- Never introduce a path where a caller can redirect another recipient's funds.
- Be explicit in PRs about security assumptions and anything left untested.
