# Cremiqa Architecture Glossary

This glossary defines the common vocabulary used throughout the Cremiqa project.

Architectural rationale belongs in the corresponding Architecture Decision Records (ADRs). This glossary is the authoritative source for architectural terminology.

## Concept Relationship Map

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

---

## Core

The orchestration engine of the platform.

The Core discovers Modules, validates the system, registers Capabilities and executes Workflows.

**See:** ADR-0001, ADR-0004

---

## Module

A self-contained unit of responsibility that owns its implementation and lifecycle, and declares one or more Capabilities.

Modules may represent hardware, software, integrations or simulations.

Modules may themselves be composed of other Modules.

**See:** ADR-0001, ADR-0004

---

## Capability

A semantic contract describing what the platform can do.

Capabilities describe **what**, never **how**.

Capabilities contain no implementation, configuration or runtime state.

**See:** ADR-0003

---

## Workflow

A declarative description of behavior expressed as an ordered sequence of Tasks.

A Workflow defines behavior.

A Workflow never depends on concrete Module implementations.

**See:** ADR-0005

---

## Task

The smallest declarative unit of behavior within a Workflow.

A Task defines:

- the required Capability
- a Parameter Contract

A Task describes what must happen.

It never specifies how the action is implemented.

**See:** ADR-0005

---

## Parameter Contract

A contract defined by a Task describing the data required for its execution.

The structure of a Parameter Contract is defined by platform specifications rather than ADRs.

**See:** ADR-0005

---

## Recipe

A declarative description of the data required to execute a Workflow.

A Recipe:

- selects a Workflow
- provides parameter values

Recipes contain data only.

Behavior belongs to Workflows.

**See:** ADR-0005

---

## Workflow Compatibility

The ability to execute a Workflow using the currently available Capabilities.

Compatibility is determined by Capabilities rather than machine models.

**See:** ADR-0005

---

## Availability

The state indicating whether a Module is ready to participate in the platform.

Availability is defined by the Module Lifecycle and is independent from runtime operation.

**See:** ADR-0004

---

## Runtime State

The current operational state of a Module while executing Workflows.

Runtime State is independent from the Module Lifecycle.

**See:** ADR-0004

---

## Core Boot Process

The sequence executed by the Core before the platform becomes operational.

It includes Module discovery, identification, configuration orchestration, validation and Capability registration.

**See:** ADR-0004

---

## Machine

A physical or virtual coffee machine represented by one or more Modules.

---

## Platform

The complete Cremiqa ecosystem consisting of the Core, Modules, Capabilities, Workflows, Recipes and supporting infrastructure.

---

## Implementation

The concrete realization of a Capability provided by a Module.

---

## Semantic Contract

A stable architectural concept describing meaning rather than implementation.

Capabilities are semantic contracts.

**See:** ADR-0003

---

## Responsibility

A well-defined concern owned by exactly one Module.

---

## Composition

The practice of building larger Modules from smaller Modules.

Composition is preferred over specialization whenever possible.

**See:** ADR-0000

---

## Platform Vocabulary

The collection of all Capability definitions understood by the platform.

---

## Reserved Terms

The following terms have precise architectural meanings within the Cremiqa project and should not be used interchangeably:

- Core
- Module
- Capability
- Workflow
- Task
- Parameter Contract
- Recipe
- Implementation
- Responsibility
