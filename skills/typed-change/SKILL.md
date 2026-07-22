---
name: typed-change
description: Use this skill when changing schemas, DTOs, interfaces, models, validators, serializers, or typed contracts across module boundaries.
---

# Typed Change

## Goal

Preserve and improve type safety across the full propagation path of every data-shape change.

## Use this skill when

- changing request or response shapes
- changing schemas, DTOs, interfaces, or models
- updating serializer or deserializer behavior
- touching typed boundaries in Python, TypeScript, or similar languages

## Test-driven development

Use Red → Green → Refactor for executable contract changes. Choose tests and static checks that protect meaningful boundary behavior and realistic compatibility risks. Validate configuration and documentation through parsers, schemas, linters, formatters, or focused review.

1. Write or update a focused test before changing implementation.
2. Capture the new shape in boundary tests, fixtures, and static expectations.
3. Confirm the focused test or type check fails for the expected contract mismatch.
4. Update the smallest complete producer-to-consumer path that makes it pass.
5. Refactor after runtime tests and static checks are green.

## Required procedure

### 1. Find the full contract surface

Identify producers, consumers, validators, serializers, deserializers, mappers, converters, tests, and user-facing documentation.

### 2. Trace the propagation path

Locate creation, normalization, validation, boundary translation, transformation, reads, field-presence assumptions, nullability, defaults, and enum values.

### 3. Keep shape integrity

Use one canonical shape per layer, explicit translation, narrow boundary mappers, and visible invariants.

### 4. Update linked contracts together

Update types, validators, runtime checks, serialization, parsing, fixtures, and focused tests as one coherent change.

### 5. Maintain contract alignment

Keep every call site, optionality rule, runtime check, and static type synchronized with the canonical shape.

### 6. Verify statically

Run affected-module type checks, boundary-shape tests, and exact fixtures.

## Prompt-writing standard

Write every new prompt as a positive, actionable instruction. State the canonical shape, invariants, propagation path, and verification criteria.

## Output checklist

Report the changed shape, updated producers and consumers, translation point, validator and serializer updates, and proportional verification evidence.

## Hard rules

- Treat every shape change as a full contract-surface change.
- Keep runtime and static contracts synchronized.
- Treat type safety as a core correctness requirement.
