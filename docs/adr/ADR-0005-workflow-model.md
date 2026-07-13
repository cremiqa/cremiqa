# ADR-0005 – Workflow Model

**Status:** Accepted

**Date:** 2026-07-13

## Context

The platform requires a machine-independent way to describe behavior. Behavior must remain independent from machine implementations, Module implementations and Recipe values.

## Decision

### A Workflow is composed of Tasks.

A Workflow is a declarative description of behavior expressed as an ordered sequence of Tasks.

### A Task is the smallest declarative unit of behavior.

Each Task defines:

- the required Capability
- a Parameter Contract

A Task describes what must happen. It never specifies how the action is implemented.

### A Recipe provides data.

A Recipe selects a Workflow and provides the parameter values required to execute it.

Recipes contain data only. Behavior belongs to Workflows.

### Workflow execution

The Core executes a Workflow by resolving each Task through the Capability Registry.

Workflow
↓
Task
↓
Required Capability
↓
Capability Registry
↓
Module

### Workflow compatibility

A Workflow is executable when every required Task can be resolved using the available Capabilities.

Compatibility is determined by available Capabilities rather than machine models.

## Consequences

- Workflows remain machine independent.
- Recipes remain data only.
- Tasks define Parameter Contracts.
- Modules remain implementation specific.
- Capability resolution is performed exclusively by the Core.

## Validation

**Implementation Status:** Planned

This decision will be validated once the same Workflow successfully executes on multiple machine configurations using different Module implementations.

## Related ADRs

- ADR-0000 – Engineering Philosophy
- ADR-0001 – Core and Module Architecture
- ADR-0003 – Capability Model
- ADR-0004 – Module Lifecycle

## Key Statement

> A Workflow defines behavior.

> A Task defines execution requirements.

> A Recipe provides data.

> The Core resolves execution.

## Future Revisions

Future specifications may define Parameter Contracts, workflow serialization, validation, composition and policy models.
