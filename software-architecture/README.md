# software-architecture

Architecture-first routing skill for designing, structuring, and refactoring software systems.

## Purpose

Use this skill when a task involves:

- Application layers, modules, or package boundaries
- Dependency direction and infrastructure isolation
- Choosing between Clean Architecture, DDD, SOLID, and design patterns
- Deciding whether an abstraction, interface, or layer is justified
- Reviewing a design for overengineering or accidental complexity

## Core Principle

First define business capabilities, responsibility boundaries, and dependency direction. Only then choose patterns or abstractions.

The skill deliberately does not apply every methodology to every task. It routes to the most relevant specialized skill when a concern such as testing, API design, or observability becomes relevant.

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
| Deployment, configuration, process lifecycle | `12-factor` |
| Layering and dependency direction | `clean-architecture` |
| Responsibility and coupling | `solid` |
| Repeated interaction or construction problem | `design-patterns` |
| Bounded contexts, aggregates, domain language | `domain-driven-design` |
| Verification strategy and test boundaries | `testing` |
| Public contracts and versioning | `api-design` |
| Failure modes and recovery | `error-handling` |
| Logs, metrics, traces, and alerts | `observability` |
| Diff, PR, and merge readiness review | `engineering-code-review` |

## Usage

Copy this directory into your Codex skills directory:

```bash
cp -R software-architecture ~/.codex/skills/
```

The skill is automatically discovered through its `SKILL.md` frontmatter. Start a new agent task after installation so the skill list is refreshed.
