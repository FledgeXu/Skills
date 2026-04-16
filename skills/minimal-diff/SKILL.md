---
name: minimal-diff
description: Use this skill for narrow bug fixes, review-driven patches, hotfixes, and local changes where scope discipline matters more than broad cleanup.
---

# Minimal Diff

## Goal

Solve the task with the smallest coherent change that fully addresses the issue.

This skill protects reviewability, reduces accidental breakage, and avoids unnecessary churn.

## Use this skill when

- fixing a bug
- addressing code review comments
- patching legacy code
- making targeted behavior changes
- working in a large or fragile codebase

## Rules

### 1. Change only what is needed

Prefer:

- narrow local fixes
- one stable abstraction adjustment
- small extractions only when they reduce duplication or clarify the fix

Avoid:

- opportunistic refactors
- style churn unrelated to the fix
- broad renaming
- architecture shifts not required by the task

### 2. Preserve existing patterns unless they are the bug

Do not introduce:

- a second style for the same responsibility
- new abstractions just to look cleaner
- additional indirection without payoff

### 3. Keep the patch reviewable

A good patch should make it easy to answer:

- what broke?
- what changed?
- why this fix?
- what behavior is now protected?

### 4. Refactor only if necessary

Refactor only when it directly:

- enables the fix
- removes the exact duplication causing the bug
- clarifies the broken boundary
- reduces recurrence risk with minimal added surface

### 5. Preserve data flow clarity

Do not widen scope just because the surrounding flow could be cleaner.
Only touch neighboring flow stages when they directly affect correctness.

## Decision test

Before expanding scope, ask:

- does this line need to change to fix the bug?
- does this extraction materially improve correctness?
- will this extra cleanup make review harder?

If the answer is unclear, do less.

## Output checklist

Report:

- what was changed
- what was deliberately not changed
- whether any small refactor was necessary for correctness
- what focused verification was run

## Hard rules

- Narrow is better than broad.
- Correct and reviewable beats ambitious cleanup.
- Do not smuggle refactors into a bug fix.
