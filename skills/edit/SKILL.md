---
name: edit
description: Execute a concrete code, content, layout, CSS, or design edit request in the correct repo while preserving operating mode, allowed write scope, validation, and design-system rules. Use for `*edit` command triggers and implicitly when the user asks to make, change, tweak, adjust, polish, fix, update, implement, resize, restyle, or otherwise edit UI/design behavior in starter or client repos.
---

# Edit

## Purpose

Use this skill when the user asks for a concrete edit.

The goal is to implement the requested change in the correct layer, then run a design-system self-check before reporting completion.

## Required Context

Before editing files, identify:

- target repo
- operating mode
- allowed write scope
- requested change
- validation required
- promotion impact

If the request starts with `*edit`, treat the rest of the message as the requested change.

If the target repo is unclear, infer from recent context when safe. Ask before editing if multiple repos are plausible.

## Request Classification

Classify the edit before changing files:

| Request Type                                     | Primary Edit Location                  |
| ------------------------------------------------ | -------------------------------------- |
| Copy, labels, links, or structured content       | `data/` or content source              |
| Page order or section composition                | `app/` page file                       |
| Section layout, spacing, or local visual polish  | `components/sections/`                 |
| Shared button/card/text/container behavior       | `components/ui/`                       |
| Reusable section mode                            | section `*.variants.ts` or preset file |
| System-wide color, spacing, font, radius, shadow | token file such as `styles/tokens.css` |
| Reset, imports, base document behavior           | global CSS or root layout only         |
| Static image, icon, or public asset              | `public/` in the implementation repo   |

Use the narrowest correct layer.

## Pixel Specs And Unit Conversion

When an edit request provides pixel values, accept them as input specs.

For PAW starter and client UI work, convert pixel values to existing tokens, component props, or `rem` values using this default baseline unless the request says otherwise:

```txt
16px = 1rem
px / 16 = rem
```

Use this order:

1. Use an existing component prop, variant, semantic class, or token.
2. Add or propose a reusable token if the value repeats or becomes part of the system.
3. Use a local `rem` value for one-off art direction.
4. Keep raw `px` only when exact pixel behavior is required or when CSS/browser behavior expects pixels.

## Workflow

1. Confirm target repo, mode, scope, validation, and promotion impact.
2. Read the relevant files before editing.
3. Classify the requested edit.
4. Implement the smallest coherent change.
5. Run a post-edit design-system self-check.
6. Run validation.
7. Browser-check desktop/mobile if UI behavior changed.
8. Report files changed, validation, remaining concerns, and promotion candidates.

## Post-Edit Design-System Self-Check

After implementation, check:

- Did this use existing tokens, primitives, sections, and variants first?
- Did pixel specs get converted to existing tokens, props, semantic classes, or `rem` values where practical?
- Did this avoid section-specific fixes in global CSS?
- Did this introduce repeated styling that should become a primitive or variant?
- Did this change starter behavior in a brand-neutral and reusable way?
- Did this keep client-specific design inside the client repo?
- Did this require an inventory or docs update?
- Did this create a promotion candidate?

If the answer reveals a clear design-system violation, fix it before final validation.

## Repo-Specific Rules

Mission Control Mode:

- edit docs, trackers, command definitions, and private skills only
- do not add deployable website code

Starter Governance Mode:

- keep reusable behavior brand-neutral
- prefer system primitives, tokens, and variants
- update inventories when reusable behavior changes
- run `pnpm check`

Client Delivery Mode:

- stay inside the client repo
- use approved client inputs and assets only
- keep docs client-safe
- log reusable discoveries as promotion candidates instead of promoting directly

Registry Governance Mode:

- only work on proven reusable patterns approved for registry consideration
- include metadata and install paths
- avoid client-specific assumptions

## Validation

Use the repo's standard validation. For PAW starter and most client repos, default to:

```txt
pnpm check
```

For docs-only mission-control edits, format Markdown/YAML where applicable and verify git status before and after.

For UI edits, also browser-check:

- desktop viewport
- mobile viewport
- no horizontal overflow
- no console/page errors

## Output

Report:

- target repo and mode
- request classification
- files changed
- validation performed
- post-edit design-system self-check result
- open decisions
- promotion candidates, if any
