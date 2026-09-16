---
name: clean-architecture
description: Use when deciding application layers, module boundaries, dependency inversion, ports/adapters, use cases, repository boundaries, or when code has circular dependencies, infrastructure leakage into domain logic, or hard-to-test business rules.
---

# Clean Architecture

## Core Principle

Business behavior must remain independent of delivery mechanisms and infrastructure. Dependencies point inward.

## Dependency Rule

```text
Delivery / Interface
        ↓
Application Use Cases
        ↓
Domain Model

Infrastructure depends inward; domain depends outward on nothing implementation-specific.
```

## Layer Responsibilities

| Layer | Owns | Must not |
|---|---|---|
| Domain | Entities, invariants, business rules | Know databases, frameworks, HTTP, queues |
| Application | Use cases, orchestration, transaction boundaries | Contain business invariants or transport details |
| Infrastructure | Databases, external APIs, queues, frameworks | Make domain depend on them |
| Interface | HTTP, CLI, gRPC, UI, event handlers | Contain business rules |

## Boundary Rules

- Place interfaces in the layer that consumes the dependency, not in the infrastructure layer.
- Convert infrastructure models to domain models at the boundary.
- Keep mapping explicit when models differ meaningfully.
- Keep transaction and unit-of-work decisions in the application layer.
- Treat repository contracts as domain/application needs, not ORM artifacts.

## Simplification Rule

For CRUD-only behavior, a controller and repository can be enough. Do not add use cases, domain services, ports, adapters, factories, and mappers when no business rule or test boundary justifies them.

Introduce layers only when:

- Business rules become hard to test through the current boundary.
- Infrastructure choices change independently.
- Multiple delivery mechanisms trigger the same behavior.
- Transport concerns repeatedly contaminate business logic.

## Review Signals

| Symptom | Likely problem | Action |
|---|---|---|
| Entity imports ORM | Dependency violation | Introduce a boundary/mapping |
| Use case contains SQL | Layer leakage | Move persistence behind a boundary |
| Domain validates HTTP status | Boundary leakage | Return a domain result/error |
| Small feature has five layers | Overengineering | Collapse to simpler structure |
| Shared utility imports both layers | Circular risk | Move shared concept or split module |
