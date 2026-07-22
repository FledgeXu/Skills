---
name: naming-and-api-shape
description: Use this skill when introducing or changing public names, functions, modules, DTOs, helper APIs, or abstractions to keep naming precise and interfaces clean.
---

# Naming and API Shape

## Goal

Use semantically precise names and interfaces that make correct usage obvious.

## Use this skill when

- naming a function, module, class, type, or field
- changing a public API
- extracting an abstraction
- reviewing helper names and parameter shapes

## Test-driven development

Use Red → Green → Refactor for observable executable API changes. Choose tests that protect meaningful caller behavior, compatibility, or realistic misuse risks. Validate configuration and documentation through parsers, schemas, linters, formatters, or focused review.

1. Write or update a focused test before changing implementation.
2. Express the desired call shape, return value, error behavior, or compatibility contract.
3. Confirm the test fails for the expected API gap.
4. Implement the narrowest precise interface that passes.
5. Refactor names and internals after focused and compatibility tests are green.

## Naming rules

Use stable domain terminology, distinguish data from behavior and transformation from orchestration, indicate collection cardinality, and reflect responsibility.

Prefer plural names for collections, nouns for data types, verbs for actions, and terms already established by neighboring code.

Choose specific role names in place of broad terms such as `util`, `helper`, `manager`, `processor`, `data`, and `common`.

## Name by role in the data flow

Use stage terms such as parse, normalize, validate, map, build, serialize, and persist; use shape terms such as raw, normalized, validated, domain, and response.

Names should reveal the handled shape, boundary role, and operation type.

## API shape rules

Prefer small explicit interfaces, explicit input and output contracts, return values, domain-shaped parameter objects, clear sequencing, and preserved type information.

Keep transformation, side effects, and orchestration visible through focused interfaces.

## Prompt-writing standard

Write every new prompt as a positive, actionable instruction. Specify the intended domain term, responsibility, signature, and correct usage.

## Review questions

Confirm alignment with repository terminology, precise responsibility, predictable behavior, clear cardinality, and an interface that guides correct use.

## Output checklist

Report naming rationale, terminology alignment, API usability, and proportional compatibility evidence.

## Hard rules

- Prefer precision and stable domain language.
- Shape APIs so correct usage is the easiest path.
