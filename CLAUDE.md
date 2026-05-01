# quartz — Agent Guide

## Role

Quartz is the **display layer**. It renders `my-wiki` content as a public static site. It does not originate content and has no opinion about what gets published.

**Content changes belong in `my-wiki/`, not here.** The `deploy.yml` workflow in `my-wiki` automatically rsyncs published notes into `quartz/content/` on every merge to main. Treat `quartz/content/` as auto-generated.

---

## When to Touch This Repo

Only for:
- **Visual config:** `quartz.config.ts` (theme colors, fonts, base URL, analytics)
- **Layout config:** `quartz.layout.ts` (sidebar, header, footer component arrangement)
- **Plugin additions:** adding/removing Quartz plugins in `quartz.config.ts`
- **Theme overrides:** custom CSS in `quartz/styles/`

Never for content edits. Never for structural changes to the wiki (folders, notes, wikilinks) — those live in `my-wiki/`.

---

## Local Preview

```bash
npx quartz build --serve
```

Opens a local preview at `localhost:8080`. Required before committing visual changes.

---

## Deployment

Deployed on Vercel. `quartz/vercel.json` holds the build config. Pushes to main trigger a Vercel build automatically.

Content is pushed here by `my-wiki`'s `deploy.yml` — not by manual commits to this repo.

---

## Relationship to my-wiki

| my-wiki | quartz |
|---------|--------|
| Source of truth for all content | Renders content as a site |
| `deploy.yml` pushes to `quartz/content/` | `quartz/content/` is auto-generated |
| `CLAUDE.md` is the canonical agent guide | This file only covers display-layer changes |
| `.quartzignore` controls what gets published | `quartz/content/` reflects those exclusions |

For any question about content, structure, or ingest: see [`my-wiki/CLAUDE.md`](../my-wiki/CLAUDE.md).
