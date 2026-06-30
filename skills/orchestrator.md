# Orchestrator

## Trigger recognition
- Archive intent: user wants to preserve or archive the current discussion
- If unclear: ask

## Steps
1. Read config.json
2. Confirm scope — ask user where the conversation to archive begins
   if not specified. Write to tmp/scope.md.
3. Read skills/resolve_conversation.md
   Output: tmp/resolved.md
4. Read skills/write_note.md
   Present note draft to user for confirmation.
   Do not proceed without explicit confirmation.
5. Write to vault. Delete tmp/.
