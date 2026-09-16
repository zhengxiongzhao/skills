---
name: solid
description: Use when designing classes, modules, functions, or interfaces, or when reviewing responsibility, coupling, duplication, substitutability, interface segregation, dependency direction, or refactoring toward SOLID principles.
---

# SOLID

## Core Principle

Each unit should have one reason to change and depend only on abstractions that match its actual responsibility.

## Quick Reference

| Principle | Use when | Do not |
|---|---|---|
| Single Responsibility | A class/module changes for multiple reasons | Split by technical layer mechanically |
| Open/Closed | Stable extension point has repeated divergent changes | Add speculative hooks |
| Liskov Substitution | Subtypes replace a base without behavior surprises | Use inheritance to reuse code |
| Interface Segregation | Consumers depend on unused methods | Fragment interfaces by method count |
| Dependency Inversion | High-level policy must not depend on infrastructure detail | Abstract every concrete dependency |

## Responsibility Rule

Ask what changes together. Put code that changes together and serves one actor in the same module. Split only when separate actors or change axes create real conflict.

## Abstraction Rule

Create an abstraction only for a real dependency boundary, second implementation, test isolation need, meaningful business concept, or independently changing implementation. A single concrete implementation does not require an interface by itself.

## Substitution Rule

If a subtype throws for operations declared by its parent, narrows input, widens output, or changes documented side effects, the abstraction is wrong. Prefer composition.

## Refactoring Heuristic

1. Name the unit's single responsibility.
2. Name its actual dependencies.
3. Remove dependencies it does not use.
4. Push infrastructure details behind the narrowest boundary.
5. Add tests that document the behavior and boundary.

Do not refactor solely to satisfy a principle when the current design is understandable and tests reveal no change conflict.
