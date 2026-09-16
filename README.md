# Codex Skills

Personal skills for AI coding agents, organized as standalone directories that follow the Agent Skill format.

```text
skills/
├── 12-factor/
├── api-design/
├── clean-architecture/
├── code-review/
├── design-patterns/
├── domain-driven-design/
├── error-handling/
├── observability/
├── software-architecture/
├── solid/
└── testing/
```

Each directory contains a standalone `SKILL.md`. `software-architecture` is the routing and anti-overengineering entry point; load the remaining skills only when their descriptions match the task.

## Skills

| Skill | Purpose |
|---|---|
| `software-architecture` | Architecture-first routing and anti-overengineering rules |
| `12-factor` | Cloud-native configuration, processes, backing services, deployment behavior |
| `clean-architecture` | Layering, dependency direction, ports/adapters, repository boundaries |
| `solid` | Class/module responsibility, coupling, substitutability, dependency direction |
| `design-patterns` | Pattern selection and avoid-pattern overuse |
| `domain-driven-design` | Bounded contexts, aggregates, domain events, ubiquitous language |
| `testing` | Unit/integration/contract/e2e strategy and test boundaries |
| `api-design` | HTTP/REST/GraphQL/gRPC contracts, versioning, idempotency, validation |
| `error-handling` | Failure classification, exceptions, result types, retries, degradation |
| `observability` | Logs, metrics, traces, health checks, alerts, correlation IDs |
| `engineering-code-review` | Diff/PR review, severity classification, verification, merge readiness |

## `software-architecture`

Architecture-first skill for designing, structuring, or refactoring software systems. It establishes a decision order based on business capabilities, responsibility boundaries, and dependency direction before selecting patterns or abstractions.

It routes to the other skills when their concerns apply, instead of applying every methodology to every task.

Core rule: introduce an abstraction only for a real dependency boundary, a second implementation, test isolation, domain independence, or a meaningful business concept.

## Why Separate Skills?

Each concern has distinct triggers:

- API contract changes do not require loading DDD modeling rules.
- DDD aggregate design does not require HTTP status-code rules.
- Testing strategy does not require observability alerting rules.
- Code review does not require full architectural redesign.

## Installation

Clone this repository and copy the skills you want into your Codex skills directory:

```bash
git clone git@github.com:zhengxiongzhao/skills.git
mkdir -p ~/.codex/skills
cp -R skills/* ~/.codex/skills/
```

To install only selected skills, copy their directories individually:

```bash
cp -R skills/software-architecture skills/testing ~/.codex/skills/
```

For tools that use a different skills or instructions directory, copy the same directories into the location they scan.

After installation, start a new Codex task so the skill list is refreshed.
