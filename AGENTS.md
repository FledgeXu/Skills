# AGENTS.md

## Purpose

This file defines my global engineering preferences.

Default stance:

- reuse before rewrite
- data shape and flow first
- clear abstractions
- functional, composable design
- strong type and boundary discipline
- small, verifiable changes

## How to work

Before writing code:

1. identify the core data shapes
2. identify how data flows across boundaries and transformations
3. inspect existing modules, abstractions, and tests for reuse
4. prefer extending an existing abstraction over creating a parallel one
5. consider whether a mature package already solves the problem
6. keep the final change narrow, explicit, and easy to verify

## Skills are the main mechanism

Use skills automatically whenever relevant.

Default skill mapping:

- use `reuse-first` before adding new code or abstractions
- use `data-shape-and-flow` when designing or refactoring logic
- use `functional-design` for non-trivial implementation structure
- use `typed-change` when a schema, DTO, interface, or model changes
- use `architecture-guard` when crossing module or layer boundaries
- use `dependency-evaluator` when deciding package vs custom code
- use `minimal-diff` for bug fixes and review-driven patches
- use `naming-and-api-shape` when introducing or changing public names or interfaces
- use `verification-runner` after code changes

## Repository-wide rules

- Do not introduce duplicate logic with different names.
- Do not add a second pattern for the same responsibility without strong justification.
- Let abstractions emerge from stable data shapes and repeated flow, not from premature generalization.
- Keep side effects at boundaries and keep transformations explicit.
- Prefer one clear canonical shape per layer, with explicit translation between layers.
- Preserve type safety and contract integrity across boundaries.
- Run the smallest meaningful verification available before claiming completion.

## Coding preferences

Prefer:

- code designed from data shape and flow
- small composable functions
- explicit contracts
- narrow public APIs
- pure transformations where practical
- stable intermediate representations
- explicit normalization, validation, and mapping stages
- names that reveal role in the data flow

Avoid:

- hidden mutable state
- loosely structured data flowing through many layers
- giant procedural functions mixing parsing, validation, transformation, I/O, and logging
- vague names and convenience abstractions with unclear ownership
- broad cleanup unrelated to the task
- abstractions that hide where data changes shape

## Reporting expectations

When finishing a task, report briefly:

- what data shapes and flow were identified
- what existing code was reused
- whether a package was considered
- what abstraction or boundary was preserved or introduced
- what verification was run
