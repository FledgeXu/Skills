---
name: reuse-first
description: Use this skill before implementing features, bug fixes, utilities, adapters, services, hooks, scripts, or abstractions. It enforces reuse-first analysis and duplicate-logic avoidance.
---

# Reuse First

## Goal

Do not create parallel logic when existing code can be extended safely.

Default preference order:

1. extend an existing abstraction
2. reuse an existing module with a small adaptation
3. use a mature package
4. add a small new abstraction
5. write one-off custom infrastructure only as a last resort

## Use this skill when

- adding a feature
- fixing a bug
- adding a helper / utility / service / adapter / hook
- refactoring overlapping logic
- introducing a new abstraction
- considering a new dependency

## Required procedure

### 1. Search for nearby prior art

Inspect:

- neighboring modules
- helper functions
- adapters
- schemas / DTOs / models
- test fixtures
- scripts
- existing abstractions with similar responsibility

### 2. Reuse by data-flow similarity

Do not look only for similar names.
Also look for:

- similar input and output shapes
- similar normalization steps
- similar validation stages
- similar transformation pipelines
- similar boundary translations

### 3. Identify reuse candidates

List concrete reuse candidates:

- files
- functions
- classes
- interfaces
- schemas
- package wrappers

For each candidate, decide:

- can it be extended directly?
- can it be generalized without harming clarity?
- would reusing it preserve architecture?

### 4. Avoid duplicate logic

Do not:

- create a second utility because the first one is inconvenient
- add a "new" / "v2" / "enhanced" path for the same responsibility
- copy logic and rename it
- create a parallel abstraction with slightly different API shape

### 5. Decide whether a package is better

Before writing infrastructure-like custom code, evaluate whether a package already solves it.

Typical candidates:

- parsing
- validation
- retries / backoff
- config loading
- structured logging
- serialization
- filesystem abstraction
- CLI plumbing
- auth / policy adapters
- testing helpers

### 6. Choose the narrowest correct change

Prefer:

- extending one existing path
- extracting one stable shared helper
- reusing stable data contracts

Avoid:

- broad cleanup
- opportunistic refactors
- adding a second architectural pattern

## Output checklist

Before finishing, state briefly:

- what existing code was reused
- what duplicate path was avoided
- whether a package was considered
- why the chosen path best matches the repository

## Hard rules

- Reuse before rewrite.
- Generalize before duplicate.
- Prefer one stable abstraction over two similar ones.
- If new code overlaps strongly with old code, stop and refactor the boundary first.
