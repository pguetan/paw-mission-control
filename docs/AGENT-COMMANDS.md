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

| Command      | Skill               | Purpose                                                                                                                                    |
| ------------ | ------------------- | ------------------------------------------------------------------------------------------------------------------------------------------ |
| `*qa-visual` | `skills/qa-visual/` | Compare a rendered page against a wireframe, screenshot, Figma export, or visual reference, then fix clear visual mismatches.              |
| `*qa-design` | `skills/qa-design/` | Audit design-system application, token usage, primitive/variant ownership, repeated patterns, and styling gaps, then fix clear violations. |

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
6. Run repo validation.
7. Report remaining design-system gaps and promotion candidates.

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
