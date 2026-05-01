---
title: Vision — LLM Wiki System
tags: [meta, system]
date: 2026-04-30
status: 🌿
---

# Vision — LLM Wiki System

---

## The Core Idea

This is my adaptation of Andrej Karpathy's LLM-wiki idea. Managing your ideas, notes, to-do's requires lots of extra busywork like summarizing, cross-referencing, filing, and keeping things consistent. LLM's are good at this by nature, and can take care of the grunt work for you.

Think of it like having a very diligent research assistant who reads everything you send them, slots it into the right place in a digital library, flags when it contradicts something you previously believed in, and keeps the whole thing internally consistent, without ever needing to be reminded of the filing system.

The human role is **sourcing and direction**. The LLM role is **synthesis and maintenance**.

---

## What Should Happen When I Drop a New Note or Source

1. **Read and extract.** The LLM reads the raw input and saves the raw input. then it synthesizes it by extracting out the deetails including claims, entities, concepts, relationships, and anything else that might be worth noting. 

2. **Locate where it lives.** It checks existing pages: does this belong on an existing entity (like a folder) page? Does it start a new one? Does it belong in multiple places?

3. **Integrate, don't duplicate.** It merges the new information into the right pages. New facts strengthen or challenge existing claims. It notes which. It also cleanly logs changes to each file, like versioning. 

4. **Flag contradictions explicitly.** If the new source says X and the wiki currently says not-X, that gets surfaced — not silently overwritten. The contradiction is surfaced and briought up to the user inn the vault inbox, then the user decides how to proceed. 

5. **Update the synthesis.** Topic summaries should reflect the accumulated weight of everything filed under them, not just the last thing added.

6. **String the concepts.** Wikilinks get created or updated. If the new note introduces a concept that was implicit in three other pages, those pages get backlinks. It also creates smart threads and folders, linking concepts together and organizing the entire wiki 'library' to prevent root clutering 

7. **File and archive.** Raw input goes into `raw/`, gets processed, then archived. The processed wiki pages are the canonical output.

---

## Division of Labor

| Me | The LLM |
|---|---|
| Find the interesting sources | Read and parse them |
| Ask the right questions | Cross-reference against existing knowledge |
| Decide what to explore next | Update entity pages, summaries, links |
| Catch errors in synthesis | Flag contradictions, note open questions |
| Set direction | Do the bookkeeping, answer my questions |

I am the editor-in-chief. The LLM is the staff researcher, advisor, copy editor, and librarian combined.

---

## The Interface Model

I open an inbox (vault-inbox). I paste something, talk through something, or drop a source. That's my side of the contract. 

The LLM reads it, figures out what it means for the existing wiki, makes the edits, and shows me what changed. If something is ambiguous, it asks. If something contradicts existing content, it surfaces it rather than hiding it.

The wiki (Quartz) is the living output. Its always current, internally consistent, and reflecting the full weight of everything that's been ingested.

---

## Why This Compounds

A good knowledge base is not just a filing system. It's a place where seeing two things next to each other produces a third thing you wouldn't have thought of alone. The LLM's job is to make those connections explicit, and help connect all bits of information I consume in an organized and enhanced way. The goal is for the whole to become more than a sum of its parts. 

Over time, the wiki gets harder to surprise. It already knows what I know. New inputs either confirm the model, extend it, or break it. All three are valuable.

---

## Current State vs. Target

**Working now:** 
- vault inbox has submission and chat feature that lets me interacteract with current state of wiki
- note ingestion and source ingestion
- LLM summarization
- basic GitHub Actions pipeline
- Gemini API connectivity 

**Missing or not working well, only based on what I have noticed - so there is definetely more missing/not working as intended:**
- Entity page creation and updating (new files and merging into existing ones). Right now there is a lot of root cluttering
- Contradiction detection and flagging
- Concept and keyword identifying works okay, but needs to be improved  for proper organization and knowledge connection
- Synthesis revision on existing topic pages when new data arrives
- Automatic wikilink insertion and backlink management
- A clear protocol for the LLM to surface open questions back to me
- The architecture is mostly right. The intelligence layer is shallow. That's what needs to evolve.
