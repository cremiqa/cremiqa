# ADR-0004 -- Module Lifecycle

## Status

Accepted

## Context

The Core establishes a deterministic and technology-independent
lifecycle for every Module before it becomes available to the platform.

The lifecycle ensures that only Modules satisfying the architectural
contract are exposed through the Capability Registry.

## Decision

Every Module SHALL progress through the following lifecycle states:

1.  Discovered
2.  Identified
3.  Validated
4.  Registered
5.  Ready

A Module SHALL NOT skip lifecycle states.

## Lifecycle

### Discovered

The Core discovers a Module implementation.

No assumptions are made beyond the Module's existence.

### Identified

The Core reads the Module metadata.

Identification establishes the Module identity, version and declared
Capabilities.

### Validated

The Core validates that the Module satisfies the architectural contract
required by the platform.

Validation MAY include:

-   metadata validation
-   Capability declaration validation
-   Parameter Contract validation
-   dependency validation
-   version compatibility checks

Validation SHALL NOT inspect or validate the Module's internal
implementation or business logic.

### Registered

The Core registers the Module's Capabilities in the Capability Registry.

Only successfully validated Modules MAY be registered.

### Ready

The Module is available for Workflow execution.

From this point, the Module is responsible for the execution semantics
of its exposed Capabilities as defined by ADR-0001.

## Consequences

### Positive

-   Predictable platform startup.
-   Stable Capability Registry.
-   Clear separation between discovery and validation.
-   Architectural contracts are verified before Modules become
    available.

### Trade-offs

-   Startup includes an explicit validation phase.
-   Modules cannot participate until lifecycle completion.

## Out of Scope

Runtime initialization, scheduling, execution model and internal state
management are implementation concerns and are intentionally outside the
scope of this ADR.

## Ownership

### Defines

This ADR is the normative source for:

-   Module Lifecycle

### References

-   ADR-0001 -- Core and Module Architecture
-   ADR-0003 -- Capability Model
-   ADR-0005 -- Workflow Execution Model
