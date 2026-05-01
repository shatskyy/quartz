---
title: Vision — LLM Wiki System
tags: [meta, system]
date: 2026-04-30
status: 🌿
---

# Vision — LLM Wiki System

I don't want to write a wiki. I want to *have* a wiki.

The distinction matters. Writing a wiki is busywork — summarizing, cross-referencing, filing, keeping things consistent. That's exactly what LLMs are good at and humans are bad at (we procrastinate, forget, lose the thread). I want to be the person who finds the interesting things and asks the right questions. The LLM does the grunt work.

---

## The Core Idea

Think of it like having a very diligent research assistant who reads everything you send them, slots it into the right place in a shared notebook, flags when it contradicts something you believed last month, and keeps the whole thing internally consistent — without ever needing to be reminded of the filing system.

That's the system I'm building. The human role is **sourcing and direction**. The LLM role is **synthesis and maintenance**.

---

## What Should Happen When I Drop a New Note or Source

1. **Read and extract.** The LLM reads the raw input and pulls out the claims, entities, concepts, and relationships worth keeping.

2. **Locate where it lives.** It checks existing pages — does this belong on an existing entity page? Does it start a new one? Does it belong in multiple places?

3. **Integrate, don't duplicate.** It merges the new information into the right pages. New facts strengthen or challenge existing claims. It notes which.

4. **Flag contradictions explicitly.** If the new source says X and the wiki currently says not-X, that gets surfaced — not silently overwritten. The contradiction is logged and visible until resolved.

5. **Update the synthesis.** Topic summaries should reflect the accumulated weight of everything filed under them, not just the last thing added.

6. **String the concepts.** Wikilinks get created or updated. If the new note introduces a concept that was implicit in three other pages, those pages get backlinks.

7. **File and archive.** Raw input goes into `raw/`, gets processed, then archived. The processed wiki pages are the canonical output.

---

## Division of Labor

| Me | The LLM |
|---|---|
| Find the interesting sources | Read and parse them |
| Ask the right questions | Cross-reference against existing knowledge |
| Decide what to explore next | Update entity pages, summaries, links |
| Catch errors in synthesis | Flag contradictions, note open questions |
| Set direction | Do the bookkeeping |

I am the editor-in-chief. The LLM is the staff researcher, copy editor, and librarian combined.

---

## What This Is Not

- It's not a note-taking app. Notes are inputs, not outputs.
- It's not a journal or a log. The wiki is evergreen synthesis, not a stream.
- It's not a chatbot. Conversations are a way to push new information in, not the end product.
- It's not Notion or Obsidian with AI bolted on. The LLM is the primary author of the wiki. I'm the curator.

---

## The Interface Model

I open an inbox (vault-inbox). I paste something, talk through something, or drop a source. That's my side of the contract.

The LLM reads it, figures out what it means for the existing wiki, makes the edits, and shows me what changed. If something is ambiguous, it asks. If something contradicts existing content, it surfaces it rather than hiding it.

The wiki (Quartz) is the living output — always current, always internally consistent, always reflecting the full weight of everything that's been ingested.

---

## Why This Compounds

A good knowledge base is not just a filing system. It's a place where seeing two things next to each other produces a third thing you wouldn't have thought of alone. The LLM's job is to make those connections explicit — to notice when a new source rhymes with something from six months ago, to build the cross-references that make the whole more than the sum of its parts.

Over time, the wiki gets harder to surprise. It already knows what I know. New inputs either confirm the model, extend it, or break it. All three are valuable.

---

## Current State vs. Target

**Working now:** raw note ingestion, LLM summarization, basic GitHub Actions pipeline.

**Missing:**
- Entity page creation and updating (not just new files — merging into existing ones)
- Contradiction detection and flagging
- Synthesis revision on existing topic pages when new data arrives
- Automatic wikilink insertion and backlink management
- Conversation-driven ingestion (not just file drops)
- A clear protocol for the LLM to surface open questions back to me

The architecture is mostly right. The intelligence layer is shallow. That's what needs to evolve.
