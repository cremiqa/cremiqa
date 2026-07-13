# ADR-0001 -- Core and Module Architecture

## Status

Accepted

## Context

The platform requires a stable architectural boundary between
orchestration and machine-specific behaviour.

Early architectural discussions considered modelling hardware devices
(such as pumps, heaters and sensors) as Modules. Validation against
multiple machine types showed that hardware is not the natural
architectural boundary.

The architecture models responsibilities instead of hardware.

## Decision

### Core

The Core is responsible for:

-   discovering Modules
-   validating Modules
-   managing the Module lifecycle
-   maintaining the Capability Registry
-   resolving Workflow Tasks to Capabilities
-   orchestrating Workflow execution

The Core SHALL NOT:

-   control hardware
-   implement control loops
-   manage hardware timing
-   contain machine-specific logic

### Module

A Module is the smallest autonomous architectural unit that fulfills a
single complete responsibility.

A Module is not a hardware abstraction.

A Module encapsulates all implementation details required to fulfill its
responsibility.

### Responsibility Boundaries

Responsibility defines the Module boundary.

Whenever a responsibility contains a control loop, that control loop
SHALL remain entirely inside a single Module.

### Module Ownership

A Module exclusively owns:

**Implementation ownership**

-   internal state
-   resources
-   implementation

**Execution semantics**

-   scheduling
-   timing
-   concurrency
-   consistency of the responsibility it fulfills

These responsibilities SHALL NOT be delegated to the Core.

### Capability

Modules expose one or more Capabilities.

A Capability is a semantic contract describing **what** a Module
provides.

Capabilities intentionally hide implementation details.

### Internal Implementation

A Module may internally compose any implementation components required
to fulfill its responsibility.

Examples include hardware drivers, sensors, actuators, timers, state
machines, control algorithms and helper components.

These are private implementation details and are outside the
architectural contract.

## Consequences

### Positive

-   The architecture remains hardware independent.
-   Workflows remain machine independent.
-   Capabilities remain semantic.
-   Deterministic control stays local to the responsible Module.
-   Module implementations may evolve without affecting the Core.

### Trade-offs

-   More implementation responsibility moves into Modules.
-   Concurrency and scheduling become Module responsibilities.
-   Correct responsibility boundaries become architecturally important.

## Notes

This ADR defines the architectural contract only.

Runtime implementation details (for example scheduling strategy or
execution model) are intentionally outside the scope of this decision.

## Ownership

### Defines

This ADR is the normative source for:

-   Module
-   Core responsibilities

### References

-   ADR-0003 -- Capability Model
-   ADR-0004 -- Module Lifecycle
-   ADR-0005 -- Workflow Execution Model
