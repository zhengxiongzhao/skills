<div align="center">

# AI Coding Agent Skills

**A focused, layered skills pack for Codex and other agent runtimes.**

[![Skills](https://img.shields.io/badge/skills-11-blue)](#skills)
[![Format](https://img.shields.io/badge/Agent_Skill-SKILL.md-2ea44f)](https://agentskills.io/)
[![Architecture](https://img.shields.io/badge/architecture-first-111827)](#design-principles)
[![Overengineering](https://img.shields.io/badge/anti--overengineering-enabled-red)](#design-principles)

[Overview](#overview) · [Skills](#skills) · [Quick Start](#quick-start) · [Design Principles](#design-principles)

</div>

---

## Overview

This repository contains standalone **Agent Skills** that help AI coding agents make better engineering decisions.

Each skill is a focused `SKILL.md` with explicit triggers, decision rules, and anti-patterns. `software-architecture` acts as the routing entry point; the other skills are loaded only when their concerns apply.

```text
                         ┌──────────────────────────────┐
                         │      software-architecture   │
                         │  routing + trade-off rules   │
                         └──────────────┬───────────────┘
                                        │
        ┌──────────────┬────────────────┼────────────────┬──────────────┐
        │              │                │                │              │
   Architecture      Domain        Quality Attributes   Operations     Review
        │              │                │                │              │
   12-factor      domain-driven      api-design      observability  engineering-
   clean-arch       design           error-handling                 code-review
   solid            design-patterns  testing
```

> **Core rule:** introduce an abstraction only for a real dependency boundary, a second implementation, test isolation, domain independence, or a meaningful business concept.

---

## Skills

| Skill | Focus | Triggered By |
|---|---|---|
| [`software-architecture`](./software-architecture/) | Architecture-first routing and complexity control | System design, dependency boundaries, architecture trade-offs |
| [`12-factor`](./12-factor/) | Cloud-native process and configuration | Deployment, configuration, stateless processes, backing services |
| [`clean-architecture`](./clean-architecture/) | Layering and dependency direction | Module boundaries, ports/adapters, infrastructure leakage |
| [`solid`](./solid/) | Responsibility and coupling design | Class/module design, interfaces, dependency direction |
| [`design-patterns`](./design-patterns/) | Pattern selection discipline | Repeated construction/interaction problems, pattern choice |
| [`domain-driven-design`](./domain-driven-design/) | Business modeling | Bounded contexts, aggregates, invariants, ubiquitous language |
| [`testing`](./testing/) | Verification strategy | Test scope, doubles, boundaries, brittleness |
| [`api-design`](./api-design/) | Contract design | HTTP/REST/gRPC/GraphQL contracts, versioning, idempotency |
| [`error-handling`](./error-handling/) | Failure behavior | Exceptions, result types, retries, degradation |
| [`observability`](./observability/) | Operational visibility | Logs, metrics, traces, health checks, alerts |
| [`engineering-code-review`](./code-review/) | Review discipline | Diff/PR review, severity, merge readiness |

### Theme Groups

```text
Architecture     software-architecture · 12-factor · clean-architecture · solid · design-patterns
Modeling         domain-driven-design
Quality          testing · api-design · error-handling
Operations       observability
Process          engineering-code-review
```

---

## Quick Start

Install all skills:

```bash
git clone git@github.com:zhengxiongzhao/skills.git
mkdir -p ~/.codex/skills
cp -R skills/* ~/.codex/skills/
```

Install selected skills:

```bash
cp -R skills/software-architecture skills/testing ~/.codex/skills/
```

Start a new Codex task after installation so the skill list is refreshed.

<details>
<summary><strong>Directory format</strong></summary>

```text
skills/
├── 12-factor/SKILL.md
├── api-design/SKILL.md
├── clean-architecture/SKILL.md
├── code-review/SKILL.md
├── design-patterns/SKILL.md
├── domain-driven-design/SKILL.md
├── error-handling/SKILL.md
├── observability/SKILL.md
├── software-architecture/{SKILL.md,README.md}
├── solid/SKILL.md
└── testing/SKILL.md
```

</details>

<details>
<summary><strong>Using with other agent runtimes</strong></summary>

Each skill is a portable directory containing a standard `SKILL.md`. Copy the directories into the skills or instructions location your runtime scans, then start a new agent session.

</details>

---

## Design Principles

### 1. Business before architecture

Define business capabilities, invariants, and responsibility boundaries before choosing patterns.

### 2. Boundaries before abstraction

Create an abstraction only when it isolates a real dependency, enables a second implementation, supports testing, preserves domain independence, or names a meaningful business concept.

### 3. Simplest sufficient design

A CRUD feature does not require use cases, domain services, ports, adapters, repositories, and ORM layers.

### 4. Load only what is relevant

- API contract work does not require DDD aggregate rules.
- DDD modeling does not require HTTP status-code rules.
- Testing strategy does not require observability alerting rules.
- Code review does not require a full architectural redesign.

### 5. Evidence before architecture

Before proposing an architectural change, state:

1. The problem being solved.
2. The simplest alternative.
3. Why the proposed design is worth its cost.

---

<div align="center">

**11 focused skills · 0 forced frameworks · 1 architecture-first entry point**

</div>
