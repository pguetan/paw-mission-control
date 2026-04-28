# AGENTS.md

## Purpose

This repo is PAW Mission Control.

It is the private internal coordination repo for managing:

- `paw-starter-kit`
- future `paw-template-registry`
- client website repos
- internal workflows, plans, trackers, and promotion decisions

It is not a deployable website and must not be copied into client repos.

## Default Agent Role

Default to planning, governance, tracking, and documentation work.

Do not assume this repo is the implementation target.

Before changing files, identify:

- target repo
- operating mode
- allowed write scope
- validation required
- promotion impact

## Operating Modes

### Mission Control Mode

Use when editing this repo.

Allowed:

- update operating docs
- update client trackers
- update system trackers
- update promotion decisions
- update internal skill plans
- update decision records

Do not:

- add client secrets
- add private client assets
- add deployable website code
- copy this repo into a client project

### Starter Governance Mode

Use when coordinating or making approved changes to `paw-starter-kit`.

Starter changes must:

- improve the reusable system
- remain brand-neutral
- avoid client-specific content
- update docs and inventories when relevant
- pass `pnpm check`

### Client Delivery Mode

Use when coordinating or making approved changes to a client repo.

Client work must:

- use approved client inputs
- stay inside the client repo
- include only client-safe docs
- log reusable discoveries as promotion candidates

### Registry Governance Mode

Future mode for `paw-template-registry`.

Registry work must:

- use proven reusable patterns
- include metadata and install paths
- pass promotion review
- avoid client-specific assumptions

## Read First

1. `README.md`
2. `docs/OPERATING-MODEL.md`
3. `docs/AGENT-WORKFLOW.md`
4. `docs/DOC-OWNERSHIP-MAP.md`
5. `docs/PROJECT-TRACKER.md`

For starter work, also read:

- `docs/STARTER-KIT-GOVERNANCE.md`
- `systems/paw-starter-kit.md`

For client work, also read:

- `docs/CLIENT-PROJECT-WORKFLOW.md`
- the relevant `clients/<client>.md`

For registry decisions, also read:

- `docs/REGISTRY-WORKFLOW.md`
- `docs/PROMOTION-CHECKLIST.md`

## Cross-Repo Safety Rules

- Do not edit another repo unless the task explicitly names it as the target.
- Do not copy mission-control docs into client repos.
- Do not commit secrets, private client assets, or credential material.
- Do not promote client-specific work into starter or registry without review.
- Keep client implementation in client repos.
- Keep reusable system work in starter or registry.
- Keep internal strategy and coordination here.

## Reporting

When done, report:

- target repo
- files changed
- mode used
- validation performed
- open decisions
- promotion candidates, if any

