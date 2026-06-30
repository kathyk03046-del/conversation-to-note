# Write Back

## Input
tmp/note_draft.md
config.json

## Task
Write the note to the vault.

1. Read vault_path and inbox_folder from config.json
2. Read title from tmp/note_draft.md frontmatter
3. Write tmp/note_draft.md to:
   {vault_path}/{inbox_folder}/{title}.md

## Rules
- Never overwrite an existing file — if a file with the same title
  exists, use {title}-{YYYYMMDD-HHmm}.md instead
- Only write to inbox_folder — never write outside it
