---
name: observability
description: Use when adding or reviewing logs, metrics, traces, health checks, readiness, alerts, dashboards, correlation IDs, operational events, or diagnosing production behavior and failure modes.
---

# Observability

## Core Principle

Emit signals that answer specific operational questions. Instrumentation must not become business logic.

## Signal Choice

| Signal | Answers |
|---|---|
| Structured log | Discrete event context |
| Metric | Rate, latency, error rate, saturation, volume |
| Distributed trace | Cross-service request path and timing |
| Health/readiness | Whether traffic should be accepted |
| Alert | Condition requiring human action |

## Instrumentation Rules

- Use structured logging with stable event names.
- Include correlation/request/trace identifiers consistently.
- Define units and dimensions for metrics.
- Instrument at boundaries and externally visible operations first.
- Keep cardinality bounded; do not use unbounded user or request IDs as metric dimensions.
- Do not log secrets, tokens, credentials, or sensitive payloads.

## Health Checks

- Liveness indicates whether the process should be restarted.
- Readiness indicates whether the process can accept traffic.
- Dependency health should distinguish startup, degraded, and fatal states according to whether traffic can still be served safely.

## Alert Rules

Alert only on actionable, user-visible, or high-confidence risk. Route symptoms and page for customer impact; send lower urgency for capacity and trend warnings.

## Anti-Patterns

- Adding traces to every internal function call before measuring blind spots.
- Logging every method entry/exit.
- Turning exceptions into stack traces without operation context.
- Emitting metrics with unbounded labels.
- Adding an alert without a documented owner and response action.
