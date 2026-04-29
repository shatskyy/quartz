---
title: Wiki Architecture Components
date: 2026-04-29
tags: [systems, tool]
status: seed
description: "Description of the components of a personal wiki architecture, including inbox, processing brain, and frontend display."
sources:
  - https://vercel.com/davids-projects-22750f80/vault-inbox
  - raw/archive/2026-04/2026-04-29-1209-input.md
---

A typical [[Personal Knowledge Management]] (PKM) wiki system can be broken down into several architectural components designed for [[knowledge ingest]] and display:

1.  **Vault Inbox**: This serves as the initial landing zone for raw input. Ideally, it should be capable of handling various file types like PDFs and websites, not just plain HTML. It acts as a staging area before processing.
2.  **Processing Repository ("Brain")**: This component, often a version-controlled repository, houses the core logic and schema. It includes agents or scripts responsible for processing raw input, extracting information, and integrating it into the wiki's structure. This is where the "intelligence" of the system resides.
3.  **Frontend Display (e.g., Quartz)**: This is the user-facing part of the system that renders and displays the entire knowledge base as an accessible wiki. Tools like [[Quartz]] are designed to publish Markdown notes as static websites.
