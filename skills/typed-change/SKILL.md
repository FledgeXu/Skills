---
name: typed-change
description: Use this skill when changing schemas, DTOs, interfaces, models, validators, serializers, or typed contracts across module boundaries.
---

# Typed Change

## Goal

Preserve and improve type safety whenever a data shape changes.

A shape change is never local unless proven otherwise.

## Use this skill when

- changing request / response shapes
- changing schemas or DTOs
- changing interfaces or models
- updating serializer / deserializer behavior
- touching typed boundaries in Python, TypeScript, or similar languages

## Required procedure

### 1. Find the full contract surface

For the changed shape, identify:

- producers
- consumers
- validators
- serializers / deserializers
- mappers / converters
- tests
- documentation if user-facing

### 2. Trace the propagation path

Ask:

- who creates this shape?
- where is it normalized?
- where is it validated?
- where is it translated across boundaries?
- who transforms it?
- who reads it?
- who assumes field presence, nullability, defaults, or enum values?

### 3. Keep shape integrity

Treat type changes as shape changes.

Prefer:

- one canonical shape per layer
- explicit translation between layers
- narrow boundary mappers
- visible invariants

Do not allow shape drift between layers.

### 4. Update all linked contracts together

When a shape changes, update together:

- type definitions
- validators
- runtime checks
- serializer / parser logic
- test fixtures
- focused tests

### 5. Eliminate hidden shape drift

Do not:

- patch one call site and ignore the rest
- keep stale optionality
- rely on "it still works at runtime"
- silently widen types without reason

### 6. Verify statically where possible

Prefer:

- type-checking affected modules
- tests that cover boundary shapes
- fixtures that reflect the new contract exactly

## Output checklist

Report:

- what shape changed
- which producers and consumers were updated
- where normalization or translation happens
- whether validators and serializers were updated
- what type-check / tests were run

## Hard rules

- If the shape changed, update the contract everywhere it matters.
- Type safety is part of correctness, not optional polish.
- Do not leave runtime and static contracts out of sync.
