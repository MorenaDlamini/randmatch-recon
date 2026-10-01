# Specs

Nothing gets built before its spec and plan are merged.

## The gate

1. Open an issue from the **Feature** form, with Given/When/Then acceptance criteria.
2. Write `specs/<feature>/spec.md` and `specs/<feature>/plan.md` and open a PR containing only those
   two files.
3. The spec reviewer role challenges it. Untestable criteria are rewritten or cut.
4. Merge the spec PR. Only then do implementation PRs start, each one linking back to the spec.

## spec.md

```markdown
# <Feature>

## Problem
Who has it, and what happens today.

## Acceptance criteria
- Given ..., when ..., then ...

## Out of scope

## Risks
What could go wrong, and which test will catch it.
```

## plan.md

```markdown
# Plan: <Feature>

## Approach
Components touched, and a diagram (Mermaid or C4) if more than one is.

## Decisions
Link to any ADR this needs.

## Tests
Risk → test type → test name.

## Steps
Small, independently mergeable PRs.
```
