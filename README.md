# PAW Mission Control

Private internal command center for the Premium Authority Website system.

This repo manages the operating model across:

- `paw-starter-kit`
- future `paw-template-registry`
- client website repos

It is not a deployable website and should not be copied into client projects.

## Repo Roles

| Repo                    | Role                                                                            |
| ----------------------- | ------------------------------------------------------------------------------- |
| `paw-mission-control`   | Internal operations, planning, governance, client tracking, promotion decisions |
| `paw-starter-kit`       | Reusable runtime foundation and starter code                                    |
| `paw-template-registry` | Future source-copy pattern registry                                             |
| client repos            | One real website implementation per client                                      |

## Core Rule

Every task must state:

- target repo
- operating mode
- allowed write scope
- validation required
- promotion impact

## Standard Folders

```txt
docs/       internal operating docs
clients/    client project trackers
systems/    system repo trackers
skills/     private agent skill plans and SKILL.md files
decisions/  decision records
```

## Privacy Boundary

Keep internal strategy, workflows, prompts, skills, roadmap, and promotion decisions here.

Client repos should receive only sanitized project guidance and the runtime files required to build, deploy, and maintain their website.
