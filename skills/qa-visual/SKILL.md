---
name: qa-visual
description: Compare a rendered web page against a wireframe, screenshot, Figma export, or visual reference, then fix clear visual mismatches while respecting the active repo's design system and operating mode. Use for `*qa-visual` command triggers, visual QA, wireframe-to-browser comparison, screenshot comparison, responsive visual polish, layout/spacing/typography mismatch fixes, and post-implementation page polish in starter or client repos.
---

# QA Visual

## Purpose

Use this skill when a rendered page needs visual QA against a reference.

The goal is to make the page visually match the approved reference without breaking repo boundaries, design-system rules, or validation discipline.

## Required Context

Before editing files, identify:

- target repo
- operating mode
- allowed write scope
- reference source
- rendered URL or page route
- validation required
- promotion impact

If any context is missing, infer conservatively from the active repo and task. Ask only when the target repo or reference cannot be determined safely.

## Inputs

Use the most authoritative available reference:

1. Figma node or design file
2. approved wireframe or screenshot
3. current browser screenshot plus user notes
4. written design notes

Use a real browser check for rendered output whenever a dev server or URL is available.

## Workflow

1. Confirm the repo mode and boundaries.
2. Inspect the reference and rendered page.
3. Compare section by section from top to bottom.
4. List concrete mismatches before editing.
5. Fix clear issues in the narrowest correct layer.
6. Browser-check desktop and mobile.
7. Run the repo's validation command.
8. Report fixes, remaining visual gaps, validation, and open decisions.

## Comparison Checklist

Check:

- section order and presence
- page width, gutters, and container alignment
- typography family, weight, scale, line height, and wrapping
- spacing between sections and inside panels
- grid/column proportions
- card size, radius, padding, and alignment
- button size, text visibility, states, and placement
- imagery, icons, logos, and placeholder behavior
- dark/light surface boundaries
- responsive behavior and horizontal overflow
- browser console or runtime errors

## Editing Rules

Edit the narrowest correct layer:

| Need                             | Edit Location                                |
| -------------------------------- | -------------------------------------------- |
| Copy or structured content       | `data/` or client-safe content source        |
| Page order/composition           | `app/` page file                             |
| Section layout or visual polish  | `components/sections/`                       |
| Shared primitive behavior        | `components/ui/`                             |
| Repeated section variant styling | `*.variants.ts` in the section folder        |
| System-wide tokens               | `styles/tokens.css` or equivalent token file |
| Global reset/foundations only    | `app/globals.css`                            |

Do not use global CSS for section-specific fixes.
Do not introduce client-specific content into starter work.
Do not turn a one-off client design into starter or registry behavior without review.

## Fix Policy

Fix by default when:

- the mismatch is visible and unambiguous
- the change stays inside the allowed write scope
- the fix strengthens an existing section, primitive, variant, or token
- validation can be run in the current turn

Pause or report instead when:

- the reference conflicts with design-system rules
- the fix requires real client assets that are not approved
- the change would promote client-specific design into starter/registry
- the target repo or write scope is unclear

## Validation

Use the repo's standard validation. For PAW starter and most client repos, default to:

```txt
pnpm check
```

Also browser-check:

- desktop viewport
- mobile viewport
- no horizontal overflow
- no console/page errors
- important text remains visible and readable

## Output

Report:

- target repo and mode
- reference used
- visual mismatches found
- files changed
- validation performed
- remaining visual gaps
- open decisions
- promotion candidates, if any
