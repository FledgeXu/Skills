---
name: dependency-evaluator
description: Use this skill when deciding whether to adopt a package or build custom code. It evaluates fit, maintenance cost, lock-in, architecture impact, and long-term clarity.
---

# Dependency Evaluator

## Goal

Choose the option with the strongest functional fit, architectural alignment, type safety, and maintenance profile. Favor a mature package for generic infrastructure and focused local code for small stable domain behavior.

## Use this skill when

- considering, replacing, or removing a package
- proposing custom infrastructure
- building configuration, validation, retry, logging, CLI, adapter, parsing, or serialization plumbing

## User-confirmed test-driven development

Before delivering executable behavior with the selected option, identify test points that protect required capabilities and realistic integration risks. Treat test points explicitly stated by the user as confirmed; otherwise propose focused test points and obtain user confirmation. Validate configuration and documentation through parsers, schemas, linters, formatters, or focused review.

After confirmation, use Red → Green → Refactor:

1. Write or update a focused test before changing implementation.
2. Express required behavior and boundary expectations independently of the candidate implementation.
3. Confirm the test fails for the expected capability gap.
4. Integrate the smallest suitable package surface or local implementation.
5. Refactor the adapter after focused and integration tests are green.

## Evaluation criteria

Evaluate each option for functional fit, implementation simplicity, conceptual weight, maintenance maturity, upgrade burden, portability, ecosystem compatibility, typing, data-shape fit, and boundary isolation.

## Decision guidance

Prefer a package when the problem is generic, package fit is strong, maturity is high, bespoke infrastructure decreases materially, and a small boundary can isolate it.

Prefer custom code when domain logic carries the complexity, package fit is weak, framework weight exceeds its benefit, and local code remains small and stable.

## Required output format

### Recommendation

- use package, keep current package, or write custom code

### Why

- concrete fit and tradeoffs
- architecture, type-safety, maintenance, and data-flow impact

### Boundary design

- isolation point and internal interface

### Verification evidence

- confirmed test points plus Red and Green for executable behavior, or focused validation for configuration and documentation

## Prompt-writing standard

Write every new prompt as a positive, actionable instruction. Describe the desired evaluation, selection criteria, and boundary outcome.

## Hard rules

- Evaluate mature packages before choosing custom infrastructure.
- Explain the capability and custom code each package replaces.
- Keep dependencies at edges and domain code vendor-independent.
