# AGENTS.md

## Purpose

This file defines my global engineering preferences.

Default stance:

- test-driven development
- reuse before rewrite
- data shape and flow first
- clear abstractions
- functional, composable design
- strong type and boundary discipline
- small, verifiable changes
- positive, actionable prompts

## How to work

Before changing implementation:

1. identify the core data shapes
2. identify how data flows across boundaries and transformations
3. inspect existing modules, abstractions, and tests for reuse
4. define the desired behavior with a focused failing test
5. prefer extending an existing abstraction over creating a parallel one
6. consider whether a mature package already solves the problem
7. implement the smallest change that passes the test
8. refactor while keeping the test suite green

## Test-driven development

Use Red → Green → Refactor for executable behavior changes:

1. Write or update a focused test before changing implementation.
2. Run the focused test and confirm that it fails for the expected reason.
3. Write the smallest implementation that makes the test pass.
4. Run the focused test and relevant regression checks.
5. Refactor only while all tests remain green.

Treat a test-first sequence as part of the deliverable. Record the failing Red result and the passing Green result in the final report.

Choose tests that protect meaningful behavior, contracts, boundaries, or realistic regression risks. Keep each test proportional to the value and risk of the change.

Reserve automated tests for executable behavior. Treat configuration and documentation changes as validation work, using the relevant parser, schema validator, linter, formatter, or focused review as evidence.

## Prompt-writing standard

Write every new prompt as a positive, actionable instruction.

- State the desired behavior, structure, or outcome directly.
- Replace prohibitions with the preferred action.
- Express constraints as affirmative boundaries and acceptance criteria.
- Preserve this positive style in future edits to this file and every referenced skill.

## Skills are the main mechanism

Use skills automatically whenever relevant.

Default skill mapping:

- use `reuse-first` before adding new code or abstractions
- use `data-shape-and-flow` when designing or refactoring logic
- use `functional-design` for non-trivial implementation structure
- use `typed-change` when a schema, DTO, interface, or model changes
- use `architecture-guard` when crossing module or layer boundaries
- use `dependency-evaluator` when deciding package versus custom code
- use `minimal-diff` for bug fixes and review-driven patches
- use `naming-and-api-shape` when introducing or changing public names or interfaces
- use `verification-runner` after code changes

## Repository-wide rules

- Reuse one canonical implementation for each responsibility.
- Extend the established pattern for a responsibility.
- Let abstractions emerge from stable data shapes and repeated flow.
- Keep side effects at boundaries and transformations explicit.
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
- local state with explicit ownership
- focused changes tied directly to the task

## Reporting expectations

When finishing a task, report briefly:

- what data shapes and flow were identified
- what existing code was reused
- whether a package was considered
- what abstraction or boundary was preserved or introduced
- which test demonstrated Red and Green for executable behavior changes
- which validation evidence covered configuration or documentation changes
