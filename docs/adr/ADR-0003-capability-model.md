# ADR-0003 -- Capability Model

## Status

Accepted

## Context

Workflows must remain independent from machine implementations.

The platform therefore requires a stable semantic contract between
Workflow Tasks and Modules.

## Decision

### Capability

A Capability is a semantic contract exposed by a Module.

A Capability describes **what** a Module provides, never **how** the
responsibility is implemented.

Examples include:

-   Heat
-   Extract
-   Grind
-   Steam
-   Clean

### Module relationship

Every Capability is owned by exactly one Module.

A Module MAY expose one or more Capabilities.

Capabilities expose responsibilities implemented by the owning Module as
defined by ADR-0001.

Capabilities SHALL NOT expose implementation details.

### Implementation independence

Capabilities SHALL NOT represent:

-   hardware devices
-   drivers
-   sensors
-   actuators
-   GPIO
-   relays
-   control algorithms
-   other implementation details

Examples of invalid Capabilities include:

-   ReadTemperature
-   EnablePump
-   GPIO17
-   BoilerRelay

### Workflow interaction

Workflow Tasks reference Capabilities.

The Core resolves the Capability referenced by each Workflow Task
through the Capability Registry.

The Workflow remains unaware of the owning Module implementation.

### Parameter Contract

Every Capability defines exactly one Parameter Contract.

The Parameter Contract describes the parameters required to execute the
Capability.

Workflow Tasks provide parameter values that satisfy the corresponding
Parameter Contract.

Capability names SHALL NOT encode parameters.

## Consequences

### Positive

-   Stable semantic platform API.
-   Hardware-independent Workflows.
-   Clear separation between architecture and implementation.
-   Modules may evolve internally without affecting Workflows.

### Trade-offs

-   Capability design requires careful modelling.
-   Poorly named Capabilities may leak implementation concepts into the
    platform.

## Out of Scope

Execution semantics, scheduling, concurrency and resource ownership
belong to the owning Module and are defined by ADR-0001.

## Ownership

### Defines

This ADR is the normative source for:

-   Capability

### References

-   ADR-0001 -- Core and Module Architecture
-   ADR-0005 -- Workflow Execution Model
