# ADR-0004 – Module Lifecycle

**Status:** Accepted

**Date:** 2026-07-13

## Context

Modules are the implementation units of the Cremiqa platform.

The Core is responsible for discovering Modules, validating the system, exposing Capabilities and orchestrating execution.

The platform therefore requires a well-defined lifecycle describing when a Module becomes part of the running system.

## Decision

### Core boot process

```text
Scan
    ↓
Discovered
    ↓
Identified
```

### Module lifecycle

```text
Identified
    ↓
Configured
    ↓
Validated
    ↓
Initialized
    ↓
Ready
    ↓
Disposed
```

The lifecycle represents availability, not operational state.

### Configured

The Module receives its configuration.

### Validated

The Module validates its own configuration and internal consistency.

The Core validates the complete system.

If validation fails, platform startup fails.

### Initialized

The Module allocates resources and completes initialization.

Initialization must not perform operational work.

### Ready

The Module is fully available.

The Core never interacts with Modules that are not in the Ready state.

Modules declare Capabilities.

The Core discovers and registers declared Capabilities only after a Module reaches the Ready state.

### Disposed

The Module releases its resources.

## Separation of Responsibilities

### Module

- Own implementation
- Own lifecycle
- Validate itself
- Manage internal resources
- Declare Capabilities

### Core

- Discover Modules
- Identify Modules
- Resolve dependencies
- Validate the system
- Register Capabilities
- Execute Workflows

## Alternatives Considered

### Running lifecycle state

Rejected because operational activity belongs to runtime execution.

### Capability registration before Ready

Rejected because partially initialized Modules must never expose Capabilities.

## Consequences

- Only Ready Modules participate in the platform.
- Startup failures occur before runtime execution.
- Lifecycle remains independent from runtime state.

## Validation

**Implementation Status:** Planned

## Related ADRs

- ADR-0000 – Engineering Philosophy
- ADR-0001 – Core and Module Architecture
- ADR-0003 – Capability Model

## Key Statement

> A Module becomes part of the platform only after reaching the Ready state.

Modules declare Capabilities.

The Core discovers and registers them.

Lifecycle represents availability.

Runtime represents operation.
