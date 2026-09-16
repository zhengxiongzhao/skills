---
name: testing
description: Use when planning or implementing tests, choosing unit/integration/contract/e2e scope, test doubles, coverage strategy, test seams, or diagnosing slow, brittle, redundant, or production-coupled tests.
---

# Testing

## Core Principle

Tests should verify behavior and boundaries, not implementation details.

## Test Selection

| Type | Verifies |
|---|---|
| Unit | Pure logic and invariants in isolation |
| Integration | Interaction with database, queue, HTTP, filesystem, container |
| Contract | Interface compatibility between producer and consumer |
| E2E | Critical user journeys through the real delivery surface |

Prefer fast tests for branching behavior. Use expensive tests for boundaries where wiring and environmental risk matter.

## Boundary Rules

- Do not mock the implementation under test.
- Mock only dependencies outside the behavior under test.
- Use real infrastructure for integration risk when feasible and fast enough.
- Test public behavior first; inspect internals only for an invariant not observable externally.
- Do not add a test solely to reach a coverage number.

## Naming And Structure

Describe observable behavior: `given`, `when`, `then`, or a clear behavior sentence. Keep arrange/act/assert structure visible. One logical behavior per test.

## Test Doubles

| Double | Use when |
|---|---|
| Stub | Provide deterministic input |
| Spy | Verify an interaction is an actual requirement |
| Mock | Protocol with the collaborator must be exact |
| Fake | Lightweight working implementation for tests |

If a mock list becomes the test's main content, the design is probably over-coupled.

## Failure Rules

Every failing test must identify a defect, requirement change, or invalid test. Do not delete or weaken it without explaining the reason.
