---
name: domain-driven-design
description: Use when modeling business behavior, defining bounded contexts, aggregates, entities, value objects, domain events, invariants, or ubiquitous language, or when separating business rules from infrastructure and coordinating multiple domain models.
---

# Domain-Driven Design

## Core Principle

Model software around business behavior and language, not database tables or framework conventions.

## Strategic Design

- Identify bounded contexts by language boundaries, ownership, and change cadence.
- Define explicit context maps between models; do not force one enterprise-wide object graph.
- Keep integration contracts small and versioned.
- Avoid a shared kernel unless multiple teams genuinely need a jointly owned model.

## Tactical Model

| Concept | Use when |
|---|---|
| Entity | Identity matters and state changes over time |
| Value Object | Immutable equality-by-value describes a concept |
| Aggregate | A consistency boundary protects invariants |
| Domain Event | Something business-relevant happened |
| Domain Service | Behavior spans multiple aggregates without belonging to one |
| Application Service | Coordinates use case, transactions, and boundaries |
| Repository | An aggregate root needs persistence abstraction |
| Factory | Creation is complex or must protect invariants |

## Aggregate Rules

- Choose boundaries from consistency invariants, not object navigation convenience.
- Reference other aggregates by identity unless within the same transaction boundary.
- Do not modify two aggregates in one transaction when eventual consistency is acceptable.
- Keep one aggregate per command; propagate side effects through domain events when justified.

## Avoid Overmodeling

- CRUD tables are not automatically entities with repositories.
- A primitive string can remain a primitive until validation or behavior makes a value object useful.
- A helper function does not need a domain service.
- A process does not need domain events unless downstream behavior is actually decoupled.

## Language Discipline

Use the business term consistently in code, tests, and docs. If a term has multiple meanings, split the model. If two terms mean the same thing in one context, unify it with the business.
