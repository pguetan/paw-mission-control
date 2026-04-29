# REGISTRY-CANDIDATES.md

## Purpose

Track reusable patterns before they are promoted into the future `paw-template-registry`.

This list is a holding area for evidence, review, and decisions. A candidate here is not approved for promotion until it passes `docs/PROMOTION-CHECKLIST.md`.

## Status Values

Use these statuses:

- `Observed`: a reusable need or pattern was noticed.
- `Candidate`: enough evidence exists to review the pattern.
- `Needs Generalization`: the pattern works but still contains client-specific assumptions.
- `Approved for Starter`: promote into `paw-starter-kit`.
- `Approved for Registry`: promote into the future `paw-template-registry`.
- `Rejected`: do not promote.
- `Deferred`: keep for later review.

## Candidate Fields

Each candidate should include:

- pattern name
- category
- source repo
- source context
- reuse reason
- evidence
- current status
- risks or cleanup needed
- proposed target
- approval state
- owner
- next action

## Candidate List

### None Yet

Status: `Observed`

Source repo:
Source context:
Category:
Reuse reason:
Evidence:
Risks or cleanup needed:
Proposed target:
Approval state:
Owner:
Next action:

No reusable registry candidates have been approved or reviewed yet.

## Candidate Template

Copy this template when a new candidate appears:

```md
### Pattern Name

Status: `Observed`

Source repo:
Source context:
Category:
Reuse reason:
Evidence:
Risks or cleanup needed:
Proposed target:
Approval state:
Owner:
Next action:

Promotion checklist:

- [ ] Solves a repeatable use case.
- [ ] Not tied to one client.
- [ ] Uses starter tokens and primitives.
- [ ] Has typed props or schema.
- [ ] Has example data.
- [ ] Has usage documentation.
- [ ] Declares dependencies.
- [ ] Has a clear use-case name.
- [ ] Checked on mobile, tablet, and desktop.
- [ ] Passes relevant validation.
```

## Review Rule

Promotion requires a separate implementation task in the target repo.

Do not copy client-specific work into starter or registry directly from this list. Generalize first, then validate in the correct operating mode.
