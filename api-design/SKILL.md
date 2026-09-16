---
name: api-design
description: Use when creating or reviewing HTTP, REST, GraphQL, gRPC, SDK, or public/internal API contracts, resources, validation, status codes, versioning, pagination, idempotency, backwards compatibility, or schema evolution.
---

# API Design

## Core Principle

Design contracts around consumers and explicit evolution, not internal implementation convenience.

## Contract Rules

- Define request, response, and error schemas explicitly.
- Make required fields, formats, limits, and defaults discoverable.
- Use versioned contracts for externally consumed interfaces.
- Additive changes can be backwards-compatible; removal, rename, type change, semantic change, or new required input require a version or migration.
- Keep internal implementation exceptions out of public error responses.

## HTTP Mapping

| Situation | Preferred response |
|---|---|
| Created resource | `201 Created` + location/identifier |
| Accepted asynchronous operation | `202 Accepted` + status link |
| Validation failure | `400 Bad Request` + field details |
| Authentication failure | `401 Unauthorized` |
| Authorization failure | `403 Forbidden` |
| Missing resource | `404 Not Found` |
| Conflict with current state | `409 Conflict` |
| Preconditions failed | `412 Precondition Failed` / ETag handling |
| Rate limit | `429 Too Many Requests` + retry guidance |

Use noun resources and verbs appropriate to the protocol; do not encode verbs in resource paths.

## Mutation Safety

Make create, update, and processing operations idempotent when retries are possible:

- Use stable client-generated request identifiers where appropriate.
- Support conditional updates with `ETag`/`If-Match` when concurrent modification matters.
Document retry behavior and duplicate handling.

## Validation Rules

Validate at the boundary before business processing.
- Reject unknown or invalid fields deliberately.
- Return field-level, machine-readable errors.
- Normalize inputs only after validation.
- Translate validation failures into protocol-appropriate responses; do not leak internal exceptions.

## Evolution Checklist

- Review every public schema change for consumer impact.
- Keep deprecation, migration, and removal timelines explicit.
- Avoid breaking pagination ordering and filtering semantics.
- Add contract tests when another team or service consumes the interface.
