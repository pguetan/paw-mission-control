# OPERATING-MODEL.md

## Purpose

This document defines how mission control coordinates starter, registry, and client work.

## Operating Modes

### Starter Governance Mode

Use for changes to `paw-starter-kit`.

The starter is an internal product foundation, not a client site.

Requires:

- reusable purpose
- no client-specific copy or assets
- docs updated
- inventories updated when patterns change
- `pnpm check` before completion
- promotion impact noted

### Client Delivery Mode

Use for real client website repos.

Requires:

- approved client brief
- approved copy/assets or explicit placeholder policy
- client-safe docs only
- scoped implementation
- no internal mission-control docs copied into client repos
- reusable discoveries logged as promotion candidates

### Registry Governance Mode

Future mode for `paw-template-registry`.

Requires:

- proven reusable pattern
- promotion checklist completed
- registry metadata
- install target paths
- usage docs
- starter compatibility notes

## Task Header

Every task should begin with:

```txt
Target repo:
Mode:
Allowed write scope:
Validation:
Promotion impact:
```

## Promotion Loop

```txt
Starter defines the system.
Client projects reveal real needs.
Reusable discoveries are tracked in mission control.
Proven patterns are promoted to registry later.
```
