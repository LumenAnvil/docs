# Security

Lumengate moves funds. Read this before using it with anything of value.

## Unaudited

Lumengate has **not** been audited. It is an open-source, well-tested contract built with care, but "well-tested" is not "audited." Use it on testnet freely; before using it with real value on mainnet, have it reviewed by someone qualified, and understand that you use it at your own risk.

## What the contract guarantees

- **Funds only go to rightful recipients.** Release computes a recipient's entitlement from their configured share and pays only them; a caller cannot redirect another recipient's funds.
- **No double payment.** The contract records what each recipient has been paid and only ever releases the unpaid remainder.
- **Conservation.** The sum of all releases never exceeds what the contract has received; remainder/dust is handled deterministically.

## What to be aware of

- **Recipients and shares are fixed at initialization.** Choose them carefully — the MVP does not support changing them afterward.
- **State lifetime.** Soroban persistent state must have its time-to-live maintained; the contract manages this for its own state, but operators should understand that on-chain state has a lifecycle. The repository documents how Lumengate handles it.
- **The token is trusted.** Lumengate distributes whatever token it's initialized with; it inherits that token contract's behavior.

## Reporting issues

If you find a security problem, report it responsibly through the repository's stated channel rather than opening a public issue with exploit details.
