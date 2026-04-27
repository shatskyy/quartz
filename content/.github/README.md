# Not used for GitHub Actions

Workflow YAMLs used to live here by mistake. **GitHub only runs workflows from** `.github/workflows/` **at the repository root** (this repo: `quartz/.github/workflows/`).

Wiki automation (**ingest** on `raw/**`, **deploy** to this Quartz repo) lives in **`shatskyy/my-wiki`**: see `my-wiki/.github/workflows/ingest.yml` (Gemini → Groq via `ingest_once.py`, then `build_catalog.py`, `/tmp/pr_meta.json` for PR text) and `deploy.yml`.

This folder is listed in `quartz.config.ts` `ignorePatterns` so it is not published as site pages.
