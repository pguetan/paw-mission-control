# DOC-OWNERSHIP-MAP.md

## Purpose

This map defines where each kind of documentation should live.

The goal is to avoid duplicate docs, doc drift, and accidental exposure of internal IP in client repos.

## Source of Truth Map

| Doc Type                         | Source of Truth                         | Notes                                         |
| -------------------------------- | --------------------------------------- | --------------------------------------------- |
| Internal operating model         | `paw-mission-control`                   | Private agency workflow and repo coordination |
| Cross-repo agent workflow        | `paw-mission-control`                   | Controls how agents move between repos        |
| Client trackers                  | `paw-mission-control`                   | One tracker per client project                |
| System trackers                  | `paw-mission-control`                   | Tracks starter and future registry status     |
| Promotion decisions              | `paw-mission-control`                   | Records what becomes reusable and why         |
| Registry workflow                | `paw-mission-control`                   | Future registry governance                    |
| Client repo export policy        | `paw-mission-control`                   | Defines what can enter client repos           |
| Internal plans and roadmaps      | `paw-mission-control`                   | Private planning docs                         |
| Starter-origin internal planning | `paw-mission-control`                   | Private copies live in `docs/internal-planning/starter-kit/` before starter sanitization |
| Private agent skills and prompts | `paw-mission-control`                   | Do not copy to client repos                   |
| Starter file map                 | `paw-starter-kit`                       | Describes actual starter code structure       |
| Starter design system            | `paw-starter-kit`                       | Token, primitive, section, and theme rules    |
| Starter component inventory      | `paw-starter-kit`                       | Should match installed starter code           |
| Starter section inventory        | `paw-starter-kit`                       | Should match installed starter sections       |
| Starter QA checklist             | `paw-starter-kit`                       | Runtime/template validation                   |
| Starter deployment guide         | `paw-starter-kit`                       | Template deployment baseline                  |
| Client-safe editing guide        | client repo                             | Generated or copied in sanitized form         |
| Client brief                     | client repo and mission-control tracker | Client repo gets client-safe version          |
| Client content map               | client repo                             | Specific to that client site                  |
| Client deployment notes          | client repo                             | Specific to hosting/env/domain setup          |

## Copying Rules

Safe to copy into client repos:

- sanitized editing guide
- client brief
- content map
- QA checklist
- deployment notes
- component usage notes for installed components

Use `docs/CLIENT-REPO-EXPORT-POLICY.md` as the source of truth before creating or populating a client repo.

Do not copy into client repos:

- mission-control plans
- internal operating model
- promotion decisions
- registry strategy
- private prompts or skills
- internal system governance docs
- starter-origin internal planning copies
- client trackers for other clients

## Starter Cleanup Rule

Do not remove docs from `paw-starter-kit` until mission control has the internal copy where needed.

After copying internal docs to mission control, the starter may keep only:

- runtime guidance
- starter-safe system docs
- code inventories
- validation docs
- client-safe examples

## Drift Control

If the same concept appears in more than one repo, one repo must be declared the source of truth.

Other repos should contain either:

- a short summary
- a sanitized version
- a link/reference

Avoid maintaining full duplicate docs across repos.
