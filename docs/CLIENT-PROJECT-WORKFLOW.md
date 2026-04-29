# CLIENT-PROJECT-WORKFLOW.md

## Purpose

Define the standard workflow for creating and managing client website repos.

## Workflow

1. Create or select the client tracker in `clients/`.
2. Confirm approved inputs.
3. Create the client repo using `docs/CLIENT-REPO-EXPORT-POLICY.md`.
4. Add client-safe `AGENTS.md` and docs.
5. Add approved copy, assets, theme, and integrations.
6. Build in the client repo.
7. Run `pnpm check`.
8. Review preview deployment.
9. Launch only after human approval.
10. Log reusable discoveries as promotion candidates.

## Client Repo Rules

Client repos may include:

- runtime source files
- selected installed patterns
- approved client content
- approved client media
- client theme
- deployment config
- sanitized docs

Client repos must not include:

- mission-control docs
- internal starter roadmap
- registry strategy
- private prompts or skills
- internal decision logs

See `docs/CLIENT-REPO-EXPORT-POLICY.md` for the full export boundary.

## Agent Instruction

When an agent works on a client repo:

```txt
Read the client tracker and client-safe repo docs.
Work only in the client repo.
Do not copy mission-control docs into the client repo.
Document reusable discoveries as promotion candidates.
```
