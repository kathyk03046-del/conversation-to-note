# Resolve Conversation

## Input
The conversation segment specified by the user — from the stated
starting point to the current message. This exists in the current
context window; no file input required.

## Task
Read the specified conversation segment and extract:
- What topic was being discussed
- What the key points were
- Whether a conclusion was reached
- What type of conversation this was

## Output
Write to tmp/resolved.md:

topic: 
key_points:
  - 
conclusion: (leave blank if none)
type: learning | decision | exploration | other

## Rules
- Do not summarize the conversation process — extract the substance
- Do not include points that were abandoned or superseded during discussion
- If the scope is ambiguous, ask the user to clarify before proceeding
