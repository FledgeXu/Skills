---
name: functional-design
description: Use this skill when writing or refactoring logic into clearer, more composable, more functional code with isolated side effects and explicit data flow.
---

# Functional Design

## Goal

Prefer explicit inputs and outputs, composition, pure transformations, isolated side effects, and small reusable units.

## Use this skill when

- writing business logic
- refactoring procedural functions
- extracting reusable transformations
- isolating I/O from pure computation
- clarifying multi-step pipelines

## User-confirmed test-driven development

Before executable logic changes, identify test points that protect meaningful behavior or realistic regression risks, with effort proportional to the logic. Treat test points explicitly stated by the user as confirmed; otherwise propose focused test points and obtain user confirmation. Validate configuration and documentation through parsers, schemas, linters, formatters, or focused review.

After confirmation, use Red → Green → Refactor:

1. Write or update a focused test before changing implementation.
2. Describe observable behavior through explicit input and output values.
3. Confirm the focused test fails for the expected reason.
4. Add the smallest pure transformation or boundary orchestration needed for Green.
5. Refactor toward composition while all relevant tests remain green.

## Core principles

### 1. Separate pure logic from side effects

Place pure transformations in independently testable functions, side effects at system boundaries, and wiring in thin orchestration.

### 2. Design from data flow

Map input, normalized, validated, transformed or enriched, and final output shapes before extracting functions.

### 3. Prefer composition

Use small single-responsibility functions, pipeline-like flow, stable intermediate representations, and helpers with explicit contracts.

### 4. Keep data flow explicit

Each step should reveal what it consumes, returns, preserves, and whether it performs a side effect.

### 5. Use abstraction honestly

Extract abstractions that remove real duplication, capture stable concepts, improve composability, and keep tracing easy. Keep simple local logic visible when extraction adds little value.

## Refactoring pattern

1. Identify boundary effects such as I/O, network, filesystem, database, logging, and environment access.
2. Identify pure stages such as parsing, normalization, validation, mapping, reduction, filtering, and derivation.
3. Extract stable pure helpers with explicit input and return types and locally owned immutable values.
4. Keep orchestration thin and readable.

## Prompt-writing standard

Write every new prompt as a positive, actionable instruction. Specify the desired composition, boundary placement, and observable behavior.

## Output checklist

Report isolated effects, pure transformations, clarified flow stages, reused logic, and proportional verification evidence.

## Hard rules

- Place side effects at boundaries.
- Make pure logic testable with direct values and lightweight fixtures.
- Prefer composition and readable flow.
- Extract abstractions after shapes and transformation stages are clear.
