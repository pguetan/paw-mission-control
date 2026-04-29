# Wireframes

Wireframes and planning assets live here for internal mission-control use.

Do not copy this folder into client repos or `paw-starter-kit`.

Use `docs/WIREFRAME-CONVERSION-HANDOFF.md` before implementation to capture the details needed for a close first-shot build.

Use `starter/` for reusable starter-system planning.
Use `clients/<client-name>/` for real client-specific planning.

## Folder Pattern

```txt
docs/wireframes/
├─ starter/
│  └─ homepage-v1/
│     ├─ home-wireframe-v1.png
│     ├─ handoff-v1.md
│     ├─ home-wireframe-v1-notes.md
│     ├─ section-map-v1.md
│     └─ assets/
│        ├─ references/
│        ├─ crops/
│        └─ exports/
└─ clients/
   └─ <client-name>/
      └─ <page-or-flow>-v1/
         ├─ <page>-wireframe-v1.png
         ├─ handoff-v1.md
         ├─ <page>-wireframe-v1-notes.md
         ├─ section-map-v1.md
         └─ assets/
            ├─ approved/
            ├─ references/
            ├─ crops/
            └─ exports/
```

## Asset Rules

- `references/`: inspiration, screenshots, and visual references.
- `approved/`: client-approved source assets only.
- `crops/`: cropped pieces extracted from wireframes.
- `exports/`: exported frames or screens from design tools.

Keep real client assets under `clients/<client-name>/`.
Keep reusable starter-system planning under `starter/`.
