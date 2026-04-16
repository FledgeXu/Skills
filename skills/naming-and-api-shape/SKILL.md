---
name: naming-and-api-shape
description: Use this skill when introducing or changing public names, functions, modules, DTOs, helper APIs, or abstractions to keep naming precise and interfaces clean.
---

# Naming and API Shape

## Goal

Use semantically precise names and clean interfaces.

The name should reveal the responsibility.
The API should make the correct usage obvious.

## Use this skill when

- naming a new function, module, class, type, or field
- changing a public API
- extracting an abstraction
- reviewing helper names and parameter shape
- cleaning up confusing interfaces

## Naming rules

Prefer names that:

- use stable domain terminology
- distinguish data from behavior
- distinguish transformation from orchestration
- indicate collection vs single value clearly
- reflect responsibility, not implementation trivia

Prefer:

- plural names for collections
- nouns for data types
- verbs for actions
- names that match neighboring terminology

Avoid:

- vague names like `util`, `helper`, `manager`, `processor`, `data`, `common`
- synonyms for existing concepts
- names that promise more abstraction than actually exists
- names that leak temporary implementation details

## Name by role in the data flow

Prefer names that reveal where a value or function sits in the data flow.

Examples:

- parse / normalize / validate / map / build / serialize / persist
- raw / normalized / validated / domain / response

Names should help the reader infer:

- what shape is being handled
- whether the value is boundary data or domain data
- whether the function transforms, validates, or orchestrates

## API shape rules

Prefer:

- small explicit interfaces
- explicit input / output contracts
- return values over hidden mutation
- domain-shaped parameter objects when many parameters would otherwise accumulate
- APIs that preserve type information clearly

Avoid:

- boolean flag soup
- overloaded convenience signatures with hidden behavior
- order-dependent APIs with undocumented sequencing constraints
- interfaces that mix transformation, side effects, and orchestration

## Review questions

Before finalizing a name or API, ask:

- does the name match repository terminology?
- does it describe responsibility precisely?
- can a caller predict behavior from the signature?
- is collection vs single-item semantics obvious?
- is this API encouraging the right usage pattern?

## Output checklist

Report:

- why the chosen name is more precise
- what ambiguous naming was avoided
- why the API shape is easier to use correctly
- whether the interface aligns with existing repository terminology

## Hard rules

- Precision beats convenience.
- Stable domain language beats local shorthand.
- Good APIs make misuse harder.
