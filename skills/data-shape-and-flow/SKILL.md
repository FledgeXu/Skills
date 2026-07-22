---
name: data-shape-and-flow
description: Use this skill when designing or refactoring code that depends on clear data structures, boundary shapes, and explicit transformation flow across layers.
---

# Data Shape and Flow

## Goal

Design code from stable data structures, clear boundary shapes, explicit transformation stages, and visible invariants.

## Use this skill when

- designing a module or typed contract
- refactoring transformation-heavy functions
- building adapters, pipelines, ETL flows, or service boundaries
- moving data across architectural layers

## Test-driven development

Use Red → Green → Refactor for executable shape or flow changes. Choose tests that protect meaningful transformations, boundaries, or realistic regression risks. Validate configuration and documentation through their parsers, schemas, linters, formatters, or focused review.

1. Write or update a focused test before changing implementation.
2. Express the expected input, intermediate invariant, boundary translation, or output in the test.
3. Confirm the test fails at the intended transformation stage.
4. Implement the smallest explicit shape transition that makes it pass.
5. Refactor after focused and boundary tests are green.

## Core principles

### 1. Start from shape

Identify source, normalized, validated, domain, output, persistence, and transport shapes as applicable.

### 2. Make transformations explicit

Use visible stages such as parse, normalize, validate, enrich, map, aggregate, and serialize. Give each significant shape transition a clear function or boundary.

### 3. Keep one canonical shape per layer

Use transport shapes at transport boundaries, domain shapes in core logic, persistence shapes near storage, and explicit translators between layers.

### 4. Let abstractions follow flow

Extract abstractions after the data flow is clear. Choose abstractions that match real stages, preserve visible inputs and outputs, reduce repeated shape handling, and improve testability.

### 5. Protect invariants

For each stage, state current guarantees, completed validation, and remaining optional or unresolved values.

### 6. Keep translations narrow

Keep boundary translations explicit, local, typed, and easy to test.

## Prompt-writing standard

Write every new prompt as a positive, actionable instruction. Describe the desired shape, transition, invariant, and boundary directly.

## Review checklist

Confirm that main shapes are explicit, translations are visible, transformation stages are locatable, names reveal flow roles, side effects remain at boundaries, and proportional evidence is recorded.

## Hard rules

- Design from data flow and stable shapes.
- Make every shape change explicit.
- Translate shapes at clear layer boundaries.
- Use abstractions that clarify flow.
