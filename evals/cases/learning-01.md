# Eval Case: learning-01

Type: learning
Topic: Karpathy's LLM Wiki pattern
Note: Mixed scenario — conversation + external URL source

---

## Input: Conversation

```
User: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f What is this article about

Agent: This is a post by Andrej Karpathy proposing a "LLM Wiki" pattern — an alternative
to traditional RAG systems. The core idea: instead of dumping documents into a vector store
and searching them raw on every query, you have an LLM build and maintain a living wiki
(structured markdown files) as you feed it new sources. The LLM synthesizes content,
cross-links pages, and resolves contradictions incrementally — so the knowledge base
compounds over time rather than requiring re-synthesis on each query. The architecture has
three layers: immutable raw sources, the LLM-maintained wiki, and a schema that governs how
the wiki is organized. It's a rethinking of personal knowledge management where AI handles
the bookkeeping and humans handle curation.

User: Explain more about the 3 layers. What are the product use cases for this structure?

Agent: [explained three layers and product use case table]

User: can you turn this into note for me
```

Scope: entire conversation from first message.

---

## Step 1: tmp/resolved.md

```
topic: Karpathy's LLM Wiki pattern — a structured approach to AI-maintained knowledge bases
key_points:
  - Traditional RAG indexes raw documents and re-synthesizes on every query; the LLM Wiki
    pattern instead has the LLM build and maintain a persistent, structured wiki that
    compounds over time
  - Three-layer architecture:
      1. Raw Sources (immutable): original documents the LLM reads but never modifies — the
         ground truth
      2. The Wiki (LLM-owned): markdown files the LLM generates and keeps consistent —
         pages are created, updated, cross-linked, and contradiction-flagged as new sources
         arrive
      3. The Schema (configuration): a file like CLAUDE.md that governs how the wiki is
         organized and what workflows the LLM follows; described as the most important file
         in the repo
  - The wiki is a "compounding artifact" — it gets richer with each source added rather
    than requiring re-synthesis each query
  - Product use cases: personal knowledge management, research wikis, book companions,
    team/internal wikis, competitive intelligence, due diligence
  - The pattern is best suited to domains where knowledge accumulates over time and
    maintaining consistency/cross-references is the expensive part
conclusion: The LLM Wiki pattern is a compelling alternative to RAG when the goal is a
  persistent, growing knowledge base rather than one-off retrieval
type: learning
```

---

## Step 2: tmp/note_draft.md

```markdown
---
title: LLM Wiki Pattern — AI-Maintained Knowledge Bases
date: 2026-06-30
type: learning
source: conversation
---

# LLM Wiki Pattern — AI-Maintained Knowledge Bases

Proposed by Andrej Karpathy. An alternative to RAG where an LLM builds and maintains a
persistent, structured wiki rather than re-synthesizing raw documents on every query.

Source: https://gist.github.com/karpathy/442a6bf555914893e9891c11519de94f

## Core Idea

Traditional RAG indexes raw documents and synthesizes answers at query time. The LLM Wiki
pattern instead has the LLM incrementally build a **wiki** — a structured collection of
markdown files — as new sources are added. The wiki is a *compounding artifact*: it grows
richer over time and can be queried directly without re-synthesis.

## Three Layers

**1. Raw Sources (immutable)**
Original documents — articles, PDFs, transcripts, data files. The LLM reads these but never
modifies them. They are the append-only ground truth.

**2. The Wiki (LLM-owned)**
A directory of markdown files generated and maintained entirely by the LLM. When a new
source is ingested, the LLM updates existing pages, creates new ones, adds cross-links, and
flags contradictions. No human writes to this layer directly.

**3. The Schema (configuration)**
A file (e.g. `CLAUDE.md`) that encodes how the wiki is organized — page types, ingestion
conventions, maintenance workflows. Karpathy calls this the single most important file in
the repo because it governs the LLM's behavior as an editor.

## Product Use Cases

| Domain | Input | Output |
|---|---|---|
| Personal knowledge | Journal entries, articles | Evolving notes on goals, health, ideas |
| Research | Papers, notes over months | Thesis-aware wiki that updates as thinking evolves |
| Book companion | Chapters as you read | Cross-linked character, theme, and plot pages |
| Team knowledge | Slack threads, meeting transcripts | Internal wiki that stays current automatically |
| Competitive intel | News, filings, product releases | Structured landscape updated as sources are added |
| Due diligence | Company docs, interviews | Organized synthesis across a corpus |

## Key Takeaway

The pattern is best suited to domains where knowledge **accumulates over time** and
maintaining consistency and cross-references is the expensive part. In those cases, the LLM
Wiki outperforms raw RAG because synthesis work happens at ingest time, not query time.
```

---

## Expected output (vault note)

Same as note_draft.md above — written to:
`Conversation to Note/LLM Wiki Pattern — AI-Maintained Knowledge Bases.md`

---

## Notes on this case

- Mixed scenario: conversation included an external URL the agent fetched
- Agent correctly inferred scope without being asked to clarify
- type: learning correctly identified
- Structure matches learning template: concept → explanation → key takeaways
