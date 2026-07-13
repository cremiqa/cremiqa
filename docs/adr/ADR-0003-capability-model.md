# ADR-0003 – Capability Model

**Status:** Accepted

**Date:** 2026-07-13

## Context

The platform requires a stable abstraction independent from concrete implementations.

## Decision

### A Capability is a semantic contract.

A Capability describes what the platform can do, never how it is implemented.

Capabilities form the common vocabulary of the platform.

### Modules publish Capabilities.

A Module may publish one or more Capabilities.

Different Modules may publish the same Capability.

### Workflows consume Capabilities.

Workflows never depend on concrete Modules.

### Capabilities are immutable.

Capabilities do not contain implementation, configuration or runtime state.

## Alternatives Considered

- Capability as an object — rejected.
- Capability as an interface — rejected.
- Capability as a semantic contract — selected.

## Consequences

- Machine-independent Workflows.
- Portable Recipes.
- Stable platform vocabulary.

## Validation

**Implementation Status:** Planned

This decision will be validated once multiple independent Module implementations execute identical Workflows using shared Capabilities.

## Related ADRs

- ADR-0000 – Engineering Philosophy
- ADR-0001 – Core and Module Architecture

## Key Statement

> Capabilities describe what the platform can do—not how it does it.

Modules publish Capabilities.

The Core discovers them.

Workflows consume them.
