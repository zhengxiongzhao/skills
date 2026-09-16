<div align="center">

# Software Architecture Skills Pack

**A layered Agent Skill pack for architecture-first AI coding agents.**

[![Skills](https://img.shields.io/badge/subskills-10-blue)](./software-architecture/#skills)
[![Entry Point](https://img.shields.io/badge/entry_point-software--architecture-111827)](./software-architecture/)
[![Format](https://img.shields.io/badge/Agent_Skill-SKILL.md-2ea44f)](https://agentskills.io/)
[![Anti-overengineering](https://img.shields.io/badge/anti--overengineering-enabled-red)](#design-principles)

[Overview](#overview) · [Structure](#structure) · [Quick Start](#quick-start) · [Design Principles](#design-principles)

</div>

---

## Overview

`software-architecture` is the parent skill. It owns the routing model, dependency-direction rules, and anti-overengineering guardrails. The ten specialized skills below it are loaded only when their concerns apply.

```text
software-architecture/
├── SKILL.md                 # parent skill and routing entry point
├── README.md                # usage and routing guide
├── 12-factor/
├── api-design/
├── clean-architecture/
├── code-review/
├── design-patterns/
├── domain-driven-design/
├── error-handling/
├── observability/
├── solid/
└── testing/
```

> **Core rule:** introduce an abstraction only for a real dependency boundary, a second implementation, test isolation, domain independence, or a meaningful business concept.

---

## Structure

```text
                         ┌───────────────────────────────────┐
                         │       software-architecture       │
                         │  parent skill + routing rules     │
                         └──────────────────┬────────────────┘
                                            │
        ┌──────────────┬────────────────────┼────────────────────┬──────────────┐
        │              │                    │                    │              │
   Architecture      Domain           Quality Attributes     Operations      Review
        │              │                    │                    │              │
   12-factor      domain-driven        api-design          observability  engineering-
   clean-arch       design             error-handling                    code-review
   solid            design-patterns    testing
```

### Subskills

| Subskill | Focus | Triggered By |
|---|---|---|
| [`12-factor`](./software-architecture/12-factor/) | Cloud-native process and configuration | Deployment, configuration, stateless processes, backing services |
| [`clean-architecture`](./software-architecture/clean-architecture/) | Layering and dependency direction | Module boundaries, ports/adapters, infrastructure leakage |
| [`solid`](./software-architecture/solid/) | Responsibility and coupling design | Class/module design, interfaces, dependency direction |
| [`design-patterns`](./software-architecture/design-patterns/) | Pattern selection discipline | Repeated construction/interaction problems, pattern choice |
| [`domain-driven-design`](./software-architecture/domain-driven-design/) | Business modeling | Bounded contexts, aggregates, invariants, ubiquitous language |
| [`testing`](./software-architecture/testing/) | Verification strategy | Test scope, doubles, boundaries, brittleness |
| [`api-design`](./software-architecture/api-design/) | Contract design | HTTP/REST/gRPC/GraphQL contracts, versioning, idempotency |
| [`error-handling`](./software-architecture/error-handling/) | Failure behavior | Exceptions, result types, retries, degradation |
| [`observability`](./software-architecture/observability/) | Operational visibility | Logs, metrics, traces, health checks, alerts |
| [`engineering-code-review`](./software-architecture/code-review/) | Review discipline | Diff/PR review, severity, merge readiness |

---

## Quick Start

Install the complete pack:

```bash
git clone git@github.com:zhengxiongzhao/skills.git
mkdir -p ~/.codex/skills
cp -R skills/software-architecture ~/.codex/skills/
```

Install only the parent skill without its subskills:

```bash
cp -R skills/software-architecture/SKILL.md ~/.codex/skills/software-architecture/
```

Start a new Codex task after installation so the skill list is refreshed.

<details>
<summary><strong>Using with other agent runtimes</strong></summary>

Each skill is a portable directory containing a standard `SKILL.md`. If your runtime requires a flat list, copy each child directory next to `software-architecture`:

```bash
cp -R skills/software-architecture/* ~/.codex/skills/
```

</details>

---

## Design Principles

1. **Business before architecture** — define capabilities, invariants, and responsibility boundaries before choosing patterns.
2. **Boundaries before abstraction** — create an abstraction only when it isolates a real dependency, enables a second implementation, supports testing, preserves domain independence, or names a business concept.
3. **Simplest sufficient design** — a CRUD feature does not require a full use-case/adapter stack.
4. **Load only relevant subskills** — API work does not need DDD aggregate rules; testing work does not need observability alerting rules.
5. **Evidence before architecture** — state the problem, simplest alternative, and why the proposed design is worth its cost.

---

<div align="center">

**1 parent skill · 10 focused subskills · 0 forced frameworks**

</div>
