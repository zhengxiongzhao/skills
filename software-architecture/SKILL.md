---
name: software-architecture
description: Use when designing, structuring, or refactoring a software system, choosing dependency boundaries, or balancing Clean Architecture, SOLID, DDD, design patterns, 12-Factor, and testing priorities. Provides an architecture-first routing model and anti-overengineering rules.
---

# Software Architecture

## Core Principle

First define business capabilities, responsibility boundaries, and dependency direction. Only then choose patterns or abstractions.

Do not add architecture because a methodology permits it. Add architecture when a concrete boundary or change axis makes it useful.

## Decision Order

1. Identify the business/domain model and invariants.
2. Identify real boundaries: domain, application, infrastructure, delivery mechanism.
3. Establish dependency direction: delivery and infrastructure depend on the domain; the domain does not know them.
4. Choose the simplest design that satisfies correctness, testability, and change requirements.
5. Add a pattern only when its explicit problem exists.

## Abstraction Rule

Introduce an abstraction only when at least one condition is true:

- There is a real dependency boundary.
- Multiple implementations are required or clearly foreseeable.
- The dependency must be isolated for tests.
- The domain must remain independent from infrastructure.
- The abstraction names a meaningful business concept.

Otherwise prefer direct code, explicit functions, and small cohesive modules.

## Routing

| Concern | Skill |
|---|---|
| Deployment, config, process, backing services | `12-factor` |
| Layering and dependency direction | `clean-architecture` |
| Class/module responsibility and coupling | `solid` |
| Repeated interaction or construction problem | `design-patterns` |
| Ubiquitous language, bounded contexts, aggregates | `domain-driven-design` |
| Verification strategy and test boundaries | `testing` |
| Public contracts, versioning, validation | `api-design` |
| Failure modes and error boundaries | `error-handling` |
| Logs, metrics, traces, health, alerts | `observability` |
| Change review and merge readiness | `code-review` |

Load only the skills needed for the current decision. Do not mechanically apply every skill to every task.

## Complexity Guardrails

- A CRUD-only feature does not need use cases, domain services, ports, adapters, repositories, and ORM layers.
- Do not create interfaces for one implementation unless the dependency must be replaced or isolated for testing.
- Do not split a module solely to satisfy a layer diagram.
- Do not introduce dependency injection machinery for a small standalone program.
- Do not turn a local utility into a shared library until a second consumer exists.

## Required Reasoning

Before proposing an architectural change, state:

1. The problem being solved.
2. The simplest alternative.
3. Why the proposed design is worth its cost.

If these cannot be answered concretely, keep the current simple design and make only the requested change.

## Output Expectation

For design work, briefly record: assumptions, boundaries, dependency direction, selected tradeoffs, rejected alternatives, and validation plan. For implementation work, follow project conventions and keep changes focused.
