# Cremiqa Glossary

This glossary is the normative vocabulary of the Cremiqa architecture.
Definitions in this document are derived from the accepted ADRs.

------------------------------------------------------------------------

## Capability

A semantic contract exposed by a Module.

A Capability defines **what** a Module provides, never **how** it is
implemented.

Every Capability is owned by exactly one Module and defines exactly one
Parameter Contract.

**Defined by:** ADR-0003

------------------------------------------------------------------------

## Core

The orchestration component of the platform.

The Core is responsible for:

-   Module discovery
-   Module validation
-   Module lifecycle management
-   Capability Registry management
-   Workflow execution
-   Capability resolution

The Core never performs machine-specific behaviour.

**Defined by:** ADR-0001

------------------------------------------------------------------------

## Module

The smallest autonomous architectural unit responsible for fulfilling
one complete responsibility.

A Module owns:

-   its internal state
-   its implementation
-   its execution semantics
-   its resources
-   scheduling
-   timing
-   concurrency

A Module encapsulates all implementation details required to fulfill its
responsibility.

**Defined by:** ADR-0001

------------------------------------------------------------------------

## Parameter Contract

The specification of the parameters required to execute a Capability.

A Parameter Contract is defined by a Capability and satisfied by a Task
during Workflow execution.

**Defined by:** ADR-0003 / ADR-0005

------------------------------------------------------------------------

## Recipe

A data object that selects a Workflow and provides parameter values for
its Tasks.

A Recipe contains data only.

It never defines behaviour.

**Defined by:** ADR-0005

------------------------------------------------------------------------

## Responsibility

A cohesive business concern fulfilled by a Module.

Responsibilities define Module boundaries.

**Defined by:** ADR-0001

------------------------------------------------------------------------

## Task

The smallest declarative unit of behaviour within a Workflow.

A Task references a Capability and provides values satisfying its
Parameter Contract.

A Task defines what must happen, never how.

**Defined by:** ADR-0005

------------------------------------------------------------------------

## Workflow

A declarative description of behaviour expressed as an ordered sequence
of Tasks.

A Workflow defines what shall happen and in which order.

It remains independent from machine and Module implementations.

**Defined by:** ADR-0005

------------------------------------------------------------------------

# Non-normative Notes

The following terms intentionally have no architectural definitions
because they are implementation details:

-   Driver
-   Sensor
-   Actuator
-   Pump
-   Boiler
-   Heater
-   GPIO
-   Relay
-   PID controller
-   State machine
-   Scheduler
-   Queue
-   Thread
-   Actor

These concepts may exist inside Module implementations but are not
architectural building blocks of the Cremiqa platform.
