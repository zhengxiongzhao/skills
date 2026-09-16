---
name: engineering-code-review
description: Use when reviewing a diff, pull request, design change, refactor, or implementation for correctness, maintainability, security, tests, migration risk, and merge readiness; also when deciding whether feedback should block or advise.
---

# Engineering Code Review

## Core Principle

Review the change's purpose, risks, and verification evidence before style.

## Review Order

1. Confirm requirements and intended behavior.
2. Inspect correctness and failure modes.
3. Check boundaries, dependency direction, and duplication.
4. Review tests and migration/rollback risk.
5. Review readability and convention consistency.
6. Confirm security and operational impact.

## Evidence Rules

- Claim only what a diff, file, command output, or requirement demonstrates.
| Severity | Use when | Required feedback |
|---|---|---|
| Blocker | Correctness, data loss, security, migration, or regression risk | Concrete evidence, defect scenario, and suggested direction |
| Major | Likely maintainability or reliability problem | Example and pragmatic remedy |
| Minor | Local readability or convention | Suggested edit |
| Nit | Optional preference | Non-blocking, labeled as nit |

- Separate required changes from preferences.
- Do not demand a redesign without explaining the concrete trigger and simpler alternative.

## Overengineering Check

Ask whether the change adds abstraction without a second implementation, real boundary, test need, or meaningful concept. If yes, suggest the simpler version and name the future condition that would justify the abstraction.

## Verification Questions

- What behavior changed and how is it demonstrated?
- Which tests cover failure modes?
- Are migration and rollback paths possible?
- What configuration, feature flag, or deployment sequencing is required?
- What observability changes are needed?

## Review Tone

Be specific and actionable. Focus on the change, not the author. For disagreements, state the tradeoff and the condition that would prove the concern.
