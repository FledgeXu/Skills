---
name: reuse-first
description: Use this skill before implementing features, bug fixes, utilities, adapters, services, hooks, scripts, or abstractions. It enforces reuse-first analysis and canonical logic.
---

# Reuse First

## Goal

Extend existing code safely and keep one canonical implementation for each responsibility.

Default preference order:

1. extend an existing abstraction
2. reuse an existing module with a small adaptation
3. use a mature package
4. add a small new abstraction
5. write focused custom infrastructure after the earlier options prove unsuitable

## Use this skill when

- adding a feature or fixing a bug
- adding a helper, utility, service, adapter, or hook
- refactoring overlapping logic
- introducing an abstraction or dependency

## Test-driven development

Use Red → Green → Refactor for executable behavior changes. Choose tests that protect meaningful behavior or realistic regression risks, with effort proportional to the change. Validate configuration and documentation through parsers, schemas, linters, formatters, or focused review.

1. Write or update a focused test before changing implementation.
2. Confirm the test fails for the expected missing or incorrect behavior.
3. Reuse or extend the closest existing path with the smallest passing change.
4. Refactor shared logic while the focused and regression tests stay green.

## Required procedure

### 1. Search for nearby prior art

Inspect neighboring modules, helpers, adapters, contracts, fixtures, scripts, and abstractions with similar responsibility.

### 2. Compare data flow

Compare names together with input and output shapes, normalization, validation, transformation pipelines, and boundary translations.

### 3. Select a reuse candidate

For each concrete candidate, assess direct extension, clarity-preserving generalization, and architectural fit.

### 4. Keep one canonical path

Route equivalent responsibilities through the established utility or abstraction. Give one concept one stable name and API shape.

### 5. Evaluate package fit

For infrastructure such as parsing, validation, retries, configuration, logging, serialization, filesystem access, CLI plumbing, authentication, and testing helpers, compare mature packages with focused local code.

### 6. Choose the narrowest correct change

Prefer one existing path, one stable shared helper, and stable data contracts. Keep cleanup and architectural change tied directly to the tested behavior.

## Prompt-writing standard

Write every new prompt as a positive, actionable instruction. State the preferred reuse behavior and acceptance criteria directly.

## Output checklist

Report the reused code, canonical path, package assessment, and proportional evidence: Red and Green for executable behavior, or focused validation for configuration and documentation.

## Hard rules

- Reuse before rewrite.
- Generalize stable shared flow before adding another implementation.
- Prefer one stable abstraction for one responsibility.
- Refactor the shared boundary first when new work overlaps strongly with existing code.
