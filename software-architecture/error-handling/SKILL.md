---
name: error-handling
description: Use when designing failure behavior, exceptions, result types, retries, validation, error boundaries, cancellation, degradation, or reviewing error messages, logging, and recovery paths.
---

# Error Handling

## Core Principle

Handle errors at the boundary where sufficient context exists to make the right decision.

## Error Classification

| Class | Meaning | Handling |
|---|---|---|
| Validation | Input does not meet contract | Fail fast, return user-safe detail |
| Client/transient | Retry may succeed | Retry with backoff/jitter when safe |
| Conflict | Current state prevents action | Resolve or report conflict |
| Infrastructure | Downstream dependency failed | Isolate, retry, degrade, or fail operation |
| Programming error | Invariant broken | Do not recover silently; surface loudly |

## Design Rules

- Preserve error identity and context across layers; translate at protocol boundaries.
- Do not convert a specific recoverable failure into a generic exception.
- Do not swallow exceptions; either handle, wrap with context, or propagate deliberately.
- Use exceptions for exceptional control flow; use typed results when failure is an expected domain outcome.
- Make retries idempotent and bounded; avoid retrying non-idempotent operations blindly.
- Handle cancellation as a normal state, not an unexpected system failure.

## Boundary Rules

Domain and application code return domain-meaningful results or errors. Transport adapters map them to HTTP, gRPC, queue events, CLI exit codes, or UI state. Infrastructure logs should never replace that decision.

## Message Rules

- Public messages state what happened and what the user can do.
- Internal logs include structured context and correlation identifiers.
- Never log secrets, full credentials, tokens, personal data, or raw payloads unless explicitly required and safe.

## Anti-Patterns

| Pattern | Consequence |
|---|---|
| Catch-all then log-and-continue | Corrupted state, hidden failures |
| Retry loop without bound/backoff | Amplified outage |
| Generic `Error: failed` | No diagnosis path |
| Exceptions for normal validation | Hard control flow and boundary leakage |
| Recovering from broken invariant | Masked defects |
