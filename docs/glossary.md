# Cremiqa Architecture Glossary

This glossary defines the common vocabulary used throughout the Cremiqa project.

## Core

The orchestration engine of the platform.

The Core owns behavior, discovers Capabilities, executes Workflows and coordinates Modules.

See: ADR-0001

## Module

A self-contained unit of responsibility that owns its implementation and lifecycle, and publishes one or more Capabilities.

Modules may represent hardware, software, integrations or simulations.

Modules may themselves be composed of other Modules.

See: ADR-0001

## Capability

A semantic contract describing what the platform can do.

Capabilities form the common vocabulary of the platform.

A Capability describes what, never how.

Capabilities are immutable and contain no implementation, configuration or runtime state.

See: ADR-0003

## Workflow

A machine-independent sequence of tasks that consumes Capabilities.

## Recipe

A declarative description of a beverage or operation.

## Machine

A physical or virtual coffee machine represented by one or more Modules.

## Platform

The complete Cremiqa ecosystem.

## Implementation

The concrete realization of a Capability provided by a Module.

## Semantic Contract

A stable architectural concept describing meaning rather than implementation.

## Responsibility

A well-defined concern owned by exactly one Module.

## Composition

Building larger Modules from smaller Modules.

## Platform Vocabulary

The collection of all Capability definitions understood by the platform.

## Reserved Terms

Core, Module, Capability, Workflow, Recipe, Implementation, Responsibility
