# CLIENT-REPO-EXPORT-POLICY.md

## Purpose

Define what enters a client website repo when a project is created from `paw-starter-kit`.

The goal is to keep client repos useful, complete, and safe without leaking mission-control planning, registry strategy, private prompts, or unrelated client context.

## Current Decision

Client repos are created manually from the starter for now.

Do not build a client export script yet. Revisit automation only after the manual process repeats enough times to reveal stable file groups, rename steps, and cleanup rules.

## Export Principles

- Start from `paw-starter-kit`, not from mission control.
- Copy only files needed to build, deploy, edit, and maintain the client website.
- Include sanitized documentation that helps the client repo stand alone.
- Keep internal coordination, promotion review, and strategic planning in mission control.
- Keep reusable system changes in starter or the future registry, not hidden inside a client repo.
- Record reusable discoveries in the mission-control client tracker.

## Required Runtime Files

Client repos should receive the starter runtime needed for a working website:

- package metadata and lockfile
- framework and tooling config
- app routes and layouts
- reusable UI primitives
- selected section components
- site data files
- content files needed by the selected pages
- shared libraries and utilities
- styling, tokens, and theme files
- public assets required by the starter baseline
- validation scripts and CI config
- environment example files without secrets

Examples:

```txt
app/
components/
content/
data/
lib/
public/
scripts/
styles/
package.json
pnpm-lock.yaml
tsconfig.json
next.config.*
postcss.config.*
eslint.config.*
.env.example
```

Adjust the exact list to match the starter's current file map.

## Selected Patterns

Copy only the patterns needed for the client scope.

Allowed:

- starter section families used by the approved sitemap
- variants and presets selected for the client direction
- reusable primitives required by those sections
- neutral examples that are needed for local development
- pattern docs that are sanitized and directly useful in the client repo

Avoid:

- unused experimental sections
- registry candidate experiments
- internal demos that could confuse client review
- client-specific work from other projects
- unapproved dependencies or integrations

If a client needs a new pattern, implement it locally first. Record it as a promotion candidate in mission control only if it may become reusable.

## Client-Safe Docs

Each client repo should receive a sanitized documentation pack:

```txt
AGENTS.md
README.md
docs/CLIENT-BRIEF.md
docs/CONTENT-MAP.md
docs/EDITING-GUIDE.md
docs/QA-CHECKLIST.md
docs/DEPLOYMENT.md
docs/COMPONENT-USAGE.md
```

These docs should describe how to work on that client site. They should not mention unrelated clients, mission-control planning, private skills, promotion debates, or internal strategy.

## Internal-Only Exclusions

Never copy these into a client repo:

- mission-control docs
- mission-control client trackers
- internal operating model
- internal agent workflow docs
- starter-origin internal planning copies
- registry strategy and promotion checklists
- private prompts or skills
- decision records
- roadmap notes
- unrelated client briefs, assets, or deployment notes
- secrets, credentials, tokens, or private environment files

## Client Repo Creation Checklist

Before creating the repo:

- Confirm the mission-control client tracker exists.
- Confirm approved inputs or explicit waivers are recorded.
- Confirm the starter source branch or commit.
- Confirm the intended client repo name and visibility.

During export:

- Copy the required runtime files from `paw-starter-kit`.
- Add the sanitized client doc pack.
- Rename project metadata.
- Reset placeholder site metadata for the client.
- Keep `.env.example`; do not copy real `.env` files.
- Remove unused examples that could confuse review.

Before first commit:

- Run the project validation command, normally `pnpm check`.
- Confirm no internal mission-control docs were copied.
- Confirm no secrets or private client assets are included accidentally.
- Commit the starter-derived baseline.

## Ownership After Export

After the client repo exists:

- The client repo owns client copy, assets, themes, integrations, deployment notes, and content maps.
- `paw-starter-kit` owns reusable runtime architecture, starter-safe docs, and inventories.
- `paw-mission-control` owns the client tracker, open decisions, promotion candidates, and internal coordination.
- The future `paw-template-registry` will own promoted source-copy patterns after review.

## Automation Policy

Do not create a client export CLI yet.

Create an export script only after:

- at least two manual client repo exports have been completed
- the required file groups are stable
- the sanitized doc pack is stable
- placeholder cleanup steps are repeatable
- the script can avoid internal docs by default

Until then, document gaps and repeated steps in mission control.
