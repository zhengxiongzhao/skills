---
name: 12-factor
description: Use when building or reviewing cloud-native services, configuring environments, managing dependencies, process lifecycle, backing services, concurrency, logs, or deployment behavior. Applies the 12-Factor App methodology without turning every service into distributed infrastructure.
---

# 12-Factor App

## Core Principle

Make the service configurable, disposable, stateless, and reproducible across development, staging, and production.

## Quick Reference

| Factor | Decision rule |
|---|---|
| Codebase | One codebase, many deployments; no deploy-specific forks |
| Dependencies | Declare and lock dependencies explicitly |
| Config | Keep environment differences in configuration, not code |
| Backing services | Treat local and remote services through configurable endpoints |
| Build/release/run | Make build artifacts immutable and releases identified |
| Processes | Keep application processes stateless and disposable |
| Port binding | Expose services through self-contained ports when appropriate |
| Concurrency | Scale via processes/workers according to workload type |
| Disposability | Start quickly and terminate gracefully |
| Dev/prod parity | Keep environments as similar as practical |
| Logs | Write event streams to stdout/stderr |
| Admin processes | Run one-off tasks in a controlled release environment |

## Configuration Rules

- Validate required environment variables at startup.
- Fail fast with the variable name and expected meaning.
- Use structured config when values are grouped or environment-specific.
- Keep secrets out of source control, images, logs, and generated files.
- Do not read configuration lazily in unrelated places when a validated application-level config is clearer.

## Stateless Rules

- Keep persistent state in a backing service.
- Do not rely on process memory, local disk, or sticky sessions for required state.
- Design workers to tolerate restart, duplicate delivery, or interruption when applicable.

## Logs And Lifecycle

- Write logs as structured events to the standard stream.
- Do not build custom log transport into business logic.
- Handle termination signals where in-flight work would otherwise be corrupted.
- Separate normal exit, configuration error, and runtime failure.

## Anti-Overengineering

- A local CLI or library does not need process lifecycle, health checks, or container rules.
- Do not add a message broker, service mesh, container orchestrator, or distributed tracing merely because the app is cloud-native.
- Use 12-Factor for deployment and process concerns; use other skills for domain and code structure.
