---
name: design-patterns
description: Use when selecting or reviewing classic design patterns, removing duplicate control-flow or construction logic, resolving circular dependencies, or checking whether a proposed pattern is necessary and maintainable.
---

# Design Patterns

## Core Principle

Patterns solve named problems. Select the pattern only after the problem is identified.

## Pattern Selection

| Problem | Candidate patterns |
|---|---|
| Alternate construction steps or lifecycle | Builder, Factory Method, Abstract Factory |
| One shared state or resource with controlled access | Singleton; prefer explicit dependency injection |
| Object adapts to an expected interface | Adapter |
| Dynamic responsibilities added at runtime | Decorator |
| One-to-many state change notification | Observer / Pub-Sub |
| State-dependent behavior transitions | State |
| Encapsulate a request/operation | Command |
| Multiple traversal representations | Iterator / Visitor |
| Redefine steps of an invariant algorithm | Template Method / Strategy |

## Before Adding A Pattern

Answer all questions:

1. What recurring problem exists now?
2. Why does simpler direct code fail?
3. What extension or variation does the pattern enable?
4. What extra indirection and failure modes does it add?

If any answer is speculative, do not add the pattern.

## Anti-Patterns

- Adding a facade for every module with only one public function.
- Adding a repository for every table when only direct persistence is needed.
- Using dependency injection everywhere without a test or replacement need.
- Using strategy objects for branching that remains simple and local.
- Using singletons to hide global state instead of passing dependencies explicitly.
- Introducing event buses when direct calls are clearer.

## Naming

Do not require pattern names in domain code. Use ubiquitous business language where possible. Reserve pattern naming for infrastructure or framework code where the convention aids recognition.
