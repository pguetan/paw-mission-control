# REGISTRY-WORKFLOW.md

## Purpose

Define the future workflow for `paw-template-registry`.

The registry should not exist until reusable patterns are proven and manual reuse becomes repetitive.

## Registry Role

The future registry will store source-copy patterns:

- components
- sections
- page templates
- variants
- presets
- example data
- install metadata

## Promotion Source

Patterns may come from:

- starter-system work
- repeated client implementation needs
- simulated client builds

Track possible promotions in `docs/REGISTRY-CANDIDATES.md`.

## Registry Rule

The registry is a curated shelf, not the workshop.

New patterns should be built in context first, then generalized and promoted.

Every candidate needs a reuse reason, source context, evidence, cleanup notes, and a proposed target before approval.

## Before Creating Registry

Wait until:

- 8-12 sections are stable
- 2-3 page templates are stable
- at least one client-style build validates the system
- manual copying becomes repetitive enough to justify the registry

## Candidate Review Flow

1. Log the discovery in the relevant client or system tracker.
2. Add or update the entry in `docs/REGISTRY-CANDIDATES.md`.
3. Check the entry against `docs/PROMOTION-CHECKLIST.md`.
4. Decide whether the target is `paw-starter-kit`, the future registry, or no promotion.
5. Promote only through a separate approved task in the target repo.
