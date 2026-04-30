---
name: qa-design
description: Audit and improve design-system application in a web repo by checking tokens, primitives, variants, repeated patterns, styling ownership, and system gaps, then fix clear violations. Use for `*qa-design` command triggers, design-system QA, token audits, component primitive audits, repeated styling extraction, variant/preset gap analysis, CSS architecture review, and starter or client design-system cleanup.
---

# QA Design

## Purpose

Use this skill when the question is whether a page or component was built correctly within the design system.

The goal is not pixel matching. The goal is to keep styling reusable, token-driven, maintainable, and appropriate to the active repo.

## Required Context

Before editing files, identify:

- target repo
- operating mode
- allowed write scope
- area under audit
- validation required
- promotion impact

If the task starts from a short command such as `*qa-design`, infer the current page or recent work as the audit target.

## Audit Workflow

1. Confirm repo mode and boundaries.
2. Inspect the relevant page, components, tokens, and inventories.
3. Identify styling ownership for each issue.
4. Find repeated patterns and one-off styling drift.
5. Decide whether each fix belongs in a token, primitive, section variant, section component, page composition, or data source.
6. Fix clear violations in the narrowest correct layer.
7. Update inventories/docs when reusable sections, variants, primitives, or tokens change.
8. Run lint/type/build validation when supported.
9. Report remaining design-system gaps and validation status.

## Design-System Checklist

Check:

- colors use tokens or approved theme classes
- typography uses approved font family, sizes, weights, and line heights
- spacing uses existing scale or tokenized values where practical
- pixel-derived values map to existing tokens, component props, semantic classes, or `rem` values where practical
- radii, shadows, borders, and focus states are consistent
- layout patterns are expressed through reusable sections or variants
- primitives are used for repeated UI controls
- variants are used when a section has multiple reusable modes
- one-off arbitrary values are justified and local
- repeated raw `px`, repeated arbitrary values, or repeated px-derived values are treated as design-system gaps
- global CSS is limited to foundations and reset behavior
- inventories describe new reusable section/variant behavior
- client-specific styling is not promoted into starter/registry without review

## Editing Rules

Prefer this order:

1. Reuse existing primitive, section, variant, or token.
2. Extend an existing variant when the pattern belongs to that section family.
3. Add a primitive only when the pattern repeats across sections.
4. Add or adjust a token only when the decision is system-wide.
5. Keep page-level styling minimal and composition-focused.
6. Use global CSS only for imports, resets, base behavior, and theme exposure.

For pixel-derived values, use `16px = 1rem` as the default conversion baseline unless the active handoff or repo says otherwise.
Preserve raw `px` only when exact pixel behavior is required or when CSS/browser behavior expects pixels.

Do not:

- add broad global selectors for local layout issues
- duplicate component patterns instead of extracting or extending
- add a token for a single accidental value
- rewrite unrelated design architecture during a narrow QA pass
- copy mission-control docs or private workflows into client repos

## Pattern Classification

Classify each finding before fixing:

| Finding Type                                        | Likely Fix                          |
| --------------------------------------------------- | ----------------------------------- |
| Repeated button/card/input issue                    | primitive update                    |
| One section needs a reusable alternate layout       | section variant                     |
| One page needs different section order              | page composition                    |
| Same spacing/radius/color appears across many areas | token or utility                    |
| Client-specific brand treatment                     | client repo only                    |
| Starter-safe reusable treatment                     | starter section/variant/inventory   |
| Possible future reusable template                   | mission-control promotion candidate |

## Validation

Use the repo's standard validation. For PAW starter and most client repos, default to:

```txt
pnpm check
```

When the audit touches visual behavior, also run a browser check across desktop and mobile.

If the repo exposes separate commands, run the relevant linting and type/build checks individually or through the aggregate validation script. Prefer the aggregate script when it includes lint, typecheck, and build.

For JavaScript/TypeScript repos, look for scripts such as:

- `pnpm lint`
- `pnpm typecheck`
- `pnpm build`
- `pnpm check`

Treat visible IDE lint errors as actionable signals, but verify them through the repo's CLI validation before reporting completion.

## Output

Report:

- target repo and mode
- design-system gaps found
- files changed
- docs/inventories updated
- validation performed
- lint/type/build status when supported
- remaining design-system gaps
- promotion candidates, if any
