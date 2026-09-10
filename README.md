# public/

Static media served from the site root. A file at `public/games/gomoku.jpg`
is reachable at `/games/gomoku.jpg`.

```
public/
├── games/   game cover art        → src/modules/games/content/games.ts
├── crew/    team portraits        → src/modules/crew/content/crew.ts
├── hero/    device screenshots    → src/modules/hero/content/hero.ts
└── brand/   logo and press files  (not referenced by the page yet)
```

App icons and social preview images are **not** here — Next.js picks those up
from `src/app/` by filename. See `docs/ASSETS.md` for the full list.

## Rules

- **Name the file after the content id.** The game with `id: 'weeland'` gets
  `public/games/weeland.jpg`. That is the only convention keeping this folder
  readable a year from now.
- Lower-case, hyphenated, no spaces, no version suffixes (`-final-v2`).
- Ship the source at roughly twice the largest rendered size, then stop —
  `next/image` resizes and converts to AVIF/WebP per request. A 4000px hero
  screenshot costs build time and gains nothing.
- Photographic content → `.jpg`. Flat colour, hard edges or transparency →
  `.png`. Vector marks → `.svg`.
- Keep each file under ~300 KB before optimisation.

Everything in here today is demo artwork drawn by
`scripts/generate-demo-assets.py`. Overwrite a file with the real one and the
site picks it up — the paths are already wired.

Dropping a *new* file in here does nothing on its own: add its path as `src` in
the matching content file. `docs/ASSETS.md` has the exact slot list.
