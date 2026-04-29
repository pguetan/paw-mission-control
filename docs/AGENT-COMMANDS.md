# AGENT-COMMANDS.md

## Purpose

Define short chat commands that map to repeatable PAW agent workflows.

These commands are private mission-control workflow triggers. They are not client-facing docs and should not be copied into client repos.

## Command Rules

- Commands are typed at the start of a chat request.
- Commands load the matching repo-local skill.
- Commands do not override repo boundaries, operating mode, allowed write scope, validation, or promotion rules.
- If the target repo is unclear, infer from the active task context or ask before editing.
- If a command includes extra instructions, the extra instructions narrow or extend the command workflow.

## Commands

| Command      | Skill                          | Purpose                                                                                                                                    |
| ------------ | ------------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------ |
| `*wireframe` | `skills/wireframe-conversion/` | Inspect and convert wireframes into mission-control planning artifacts and implementation plans.                                           |
| `*edit`      | `skills/edit/`                 | Execute a concrete code, content, layout, CSS, or design edit request, then run a post-edit design-system self-check.                      |
| `*qa-visual` | `skills/qa-visual/`            | Compare a rendered page against a wireframe, screenshot, Figma export, or visual reference, then fix clear visual mismatches.              |
| `*qa-design` | `skills/qa-design/`            | Audit design-system application, token usage, primitive/variant ownership, repeated patterns, and styling gaps, then fix clear violations. |

## `*wireframe`

Use when a wireframe, screenshot, Figma export, or planning asset needs to become a repo-safe PAW build plan before coding.

Default workflow:

1. Identify target repo, mode, wireframe source, validation, and promotion impact.
2. Store or reference the wireframe in the correct mission-control location.
3. Inspect the full page or flow from top to bottom.
4. Map sections to existing starter/client sections, new reusable sections, shared components, and page composition.
5. Identify data, assets, repo-boundary decisions, and validation needs.
6. Update wireframe notes and section maps.
7. Define the post-implementation QA plan using `*qa-visual` and `*qa-design`.
8. Report implementation target, build order, open questions, validation required, and QA follow-up.

Examples:

```txt
*wireframe inspect this homepage wireframe and create the starter build plan
*wireframe map this client services page into sections and data needs
*wireframe update the section map after this revised screenshot
```

## `*edit`

Use when the user wants a concrete edit made.

Default workflow:

1. Identify target repo, mode, requested change, validation, and promotion impact.
2. Classify the request as content, page composition, section layout, primitive, variant, token, global foundation, or asset work.
3. Edit the narrowest correct layer.
4. Run the post-edit design-system self-check from `skills/edit/`.
5. Run repo validation.
6. Browser-check desktop and mobile when UI behavior changed.
7. Report files changed, validation, design-system self-check result, and remaining concerns.

Examples:

```txt
*edit Make the navigation full width.
*edit Reduce the hero panel height on mobile.
*edit Update the blog preview heading copy.
```

## `*qa-visual`

Use when the rendered page needs to match a visual reference more closely.

Default workflow:

1. Identify target repo, mode, reference, rendered URL, validation, and promotion impact.
2. Inspect the reference and browser-rendered page.
3. Compare section by section.
4. Fix clear visual mismatches in the narrowest correct layer.
5. Browser-check desktop and mobile.
6. Run repo validation.
7. Report fixed items and remaining visual gaps.

Examples:

```txt
*qa-visual compare this homepage to the uploaded wireframe and fix obvious mismatches
*qa-visual check /about against the Figma export
*qa-visual polish mobile spacing on the current page
```

## `*qa-design`

Use when the implementation needs design-system governance rather than direct pixel matching.

Default workflow:

1. Identify target repo, mode, audit area, validation, and promotion impact.
2. Inspect tokens, primitives, section variants, page composition, and inventories.
3. Classify findings by ownership layer.
4. Fix clear design-system violations in the narrowest correct layer.
5. Update docs/inventories if reusable behavior changes.
6. Run repo validation, including lint/type/build checks when supported.
7. Report remaining design-system gaps, lint/type/build status, and promotion candidates.

Examples:

```txt
*qa-design audit the homepage sections for token and primitive drift
*qa-design find repeated card/button patterns and extract the right reusable layer
*qa-design review this client page before we decide what should become reusable
```

## Repo-Specific Behavior

Mission Control Mode:

- update workflow docs, trackers, command definitions, and private skills
- do not add deployable website code

Starter Governance Mode:

- keep changes reusable and brand-neutral
- update starter inventories when section, primitive, variant, or token behavior changes
- run `pnpm check`

Client Delivery Mode:

- stay inside the client repo
- use approved client inputs only
- keep docs client-safe
- log reusable discoveries as promotion candidates instead of promoting automatically

Registry Governance Mode:

- only promote proven reusable patterns after review
- include metadata and install paths
- avoid client-specific assumptions
