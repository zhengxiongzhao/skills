# AI Coding Agent Skills

**A focused, layered skills pack for Codex and other agent runtimes.**

[![Skills](https://img.shields.io/badge/skills-11-blue)](#software-architecture)
[![Subskills](https://img.shields.io/badge/subskills-10-blue)](#subskills)
[![Format](https://img.shields.io/badge/Agent_Skill-SKILL.md-2ea44f)](https://agentskills.io/)
[![Anti-overengineering](https://img.shields.io/badge/anti--overengineering-enabled-red)](#design-principles)

[Overview](#overview) · [software-architecture](#software-architecture) · [Quick Start](#quick-start) · [Design Principles](#design-principles)

---

## Overview

This repository contains standalone **Agent Skills** that help AI coding agents make better engineering decisions.

Each skill is a focused `SKILL.md` with explicit triggers, decision rules, and anti-patterns. `software-architecture` is the parent skill; the ten specialized skills under it are loaded only when their concerns apply.

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

> **Core rule:** introduce an abstraction only for a real dependency boundary, a second implementation, test isolation, domain independence, or a meaningful business concept.

---

## software-architecture

[`software-architecture`](./software-architecture/) is the parent skill and the entry point for architecture decisions. It defines:

- Business capabilities and domain invariants first
- Responsibility boundaries and dependency direction second
- The simplest sufficient design before any pattern
- Routing to specialized subskills only when their concerns apply
- Explicit guardrails against speculative abstraction

### Structure

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

#### Theme Groups

```text
Architecture     12-factor · clean-architecture · solid · design-patterns
Modeling         domain-driven-design
Quality          testing · api-design · error-handling
Operations       observability
Process          engineering-code-review
```

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
mkdir -p ~/.codex/skills/software-architecture
cp skills/software-architecture/SKILL.md ~/.codex/skills/software-architecture/
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
