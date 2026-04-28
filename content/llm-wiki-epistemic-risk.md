---
title: LLM Wiki Epistemic Risk & the RAG Solution
date: 2026-04-27
tags: [pkm, concept]
status: seed
description: "How LLM synthesis errors silently compound across linked notes (epistemic drift), and why RAG over immutable source documents is the architectural fix."
---

## The Problem: Error Propagation in LLM Wikis

An [[quartz-obsidian-wiki-setup|LLM-powered wiki]] introduces a subtle but compounding risk: a single misinterpretation or hallucination by the LLM layer does not stay isolated. Because the [[00-Meta/System-Architecture|synthesis pipeline]] links and integrates notes, one bad fact can be woven into multiple downstream notes — silently corrupting an entire knowledge layer over time.

This is sometimes called **epistemic drift**: the gradual decay of a knowledge base's reliability as errors compound through interconnected notes.

Key failure modes:
- A misquoted statistic gets linked into several notes, normalizing the error.
- A concept mis-synthesized from a source article becomes the "canonical" understanding, overwriting the original meaning.
- Because the LLM writes confidently, errors are hard to distinguish from correct entries without re-checking sources.

## The Solution: A Two-Layer Architecture

The fix is to separate **ground truth** from **personal synthesis**:

| Layer | Tool | Purpose |
|---|---|---|
| **Truth** | RAG over source documents | Answer factual questions against original, unmodified articles |
| **Synthesis** | LLM Wiki (this vault) | Personal notes, reflections, and connected ideas |

### RAG as Ground Truth

RAG (Retrieval-Augmented Generation) answers questions by retrieving the original source text first, so the answer is grounded in the unedited document rather than a prior LLM synthesis. Use RAG when you need to query articles, papers, or any external content you have published or collected.

This keeps the source material **immutable** — the LLM reads it at query time rather than rewriting it into the wiki.

### LLM Wiki as Personal Synthesis Layer

Reserve the LLM wiki for:
- Personal notes and observations.
- Reflections on ideas (not verbatim article summaries).
- Connecting concepts across domains using `[[Double Brackets]]`.
- **Not** bulk-ingesting third-party articles verbatim.

The distinction is intentional: when a note is personal synthesis rather than a factual claim, a small LLM error is far less damaging because it does not claim to be ground truth.

## Practical Guideline for This Vault

- **Articles you have published** → Index them for RAG retrieval; do not synthesize them into notes.
- **Ideas and reflections** → Synthesize into atomic notes here.
- **External research** → Summarize with explicit attribution; link to the original source.

## Related Notes

- [[quartz-obsidian-wiki-setup]] — The PKM stack this vault runs on.
- [[00-Meta/System-Architecture|System Architecture]] — The full ingestion pipeline.
- [[recursive-self-improvement]] — Related risks of compounding AI errors.
