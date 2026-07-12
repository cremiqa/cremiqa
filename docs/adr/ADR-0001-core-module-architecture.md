# ADR-0001 – Core and Module Architecture

**Status:** Accepted

**Date:** 2026-07-12

## Context

Cremiqa is intended to support multiple coffee machines, hardware platforms, sensors, simulations and future extensions without requiring changes to the platform Core.

The architecture therefore needs a stable separation between platform behavior and implementation details.

## Decision

### The Core owns behavior.

The Core is responsible for:

- Module Runtime
- Event Bus
- Workflow Engine
- State Machine
- Capability Registry
- Configuration
- Time

The Core must not contain machine-specific or hardware-specific knowledge.

### Everything else is a Module.

Every concrete implementation is represented as a Module.

Examples include:

- Gaggia Module
- Saeco Module
- Raspberry GPIO Module
- ESP32 Module
- Vision Module
- Scale Module
- Milk Module
- MQTT Module
- Simulator Module

Modules may represent hardware, software, integrations or simulations.

The Core treats them uniformly.

### Modules own implementation.

The Core defines behavior and orchestration.

Modules provide concrete implementations.

A Module may itself be composed of other Modules, allowing complex systems to be built from reusable building blocks.

### Modules provide Capabilities.

A Capability describes **what** can be done, not **how** it is implemented.

Examples include:

- Heat
- Pump
- Temperature
- Pressure
- Weight
- Vision
- Grinder
- Milk
- Cleaning

Capabilities intentionally hide implementation details.

### Workflows depend on Capabilities.

A Workflow expresses a sequence of tasks.

It never depends on a specific machine or Module.

Execution is possible whenever the required Capabilities are available.

### Recipes describe Workflows.

Recipes are machine-independent descriptions of beverage preparation.

Compatibility is determined automatically from the available Capabilities.

Recipes and Workflows may contain **optional tasks**. Missing optional Capabilities must **not** prevent successful recipe execution. Instead, optional tasks are skipped when the required Capability is unavailable.

Examples include:

- Group head cleaning
- Milk system purge
- Crema analysis
- Automatic yield measurement

This allows a single recipe to adapt naturally to machines with different feature sets.

## Architecture

```text
Core
    ↓
Module Runtime
    ↓
Modules
    ↓
Capabilities
    ↓
Workflows
    ↓
Recipes
```

## Consequences

- The Core remains stable while the ecosystem grows through additional Modules.
- Adding support for a new machine should primarily involve creating new Modules rather than modifying existing Core behavior.
- A single Recipe can execute across different machine configurations while gracefully adapting to available Capabilities.

This decision establishes the architectural foundation of the Cremiqa platform.
