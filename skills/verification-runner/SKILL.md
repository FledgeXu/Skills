---
name: verification-runner
description: Use this skill after code changes to choose and run the smallest meaningful lint, type-check, and test commands, then report verification honestly.
---

# Verification Runner

## Goal

Support every completion claim with runnable evidence, starting with the smallest meaningful check.

## Use this skill when

- any code or prompt change was made
- a bug fix or refactor was completed
- an abstraction, schema, or contract changed

## User-confirmed test-driven development

Before executable behavior changes, identify test points that protect meaningful behavior, contracts, boundaries, or realistic regression risks, with effort proportional to the change. Treat test points explicitly stated by the user as confirmed; otherwise propose focused test points and obtain user confirmation. Validate configuration and documentation through parsers, schemas, linters, formatters, or focused review.

After confirmation, use Red → Green → Refactor as the verification timeline:

1. Write or update a focused test before changing implementation.
2. Run it and record the expected Red result.
3. Run it again after implementation and record the Green result.
4. Run the smallest relevant lint, type, regression, and integration checks.
5. Refactor while keeping the selected checks green.

## Verification strategy

### 1. Start with focused checks

Lint changed files, type-check affected modules, run nearby focused tests, and exercise the changed behavior directly.

### 2. Expand according to impact

Add broader checks for shared abstractions, type contracts, integration points, and other affected consumers.

### 3. Verify data-flow-sensitive changes

Prioritize normalization, validation, serialization, deserialization, mapping, and boundary-type checks.

### 4. Report verification precisely

State commands, results, skipped checks with their reason, and residual uncertainty.

## Verification order

1. confirm the test points with the user
2. focused test in Red
3. focused test in Green
4. formatting and lint for touched files
5. type-check for affected modules
6. focused regression tests
7. broader tests proportional to impact

## Evidence rules

- Use “verified” after running the relevant checks.
- Use “passing” when the reported checks passed.
- Use “fixed” after validation demonstrates the corrected behavior.
- Describe unavailable checks, the substitute evidence, and remaining uncertainty precisely.

## Prompt-writing standard

Write every new prompt as a positive, actionable instruction. Specify the test points to confirm and the evidence required for Red, Green, regression coverage, and honest reporting.

## Output checklist

Always report commands, proportional evidence, skipped checks, and remaining risk. Include confirmed test points and Red and Green results for executable behavior changes.

## Hard rules

- Treat verification as part of the task.
- Prefer focused evidence before broader suites.
- Match every claim to actual evidence.
