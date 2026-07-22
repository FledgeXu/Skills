---
name: minimal-diff
description: Use this skill for narrow bug fixes, review-driven patches, hotfixes, and local changes where scope discipline matters more than broad cleanup.
---

# Minimal Diff

## Goal

Solve the task with the smallest coherent change that fully addresses the issue and stays easy to review.

## Use this skill when

- fixing a bug
- addressing code review comments
- patching legacy code
- making targeted behavior changes
- working in a large or fragile codebase

## Test-driven development

Use Red → Green → Refactor for targeted executable behavior changes. Choose the smallest test that protects meaningful behavior or a realistic recurrence risk. Validate configuration and documentation through parsers, schemas, linters, formatters, or focused review.

1. Write or update a focused test before changing implementation.
2. Confirm the test fails for the reported behavior.
3. Change the smallest implementation surface that makes it pass.
4. Run focused regression checks.
5. Refactor only within the tested surface while all checks stay green.

## Rules

### 1. Change the required surface

Prefer narrow local fixes, one stable abstraction adjustment, and small extractions that directly improve correctness or remove causal duplication.

### 2. Preserve established patterns

Use the existing style and responsibility boundary. Introduce indirection when it provides a concrete correctness or reuse benefit.

### 3. Keep the patch reviewable

A reviewer should quickly see the failing behavior, changed lines, reason for the fix, and protecting test.

### 4. Tie refactoring to correctness

Refactor when it enables the fix, removes causal duplication, clarifies the broken boundary, or reduces recurrence risk with a small surface.

### 5. Preserve data-flow clarity

Touch neighboring flow stages when they directly affect the tested correctness.

## Decision test

Before expanding scope, identify the direct correctness benefit, review impact, and test coverage for each additional line.

## Prompt-writing standard

Write every new prompt as a positive, actionable instruction. Describe the exact desired behavior and the smallest accepted scope.

## Output checklist

Report changed scope, preserved surrounding scope, required refactoring, and proportional verification evidence.

## Hard rules

- Prefer a narrow coherent patch.
- Optimize for correctness and reviewability.
- Keep refactoring directly connected to the tested fix.
