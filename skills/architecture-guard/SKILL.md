---
name: architecture-guard
description: Use this skill when a task crosses layers, changes boundaries, introduces a pattern, or affects the repository’s architectural consistency.
---

# Architecture Guard

## Goal

Preserve the repository’s architectural coherence through stable boundaries, established abstractions, and one pattern for each responsibility.

## Use this skill when

- changing shared modules
- adding a service, adapter, or layer
- moving logic across boundaries
- replacing abstractions
- working in an established layered codebase

## User-confirmed test-driven development

Before executable boundary changes, identify test points that protect meaningful ownership, dependency, and integration behavior. Treat test points explicitly stated by the user as confirmed; otherwise propose focused test points and obtain user confirmation. Validate configuration and documentation through parsers, schemas, linters, formatters, or focused review.

After confirmation, use Red → Green → Refactor:

1. Write or update a focused test before changing implementation.
2. Capture the expected ownership, dependency direction, or boundary translation.
3. Confirm the test fails at the intended architectural seam.
4. Make the smallest boundary-preserving change that passes.
5. Refactor after focused and integration tests are green.

## Required checks

### 1. Identify current boundaries

Map domain logic, orchestration, I/O, adapters, transport, persistence, and presentation layers.

### 2. Respect existing responsibilities

Identify the owning layer, dependency direction, established pattern, and required translation point.

### 3. Protect boundary shapes

Use transport shapes for transport, domain shapes for domain logic, persistence shapes for persistence, and explicit translation points between them.

### 4. Maintain architectural alignment

Route I/O through adapters, keep persistence at its boundary, translate transport and domain shapes explicitly, and use established extension points.

### 5. Justify new abstractions positively

Introduce a layer or abstraction when it captures a stable concept, removes recurring duplication, protects a useful boundary, and improves overall consistency.

## Prompt-writing standard

Write every new prompt as a positive, actionable instruction. State the intended owner, boundary, dependency direction, and accepted pattern.

## Output checklist

Report the preserved boundary, cross-layer changes, abstraction decision, neighboring pattern alignment, and proportional verification evidence.

## Hard rules

- Treat consistency as a feature.
- Provide explicit justification for each boundary change.
- Keep one established pattern for each responsibility.
