# AGENT-WORKFLOW.md

## Purpose

Define how coding agents should operate across mission control, starter, registry, and client repos.

## Default Rule

Mission control coordinates work. It is not automatically the write target.

Every task must declare the write target repo.
Use the root `AGENTS.md` as the mandatory operating contract for agents in this repo.

## Command Triggers

Short chat commands are defined in `docs/AGENT-COMMANDS.md`.

Current command triggers:

- `*edit` loads `skills/edit/` for scoped code, content, layout, CSS, or design edits.
- `*qa-visual` loads `skills/qa-visual/` for visual reference comparison and fixes.
- `*qa-design` loads `skills/qa-design/` for design-system audits and fixes.

Commands speed up workflow selection, but they do not change repo boundaries, allowed write scope, validation, or promotion rules.

Use the edit workflow implicitly for concrete change requests such as make, change, tweak, adjust, polish, fix, update, implement, resize, or restyle.

## Starter Work Prompt Pattern

```txt
Target repo: paw-starter-kit
Mode: Starter Governance
Allowed write scope:
Validation: pnpm check
Promotion impact:
```

## Client Work Prompt Pattern

```txt
Target repo: client-name-website
Mode: Client Delivery
Allowed write scope:
Validation: pnpm check
Promotion impact: log only unless approved
```

## Registry Work Prompt Pattern

```txt
Target repo: paw-template-registry
Mode: Registry Governance
Allowed write scope:
Validation:
Promotion checklist:
```

## Cross-Repo Safety

- Do not edit mission control when asked to implement a client page.
- Do not edit starter from a client task unless explicitly approved.
- Do not copy mission-control docs into client repos.
- Log reusable discoveries as promotion candidates.
