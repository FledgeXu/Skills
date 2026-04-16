---
name: architecture-guard
description: Use this skill when a task risks crossing layers, bypassing boundaries, introducing a second pattern, or weakening the repository’s architectural consistency.
---

# Architecture Guard

## Goal

Preserve the repository’s architectural coherence.

Do not casually weaken boundaries, bypass stable abstractions, or introduce a second pattern for the same responsibility.

## Use this skill when

- changing shared modules
- adding a new service / adapter / layer
- moving logic across boundaries
- replacing existing abstractions
- touching a codebase with established layering

## Required checks

### 1. Identify current boundaries

Map the local architecture:

- domain logic
- orchestration
- I/O boundaries
- adapters
- transport / DTO layer
- persistence layer
- UI / controller / presentation layer

### 2. Respect existing responsibilities

Ask:

- which layer owns this logic?
- does the proposed change cross a boundary?
- does it force lower-level details into higher-level code?
- does it duplicate an existing pattern?

### 3. Protect boundary shapes

Each architectural layer should have clear data boundaries.

Prefer:

- transport shapes for transport
- domain shapes for domain logic
- persistence shapes for persistence
- explicit translation points between them

Avoid leaking one layer’s shape directly into another unless that simplicity is clearly justified.

### 4. Avoid architectural drift

Do not:

- bypass adapters casually
- place persistence logic in domain transformation code
- mix transport shapes with domain shapes without a clear translation boundary
- introduce convenience shortcuts that weaken the architecture

### 5. Introduce new abstraction only with justification

A new layer or abstraction is justified only when it:

- captures a stable concept
- removes recurring duplication
- protects a useful boundary
- improves consistency more than it increases complexity

## Preferred outcomes

Prefer:

- keeping the current layering intact
- adding small boundary-preserving helpers
- reusing one stable pattern
- making translation points explicit

Avoid:

- second architectures
- ad hoc shortcuts
- "temporary" bypasses that become permanent
- generic layers with no demonstrated reuse

## Output checklist

Report:

- what boundary was preserved
- whether any cross-layer change was needed
- why a new abstraction was or was not introduced
- how the result stays consistent with neighboring code

## Hard rules

- Consistency is a feature.
- Boundary violations require explicit justification.
- One repository should not accumulate multiple competing patterns for the same responsibility.
