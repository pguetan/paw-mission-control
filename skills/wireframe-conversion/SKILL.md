---
name: wireframe-conversion
description: Inspect and convert PAW homepage/page wireframes into mission-control planning artifacts and starter-kit implementation plans. Use when Codex is given a wireframe image, screenshot, Figma export, or planning asset for `paw-starter-kit` or a client website and needs to create or update wireframe notes, section maps, reusable section/component/data needs, build order, repo-boundary decisions, and validation steps before implementation.
---

# Wireframe Conversion

## Purpose

Turn a wireframe into a repo-safe PAW build plan before coding.

Use mission control for planning artifacts, then implement only in the correct target repo.

## Required Context

Before editing files, identify:

- target repo
- operating mode
- allowed write scope
- validation required
- promotion impact

For starter-system wireframes, default to:

```txt
Target repo: paw-mission-control for planning, then paw-starter-kit for implementation
Mode: Mission Control Mode for planning, then Starter Governance Mode
Allowed write scope: docs/wireframes/ for planning; implementation scope must be declared separately
Validation: Markdown check for planning; pnpm check for starter implementation
Promotion impact: tracking only unless explicitly approved
```

## Wireframe Storage

Store wireframes in `paw-mission-control`, not in `paw-starter-kit`.

Starter-system wireframes:

```txt
docs/wireframes/starter/<page-or-flow>-vN/
```

Client wireframes:

```txt
docs/wireframes/clients/<client-name>/<page-or-flow>-vN/
```

Each package should contain:

```txt
<page>-wireframe-vN.png
handoff-vN.md
<page>-wireframe-vN-notes.md
section-map-vN.md
assets/
```

Use `assets/references/`, `assets/crops/`, and `assets/exports/` for starter wireframes.
Use `assets/approved/` only for real client-approved assets.

## Inspection Workflow

1. Inspect the wireframe visually.
2. Collect or confirm the handoff details from `docs/WIREFRAME-CONVERSION-HANDOFF.md`.
3. Identify the full section order from top to bottom.
4. Classify each block as existing starter section, new reusable section, shared component, or page composition only.
5. Identify data sources needed for each block.
6. Mark client-specific copy, names, brands, logos, or assets that must be replaced for starter-safe implementation.
7. Define a build order that starts with shared primitives and foundational sections.
8. Define the post-implementation QA sequence.
9. Update the handoff, notes, and section map before implementing.

## Handoff Requirements

For close first-shot implementation, use `docs/WIREFRAME-CONVERSION-HANDOFF.md`.

The handoff should capture:

- reference source and version
- target repo and route
- desktop/mobile viewport sizes
- exact, close, or directional match level
- typography, color, spacing, sizing, radius, and asset details
- copy/content constraints
- ordered section expectations
- responsive behavior
- interaction and accessibility requirements
- implementation constraints
- QA acceptance criteria

If the handoff is incomplete, state assumptions before coding.

## Section Map Requirements

The section map must include:

- ordered wireframe blocks
- starter section candidate names
- whether each block is reusable
- notes about existing vs new sections
- shared component needs
- data source needs
- build decisions
- validation expectations

Prefer section names that match starter conventions:

```txt
HeroSection
ServicesSection or OffersSection
TestimonialsSection
CtaSection
LogoStripSection
LeadMagnetSection
BlogPreviewSection
AuthorityBioSection
SiteHeader
SiteFooter
```

## Repo Boundary Rules

- Planning artifacts live in `paw-mission-control`.
- Reusable, brand-neutral implementation lives in `paw-starter-kit`.
- Client-specific implementation lives in the client repo.
- Registry candidates are tracked in mission control and are not promoted automatically.
- Do not copy mission-control wireframes or internal notes into client repos.

## Starter-Safe Rules

For starter implementation plans:

- replace real names, company names, testimonials, client logos, and private assets with neutral example data
- express visual direction as reusable presets, not fixed brand identity
- use tokens and existing primitives before adding new styles
- add new primitives only when repeated patterns justify them
- update component and section inventories with implementation changes
- run `pnpm check` before reporting completion

## Post-Implementation QA Hooks

Every wireframe implementation plan must include these follow-up checks:

1. `*qa-visual` after implementation to compare the rendered page against the wireframe or visual reference.
2. `*qa-design` after visual QA to audit tokens, primitives, variants, repeated patterns, and styling ownership.

These hooks are required planning steps, not permission to ignore repo boundaries.

For starter work, the QA plan should also include `pnpm check`.
For client work, use the client repo's validation command and log reusable discoveries as promotion candidates.

## Recommended Build Order

Build in small slices:

1. shared primitives and data shape updates
2. header/footer and global page skeleton
3. simple reusable sections such as CTA and logo strip
4. content-heavy sections such as offers, bio, lead magnet, blog preview, testimonials
5. page template/composition
6. responsive polish
7. `*qa-visual` rendered comparison
8. `*qa-design` design-system audit
9. docs and inventory updates
10. validation and commit

## Output

When planning is complete, report:

- where the wireframe package lives
- sections identified
- existing starter pieces to reuse
- new sections/components/data needed
- suggested build order
- target repo for implementation
- validation required
- required `*qa-visual` and `*qa-design` follow-up
- open questions
