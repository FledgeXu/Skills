---
name: functional-design
description: Use this skill when writing or refactoring logic into clearer, more composable, more functional code with isolated side effects and explicit data flow.
---

# Functional Design

## Goal

Prefer functionally structured code:

- explicit inputs and outputs
- composition over mutation-heavy control flow
- pure transformations separated from side effects
- small reusable units

This skill is about clarity, composability, and testability.
It is not about abstraction for its own sake.

## Use this skill when

- writing new business logic
- refactoring long procedural functions
- extracting reusable transformations
- isolating I/O from pure computation
- clarifying multi-step pipelines

## Core principles

### 1. Separate pure logic from side effects

Prefer:

- pure transformation functions
- I/O at the boundary
- orchestration that wires together pure steps

Avoid:

- mixing parsing, validation, transformation, persistence, and logging in one block
- hidden global state
- mutating shared state across phases

### 2. Design from data flow

Before extracting functions, map the flow of data through the operation:

1. identify the input shape
2. identify the normalized shape
3. identify the validated shape
4. identify the transformed or enriched shape
5. identify the final output shape

Prefer each major transformation stage to correspond to a clear function or boundary.

### 3. Prefer composition

Prefer:

- small functions with one responsibility
- pipeline-like flow
- stable intermediate representations
- helpers with explicit contracts

Avoid:

- giant control functions
- deep nested branching when data transformation can be staged
- stateful phase switching unless truly necessary

### 4. Keep data flow explicit

Each step should make it obvious:

- what it consumes
- what it returns
- what invariants it preserves
- whether it performs side effects

### 5. Use abstraction honestly

Extract only when it:

- removes real duplication
- captures a stable concept
- improves composability
- keeps tracing and debugging easy

Do not extract when it:

- hides simple code
- introduces generic layers with no reuse
- makes local logic harder to follow
- obscures where data changes shape

## Refactoring pattern

When refactoring a large procedural block:

1. Identify boundary side effects
   - I/O
   - network
   - file system
   - database
   - logging
   - environment access

2. Identify pure transformation stages
   - parsing
   - normalization
   - validation
   - mapping
   - reduction
   - filtering
   - derivation

3. Extract stable pure helpers
   - explicit input types
   - explicit return types
   - no hidden mutation

4. Leave orchestration thin
   - call pure helpers
   - perform side effects at edges
   - preserve readable control flow

## Output checklist

When using this skill, report:

- what side effects were isolated
- what pure transformations were extracted
- what data-flow stages were clarified
- what duplication was removed
- whether the resulting shape is easier to test

## Hard rules

- Side effects belong at boundaries.
- Pure logic should be testable without environment setup.
- Composition is preferred over mutation-heavy orchestration.
- Do not extract abstractions before the data shapes and transformation stages are clear.
- Readability wins over clever functional style.
