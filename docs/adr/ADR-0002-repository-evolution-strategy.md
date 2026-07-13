# ADR-0002 -- Repository Evolution Strategy

## Status

Accepted

## Date

2026-07-12

## Context

Cremiqa is designed as a modular platform that is expected to evolve
over time.

Repository boundaries and architectural boundaries intentionally remain
independent.

## Decision

### Architecture comes first

Architectural boundaries SHALL NOT be influenced by repository
boundaries.

Repository layout is an organizational concern and SHALL remain
independent from the architectural model defined by ADR-0001.

### Cremiqa uses a monorepository

All first-party project artifacts live in a single Git repository.

This includes:

-   Core
-   Modules
-   Documentation
-   Tools
-   Examples
-   Tests

### Modules are developed in the monorepository

Every first-party Module is initially developed inside the main
repository.

### Repository extraction is an optimization

A Module MAY be extracted into its own repository once it demonstrates
an independent development lifecycle and the benefits outweigh the
operational cost.

The extraction decision SHALL NOT require architectural changes.

### Design for tomorrow. Build for today.

The repository strategy is optimized for the current stage of the
project while preserving future flexibility.

## Alternatives Considered

### Separate repository for every Module

Rejected due to unnecessary operational overhead during the early stages
of the project.

### Separate repositories for Core and Modules

Rejected because coordinated evolution is expected during the foundation
phase.

### Monorepository

Accepted.

## Consequences

### Positive

-   Single source of truth.
-   Unified versioning.
-   Simplified onboarding.
-   Easier cross-module refactoring.
-   Future repository extraction remains possible.

### Trade-offs

-   Larger repository.
-   Shared CI/CD pipeline.
-   Repository history grows over time.

## Review

This decision SHOULD be revisited only when repository extraction
becomes justified by organizational or technical needs.

## Ownership

### Defines

This ADR is the normative source for:

-   Repository strategy

### References

-   ADR-0000 -- Engineering Philosophy
-   ADR-0001 -- Core and Module Architecture
