---
name: data-shape-and-flow
description: Use this skill when designing or refactoring code that depends on clear data structures, boundary shapes, and explicit transformation flow across layers.
---

# Data Shape and Flow

## Goal

Design code from the shape of data and the path it takes through the system.

Good abstractions should emerge from:

- stable data structures
- clear boundary shapes
- explicit transformation stages
- visible invariants

## Use this skill when

- designing a new module
- introducing DTOs, schemas, models, or interfaces
- refactoring long transformation-heavy functions
- building adapters, pipelines, ETL flows, or service boundaries
- moving data across architectural layers

## Core principles

### 1. Start from shape

Before designing functions or abstractions, identify:

- source input shape
- normalized shape
- validated shape
- domain shape
- output shape
- persistence or transport shape if applicable

### 2. Make transformations explicit

Prefer explicit stages such as:

- parse
- normalize
- validate
- enrich
- map
- aggregate
- serialize

Do not hide multiple shape transitions inside one opaque function.

### 3. Keep one canonical shape per layer

Prefer:

- transport shapes at boundaries
- domain shapes in core logic
- persistence shapes near storage
- explicit translators between them

Avoid:

- one loose mutable structure passed through every layer
- hidden field injection
- silent shape drift

### 4. Let abstractions follow flow

Extract abstractions only after the data flow is clear.

Good abstractions:

- match real transformation stages
- preserve visibility of inputs and outputs
- reduce repeated shape handling
- improve testability

Bad abstractions:

- obscure where data changes shape
- merge unrelated stages too early
- hide invariants

### 5. Protect invariants

For each stage, make clear:

- what is guaranteed now
- what has been validated
- what remains optional or unresolved

### 6. Keep translations narrow

Boundary translations should be:

- explicit
- local
- typed
- easy to test

Do not let translation logic leak everywhere.

## Review checklist

Before finishing, confirm:

- are the main shapes explicit?
- are boundary translations visible?
- is each transformation stage easy to locate?
- does naming reflect role in the flow?
- are side effects separated from transformation?

## Hard rules

- Design from data flow, not from arbitrary layering.
- Shape changes must be explicit.
- One layer should not casually leak its shape into another.
- Abstractions should clarify flow, not hide it.
