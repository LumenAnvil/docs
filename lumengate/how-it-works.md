# How it works

Lumengate distributes a token among recipients in proportion to their shares. The model is deliberately simple and predictable.

## Shares

At initialization, each recipient is assigned an integer **share** (a weight). The contract stores the total of all shares. A recipient's entitlement is their share divided by the total — so if Alice has 3 shares and Bob has 1, of every 4 units received, Alice is owed 3 and Bob 1.

## Release accounting

The contract tracks how much it has received in total and how much each recipient has already been paid. When a recipient releases:

1. Compute their total entitlement from the contract's total received and their share.
2. Subtract what they've already been released.
3. Transfer the difference to them, and record it.

This makes release **safe to call repeatedly** and **safe to call by anyone** — funds only ever move to the rightful recipient, and no one can be paid twice for the same receipts. It also handles partial releases correctly: a recipient can claim, more funds can arrive, and they can claim again for just the new portion.

## Dust and rounding

Because shares are integer weights and amounts are integers, distributions don't always divide evenly. Lumengate handles the remainder ("dust") deterministically, according to a rule documented in the repository README, so that no funds are lost or double-counted. The invariant that matters: the sum of all releases never exceeds what the contract has received.

## What's fixed in the MVP

Recipients and their shares are set at initialization and fixed thereafter. Mutable recipient sets, weighted governance over shares, and multi-token support are intentionally left as future contributor issues rather than half-built — see [Contributing](contributing.md).
