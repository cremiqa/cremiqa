# Cremiqa

**A modular platform for coffee automation.**

Cremiqa is an open, machine-independent platform for automating coffee
preparation.

Rather than focusing on a specific coffee machine, Cremiqa models the
coffee-making process itself. Whether coffee is prepared using a moka
pot, a semi-automatic espresso machine or a fully automatic machine, the
same architectural concepts apply.

The architectural vocabulary used throughout the project is defined by
the accepted ADRs and summarized in the Glossary.

## Vision

Coffee machines differ.

Coffee preparation does not.

Cremiqa separates **behavior** from **implementation**.

-   Recipes provide data.
-   Workflows describe behavior.
-   Tasks define execution requirements.
-   Capabilities define semantic contracts.
-   Modules fulfill responsibilities.
-   The Core orchestrates execution.

## Architecture Overview

``` text
Recipe
   │
provides values for
   ▼
Workflow
   │
contains
   ▼
Task
   │
references
   ▼
Capability
   │
implemented by
   ▼
Module
   ▲
managed by
   │
Core
```

Each Capability defines a Parameter Contract that must be satisfied by
the corresponding Task during Workflow execution.

These concepts are intentionally independent from any specific hardware
platform or programming language.

## Project Status

Cremiqa is currently in **Phase Zero**.

The architecture, terminology and engineering principles are being
established before implementation begins.

## Documentation

Recommended reading order:

1.  `docs/adr/ADR-0000-engineering-philosophy.md`
2.  `docs/adr/ADR-0001-core-and-module-architecture.md`
3.  `docs/adr/ADR-0002-repository-evolution-strategy.md`
4.  `docs/adr/ADR-0003-capability-model.md`
5.  `docs/adr/ADR-0004-module-lifecycle.md`
6.  `docs/adr/ADR-0005-workflow-model.md`
7.  `docs/glossary.md`

## Guiding Principles

-   Platform before implementation.
-   Behavior before technology.
-   Semantic contracts over concrete implementations.
-   Composition over specialization.
-   Readability over cleverness.

## Contributing

Please read `CONTRIBUTING.md` before opening an issue or submitting a
pull request.

## License

Source code is licensed under the Apache License 2.0.

See the `LICENSE` file for details.
