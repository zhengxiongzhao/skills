# `software-architecture`

> Parent architecture skill with ten specialized subskills.

![Type](https://img.shields.io/badge/type-parent_skill-111827)
![Focus](https://img.shields.io/badge/focus-architecture-blue)
![Method](https://img.shields.io/badge/method-boundaries--first-2ea44f)
![Anti-pattern](https://img.shields.io/badge/guardrail-overengineering-red)

## When To Use

Use this skill when a task involves:

- Application layers, modules, or package boundaries
- Dependency direction and infrastructure isolation
- Choosing between Clean Architecture, DDD, SOLID, and design patterns
- Deciding whether an abstraction, interface, or layer is justified
- Reviewing a design for overengineering or accidental complexity

## Core Principle

First define business capabilities, responsibility boundaries, and dependency direction. Only then choose patterns or abstractions.

```text
Business / Domain
        ↓
Responsibility Boundaries
        ↓
Dependency Direction
        ↓
Simplest Sufficient Design
        ↓
Pattern (only when justified)
```

## Abstraction Rule

Introduce an abstraction only when at least one condition is true:

- There is a real dependency boundary.
- Multiple implementations are required or clearly foreseeable.
- The dependency must be isolated for tests.
- The domain must remain independent from infrastructure.
- The abstraction names a meaningful business concept.

Otherwise prefer direct code, explicit functions, and small cohesive modules.

## Subskill Routing

| Concern | Subskill |
|---|---|
| Deployment, configuration, process lifecycle | [`12-factor`](./12-factor/) |
| Layering and dependency direction | [`clean-architecture`](./clean-architecture/) |
| Responsibility and coupling | [`solid`](./solid/) |
| Repeated interaction or construction problem | [`design-patterns`](./design-patterns/) |
| Bounded contexts, aggregates, domain language | [`domain-driven-design`](./domain-driven-design/) |
| Verification strategy and test boundaries | [`testing`](./testing/) |
| Public contracts and versioning | [`api-design`](./api-design/) |
| Failure modes and recovery | [`error-handling`](./error-handling/) |
| Logs, metrics, traces, and alerts | [`observability`](./observability/) |
| Diff, PR, and merge readiness review | [`engineering-code-review`](./code-review/) |

## Complexity Guardrails

- A CRUD-only feature does not need a full use-case/adapter stack.
- Do not create an interface for a single implementation unless it is replaced or isolated for testing.
- Do not split a module only to satisfy a layer diagram.
- Do not introduce dependency-injection machinery for a small standalone program.
- Do not promote a local utility to a shared library until a second consumer exists.

## Usage

Install the parent and all subskills:

```bash
cp -R software-architecture ~/.codex/skills/
```

If your runtime requires a flat skill list, copy each child directory next to `software-architecture`:

```bash
cp -R software-architecture/* ~/.codex/skills/
```

The skill is automatically discovered through its `SKILL.md` frontmatter. Start a new agent task after installation so the skill list is refreshed.
