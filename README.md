# conversation-to-note

Most insights don't come from reading articles — they come from working through a problem in conversation. This agent treats the conversation itself as the source, extracts the substance, and writes a self-contained note to your Obsidian vault.

**Built for:** Claude Code + Obsidian users who want to preserve thinking, not just information.

---

## The workflow

```
conversation → resolve → draft → confirm → vault
```

You have a conversation with an AI agent — learning something, making a decision, exploring an idea. When you're ready to preserve it:

> "Archive this discussion, starting from [your first message]"

The agent extracts what matters, drafts a note, shows it to you, and writes to your vault only after explicit confirmation.

---

## Design decisions

**The conversation is the source.**
Traditional knowledge tools ingest external documents — PDFs, URLs, notes. This agent inverts that: the discussion that produced the insight is already the input. No copy-pasting, no saving links.

**Type-aware note structure.**
A decision and a learning look different on paper. The agent detects conversation type and adapts accordingly:
- `learning` — concept → explanation → key takeaways
- `decision` — context → options considered → decision → reasoning
- `exploration` — question → what was explored → open threads

**Explicit confirmation before every write.**
The agent never writes to your vault without showing you the draft first. This is a hard rule in `CLAUDE.md`, not a default behavior. Vault writes are irreversible enough to warrant a human checkpoint.

**Scope is always user-specified.**
The agent never decides on its own where the archivable conversation begins. You tell it the starting point. This avoids silent scope drift and keeps you in control of what gets preserved.

**Skills as plain markdown.**
The agent's behavior is defined in `skills/*.md` — readable files you can inspect, fork, and modify without touching any code.

---
## Setup

In your Claude Code, Obsidian:

```bash
git clone https://github.com/your-username/conversation-to-note
cd conversation-to-note
cp config.template.json config.json
```

Edit `config.json`:
```json
{
  "vault_path": "/path/to/your/obsidian/vault",
  "inbox_folder": "Conversation to Note"
}
```

## Usage

Open a Claude Code session in this directory. Have a conversation on any topic.
When ready to archive:

> "Archive this discussion, starting from [your first message]"

The agent will confirm scope, show you a draft note, and write to vault only after
your explicit confirmation.

## Project structure

```
conversation-to-note/
├── CLAUDE.md                    # Agent entry point and hard rules
├── config.json                  # Your vault path (gitignored)
├── config.template.json
├── skills/
│   ├── orchestrator.md          # Main workflow
│   ├── resolve_conversation.md  # Extract substance from conversation
│   ├── write_note.md            # Draft the Obsidian note
│   └── write_back.md            # Write confirmed note to vault
└── evals/
    └── cases/
        └── learning-01.md       # End-to-end trajectory example
```

## Evals

`evals/cases/` contains real end-to-end trajectories: input conversation,
intermediate outputs (`tmp/resolved.md`, `tmp/note_draft.md`), and final vault
note. Use these as regression baselines when modifying skills.

## License

MIT
