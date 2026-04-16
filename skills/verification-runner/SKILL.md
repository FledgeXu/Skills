---
name: verification-runner
description: Use this skill after code changes to choose and run the smallest meaningful lint, type-check, and test commands, then report verification honestly.
---

# Verification Runner

## Goal

Do not claim completion without verification when runnable checks are available.

Prefer the smallest meaningful verification first, then expand only when necessary.

## Use this skill when

- any code change was made
- a bug fix was applied
- a refactor was completed
- a new abstraction was introduced
- a schema or contract changed

## Verification strategy

### 1. Start with focused checks

Prefer:

- lint changed files
- type-check affected modules
- run focused tests near the changed code
- run one targeted command that exercises the changed behavior

### 2. Expand only if needed

Escalate to broader checks when:

- the change affects shared abstractions
- type contracts changed
- integration points changed
- focused checks are insufficient to establish confidence

### 3. Verify data-flow-sensitive changes appropriately

If the change affects shape transitions or boundary mappings, prioritize:

- tests around normalization
- tests around validation
- tests around serialization / deserialization
- tests around mapper behavior
- static checking of the affected boundary types

### 4. Report verification precisely

State:

- what commands were run
- what passed
- what was not run
- what residual uncertainty remains, if any

## Verification order

Typical order:

1. formatting / lint for touched files
2. type-check for affected module or package
3. focused tests
4. broader tests only when justified

## Honesty rules

Do not say:

- "verified" if nothing was run
- "all good" when checks failed
- "fixed" if only a hypothesis was applied without validation

If checks could not be run, say:

- why not
- what was checked instead
- what remains unverified

## Output checklist

Always report:

- commands run
- results
- skipped checks
- any remaining risk

## Hard rules

- Verification is part of the task, not an optional extra.
- Focused verification is preferred to noisy broad runs.
- Claims must match actual evidence.
