# In the browser

Lumenscan also runs as a **static web app**, with nothing to install:

**<https://lumenanvil.github.io/lumenscan-web/>**

Paste a deployed contract ID, or drop in a local `.wasm` build, and see the same
decoded interface the CLI prints — functions, their arguments and types, the
user-defined types, and events.

## Same decoding, same names

The web inspector is not a re-implementation of the decoder. It uses
[`@stellar/stellar-sdk`](https://www.npmjs.com/package/@stellar/stellar-sdk) to
read a contract's spec — `contract.Client.from` fetches and decodes a deployed
contract over RPC, and `contract.Spec.fromWasm` reads the `contractspecv0`
custom section out of raw `.wasm` bytes. It then names types exactly the way the
Rust CLI does — `Vec<String>`, `Option<u32>`, `Result<(), Error>` — so a type
reads identically whether you used the terminal or the browser.

It is strictly **read-only**: it fetches and decodes, and never deploys,
invokes, signs, or changes anything.

## When to use which

| | CLI | Web |
| --- | --- | --- |
| Scripting, CI, JSON output | ✅ | — |
| Nothing to install, shareable link | — | ✅ |
| Offline, no network | ✅ (fixtures) | drop in a `.wasm` |
| Markdown / JSON renderers | ✅ | — |

For everyday "what does this contract expose?" either works; reach for the CLI
when you want to pipe the result into another tool.

## Source

The web app lives in its own repository,
[LumenAnvil/lumenscan-web](https://github.com/LumenAnvil/lumenscan-web)
(TypeScript + React + Vite), and shares the CLI's `oracle.wasm` test fixture so
the two decoders are pinned to the same real contract bytes.

## Next

- [Output & reference](reference.md) — the CLI's commands and JSON shape
- [Quickstart](quickstart.md) — inspect a contract from the terminal
