# ADR-0000 – Engineering Philosophy

**Status:** Accepted

**Date:** 2026-07-12

## Context

The Cremiqa project aims to become a long-lived, modular platform for coffee automation.

Architecture decisions should remain consistent over many years and contributors. To achieve this, technical decisions must be guided by a small set of engineering principles rather than personal preference or short-term optimization.

## Decision

### Readability over cleverness

Code is read significantly more often than it is written.

Every implementation should optimize for clarity first.

### No magic

Avoid hidden behavior, implicit dependencies and unexplained constants.

Every important decision should have a visible reason.

### Simplicity over complexity

If a simpler model exists without sacrificing correctness, prefer the simpler model.

Complexity must always justify itself.

### Composition over specialization

Systems should be assembled from small, well-defined building blocks.

Avoid inheritance-based designs when composition naturally models the domain.

### Stable abstractions

The Core depends only on abstractions.

Concrete implementations belong outside the Core.

### Prefer artifacts over discussions

Ideas become valuable once they exist as code, documentation or diagrams.

Create a baseline early and iterate on the artifact.

### Design for tomorrow. Build for today.

Architecture should anticipate growth.

Implementation should solve today's problem without unnecessary complexity.

### Don't reinvent. Integrate.

Use proven engineering concepts whenever possible.

Innovation comes from combining good ideas into a coherent platform rather than inventing everything from scratch.

### Documentation is source code

Documentation is versioned, reviewed and maintained with the same discipline as code.

### Documentation is part of the product

Architecture decisions, design rationale and engineering principles are first-class project artifacts.

Important decisions must be captured as ADRs.

## Consequences

All future design and implementation decisions should be evaluated against these principles.

When a decision conflicts with one of these principles, the burden of proof lies with the more complex solution.
