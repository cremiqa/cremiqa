# ADR-0001 – Core and Module Architecture

**Status:** Accepted

**Date:** 2026-07-12

## Context

Cremiqa supports multiple machines through a stable platform architecture.

## Decision

### The Core owns behavior.

The Core owns orchestration and contains no machine-specific knowledge.

### Everything else is a Module.

A Module is a self-contained unit of responsibility that owns its implementation and lifecycle, and publishes one or more Capabilities.

Modules may represent hardware, software, integrations or simulations.

Modules may themselves be composed of other Modules.

### Workflows consume Capabilities.

Recipes are machine-independent and may contain optional tasks. Missing optional Capabilities do not prevent successful execution.

## Validation

**Implementation Status:** Planned

## Related ADRs

- ADR-0000 – Engineering Philosophy
- ADR-0003 – Capability Model
