# Write Note

## Input
tmp/resolved.md

## Task
Generate a well-structured Obsidian note from the resolved content.

The note must:
- Have a clear title derived from the topic
- Be self-contained — readable without any memory of the original
  conversation
- Match the structure to the conversation type:
  - learning: concept → explanation → key takeaways
  - decision: context → options considered → decision → reasoning
  - exploration: question → what was explored → open threads
  - other: use best judgment

## Output
Write to tmp/note_draft.md:

---
title: 
date: {today}
type: {type from resolved.md}
source: conversation
---

# {title}

{note body}

## Rules
- Do not write to vault — output to tmp/note_draft.md only
- Do not invent content not present in tmp/resolved.md
