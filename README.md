# Cremiqa

**A modular platform for coffee automation.**

Cremiqa is an open, machine-independent platform for automating coffee preparation.

Rather than focusing on a specific coffee machine, Cremiqa models the coffee-making process itself. Whether the coffee is prepared using a moka pot, a semi-automatic espresso machine or a fully automatic machine, the platform describes the process using the same architectural concepts.

## Vision

Coffee machines differ.

Coffee preparation does not.

Cremiqa separates **behavior** from **implementation**.

- Recipes describe **what** should be prepared.
- Workflows describe **how** it is prepared.
- Capabilities describe **what the platform can do**.
- Modules provide the implementation.
- The Core orchestrates everything.

## Architecture Overview

```text
Recipe
    │
provides values for
    ▼
Parameter Contracts
    ▲
defined by
    │
Tasks
    ▲
contained in
    │
Workflow
    │
requires
    ▼
Capabilities
    ▲
declared by
    │
Modules
    │
managed by
    ▼
Core
```

These concepts are intentionally independent from any specific hardware platform or programming language.

## Project Status

Cremiqa is currently in **Phase Zero**.

The architecture, terminology and engineering principles are being established before implementation begins.

## Documentation

Recommended reading order:

1. `docs/glossary.md`
2. `docs/adr/ADR-0000-engineering-philosophy.md`
3. Remaining accepted ADRs

## Guiding Principles

- Platform before implementation.
- Behavior before technology.
- Semantic contracts over concrete implementations.
- Composition over specialization.
- Readability over cleverness.

## Contributing

Please read `CONTRIBUTING.md` before opening an issue or submitting a pull request.

## License

Source code is licensed under the Apache License 2.0.

See the `LICENSE` file for details.
