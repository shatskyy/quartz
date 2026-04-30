---
title: Proposed Multi-Mode Wiki Vault Architecture
date: 2026-04-29
tags: [meta, design]
status: seed
description: "A proposal for a more segmented wiki vault architecture, introducing distinct modes for personal, books, and research content with tailored processing."
sources:
  - raw/archive/2026-04/2026-04-29-1447-input.md
---
This note outlines a proposed alternative vault structure for the wiki, aiming to introduce distinct "modes" that would influence content ingestion, organization, and processing logic. The proposal suggests segregating raw inputs and processed wiki content into specific subdirectories based on their domain.

### Proposed Directory Structure

The core idea is to move beyond a flat root directory for all wiki notes and introduce domain-specific paths:

```
vault/
├── raw/
│   ├── personal/
│   ├── books/
│   ├── research/
│   └── assets/
├── wiki/
│   ├── shared/
│   │   ├── entities/
│   │   ├── concepts/
│   │   └── timelines/
│   ├── personal/
│   │   ├── syntheses/
│   │   ├── source-notes/
│   │   └── dashboards/
│   ├── books/
│   │   ├── chapters/
│   │   ├── characters/
│   │   ├── themes/
│   │   └── quotes/
│   ├── research/
│   │   ├── source-notes/
│   │   ├── claims/
│   │   ├── comparisons/
│   │   ├── syntheses/
│   │   └── bibliography/
│   ├── index.md
│   ├── log.md
│   ├── hot.md
│   └── overview.md
├── profiles/
│   ├── personal.md
│   ├── books.md
│   └── research.md
├── AGENTS.md
└── CLAUDE.md
```

### Proposed Operational Modes

The vault would operate with different "modes" selected via a schema switch in the vault inbox, not a product switch. Each mode would tailor the ingestion and processing:

#### Personal Mode
*   **Focus**: Journal entries, habits, goals, people, recurring themes, and “what changed recently.”
*   **Characteristics**: Strong privacy defaults, less aggressive auto-web-search.

#### Books Mode
*   **Focus**: Chapter-by-chapter ingestion of book content.
*   **Characteristics**: Dedicated pages for [[characters]], [[themes]], plot threads, locations, [[quotes]]. Optional spoiler-handling conventions.

#### Research Mode
*   **Focus**: More formal source summaries and academic content.
*   **Characteristics**: Explicit [[claim]]/[[evidence]]/counterclaim structure. [[Contradiction]] tracking and [[source quality]] notes.

This proposal aims to provide more specialized [[knowledge management]] and [[information architecture]] within the wiki.

## Related Concepts
- [[Vault Structure]]
- [[Ingest Process]]
- [[Information Architecture]]
- [[Knowledge Management Systems]]
