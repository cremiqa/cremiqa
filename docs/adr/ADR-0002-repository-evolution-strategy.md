# ADR-0002 – Repository Evolution Strategy

**Status:** Accepted

**Date:** 2026-07-12

## Context

Cremiqa is designed as a modular platform that is expected to grow over time. Repository boundaries and architectural boundaries intentionally remain independent.

## Decision

### Cremiqa uses a monorepository.

All first-party project artifacts live in a single Git repository.

This includes:

- Core
- Modules
- Documentation
- Tools
- Examples
- Tests

### Modularity is an architectural concern.

Repository boundaries must **not** define architectural boundaries.

Modules are architectural building blocks.

Repositories are organizational units.

### Modules live inside the monorepo by default.

Every new Module starts its lifecycle inside the main repository.

### Repository extraction is an optimization.

A Module may become its own repository only after demonstrating an independent lifecycle.

### Design for tomorrow. Build for today.

The repository structure is intentionally optimized for today's needs while allowing future extraction without architectural changes.

### Architecture always comes first.

The architecture must never be compromised to match the repository layout.

## Alternatives Considered

- Separate repository for every Module — rejected due to unnecessary operational overhead.
- Separate repositories for Core and Modules — rejected because coordinated evolution is expected during the early phases.
- Monorepository — selected.

## Consequences

- Single source of truth.
- Unified versioning.
- Simpler onboarding.
- Future extraction remains possible.

## Validation

**Implementation Status:** Planned

This decision will be considered validated only after the project has evolved long enough to demonstrate that the monorepo strategy continues to support development effectively.

## Related ADRs

- ADR-0000 – Engineering Philosophy
- ADR-0001 – Core and Module Architecture

## Future Revisions

Revisit this ADR only when repository extraction becomes justified by organizational or technical needs.
