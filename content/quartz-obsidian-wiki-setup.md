---
title: Quartz + Obsidian Wiki Setup
date: 2026-04-27
tags: [pkm, system]
status: evergreen
description: "How this wiki is built using Obsidian for editing and Quartz for publishing, following Karpathy's atomic note philosophy."
sources:
  - https://quartz.jzhao.xyz/
---
**Summary**: A personal knowledge base built with Obsidian for editing and Quartz for publishing, following Andrej Karpathy's philosophy of atomic, interlinked notes.

---

## Stack

- **Obsidian** — local-first Markdown editor; handles authoring, backlinks, and graph view.
- **Quartz** — static-site generator that converts an Obsidian vault into a fast, searchable website.

## Automation (wiki repo)

Ingest runs in **my-wiki** on pushes to `raw/**` on `main`: **Gemini** first, **Groq** fallback (`ingest_once.py`); applies JSON (`archive_raw`, `discard_raw`, `log_append`; legacy `delete_raw` mapped in code); writes `/tmp/pr_meta.json`; then **`build_catalog.py`** (regenerates `00-Meta/catalog.md`, skips `CLAUDE.md` / `AGENTS.md`). Secrets: `GEMINI_API_KEY` and/or `GROQ_API_KEY`, optional model overrides, `GH_TOKEN`. Optional entry via **vault-inbox** (commit to `raw/` or Claude Routine). Details: `00-Meta/System-Architecture.md`.

## Karpathy Philosophy Applied

Andrej Karpathy advocates for notes that are small, focused, and heavily cross-linked rather than large monolithic documents. Key principles adopted here:

- **Atomic notes** — one concept per file; split when a section grows large enough to stand alone.
- **Bi-directional linking** — every note that references a concept links it with `[[Double Brackets]]`; Obsidian and Quartz both render the backlink graph automatically.
- **Progressive refinement** — notes are never "done"; new information is integrated into the existing note rather than duplicated.

## Known Issues & Gotchas

### YAML Tags — No Hashtags

Quartz throws a **`flow collection` parse error** if tag values in the YAML front matter include a `#` symbol (e.g., `tags: [#quartz, #obsidian]`). Always write tags without the hash:

```yaml
# Correct
tags: [quartz, obsidian]

# Breaks Quartz
tags: [#quartz, #obsidian]
```

This rule is enforced in [[CLAUDE.md]] under *Metadata Standards*.

## Source Reference

- [The State of GPT — Andrej Karpathy](https://karpathy.ai/stateofgpt.html)

## Related Notes

- [[Test]]
