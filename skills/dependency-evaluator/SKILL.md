---
name: dependency-evaluator
description: Use this skill when deciding whether to adopt a package or build custom code. It evaluates fit, maintenance cost, lock-in, architecture impact, and long-term clarity.
---

# Dependency Evaluator

## Goal

Do not default to custom infrastructure when a mature package fits.
Do not add dependencies casually when local code is simpler and more stable.

## Use this skill when

- a new package is being considered
- someone proposes writing custom infrastructure
- replacing an existing package
- building generic plumbing such as config, validation, retries, logging, CLI, adapters, parsing, or serialization

## Evaluation criteria

For each option, evaluate:

### 1. Functional fit

- Does it solve the actual problem?
- Does it match the current architecture?
- Does it support the required data model and workflow?
- Does it reduce custom glue code?

### 2. Complexity cost

- Does it simplify implementation?
- Does it introduce conceptual weight?
- Does it force awkward abstractions?
- Does it create too much framework surface area?

### 3. Maintenance profile

- Is it mature and stable?
- Is the API understandable?
- Is the upgrade burden reasonable?
- Does it reduce or increase bespoke code maintenance?

### 4. Lock-in and portability

- Does it leak into domain code?
- Can it be isolated behind a small boundary?
- Will removal later be expensive?

### 5. Ecosystem compatibility

- Does it work with the project language/runtime/toolchain?
- Does it preserve typing expectations?
- Does it align with the repository’s patterns?

### 6. Data-shape fit

- Does it work with the repository’s existing data shapes?
- Does it preserve or improve clarity of boundary translations?
- Does it make data flow clearer or more opaque?

## Decision guidance

Prefer a package when:

- the problem is generic
- the package is mature
- package fit is strong
- it reduces bespoke infrastructure materially
- the package can be isolated behind a small boundary

Prefer custom code when:

- domain logic is the real complexity
- package fit is poor
- the package is too heavy
- the package would distort architecture
- custom code is truly small, local, and stable

## Required output format

When making a recommendation, state:

### Recommendation

- use package / keep current package / write custom code

### Why

- concrete fit
- concrete tradeoffs
- architecture impact
- type-safety impact
- maintenance impact
- data-flow impact

### Boundary design

- where the package should be isolated
- what internal interface should shield the rest of the code

## Hard rules

- Never recommend custom infrastructure by reflex.
- Never recommend a package without explaining what it replaces.
- Keep dependencies at the edges when possible.
- Keep domain code independent from vendor-specific details.
