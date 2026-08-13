# Templates

Lumenprint generates projects from templates. Each template is a complete, compiling Soroban contract project that you use as a starting point.

> Exact template names and contents reflect the intended design; confirm against your build's `lumenprint list` output.

## Available templates

- **minimal** — a small working contract (such as a counter or hello-style contract), the simplest starting point.
- **token** — a fungible-token-style contract skeleton. This is a starting point to build on, **not an audited token implementation** — treat it as scaffolding, not a finished, secure token.
- **access** — a contract with a basic owner/admin authorization pattern, as a starting point for access-controlled contracts.

Each template compiles and its generated tests pass out of the box.

## How templates work

A template is data, not code: a set of files plus a manifest entry describing it. When you run `lumenprint new`, Lumenprint copies the template's files and substitutes the project name and any options. This design is deliberate — it means the tool's core logic doesn't change when templates are added or edited.

## Adding a template

Because templates are data-driven, adding one is a self-contained contribution: add the template's files and a manifest entry, and it appears in `lumenprint list` and `lumenprint new`. No changes to the generation logic are needed.

The key requirement: a new template must **compile and pass its generated tests**. Lumenprint's own CI generates each template and builds it, so a template that doesn't build is caught before it ships. See [Contributing](contributing.md) for the exact expectations.

## Keeping templates current

Templates encode a specific soroban-sdk version and build target. Because the Soroban toolchain moves, templates need occasional updates to track the current SDK — a common and welcome contribution. The generate-and-build CI is what surfaces when a template has fallen behind.
