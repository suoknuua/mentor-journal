# LLM Mentor Journal (VS Code + Copilot Agent)

This repo is a persistent memory + coaching workflow for mentoring sessions with an LLM in **VS Code + Copilot Agent**.

## How it works

- You hold mentoring/coaching sessions with Copilot Agent in VS Code.
- At the end of each session, Copilot Agent writes a markdown journal file into `/journal/`.
- You then **manually commit and push** to your branch.

## Session workflow

1. **Before Session 1**
   - Fill out: `templates/USER_CONTEXT_TEMPLATE.md`
   - Copy the filled template into: `journal/CONTEXT_SNAPSHOT.md` (or summarize into it).

2. **Start a session**
   - Open Copilot Agent chat in VS Code.
   - Ask it to read:
     - `journal/CONTEXT_SNAPSHOT.md`
     - the most recent 1–3 entries in `journal/`

3. **End a session**
   - Say: `session ended`
   - Copilot Agent must create a new journal entry:
     - Path: `journal/`
     - Name: `DD-MM-YYYY-journal-entry-N.md` (N starts at 1 each day)
     - Format: follow `templates/JOURNAL_ENTRY_TEMPLATE.md`

4. **Commit + push**
   - You commit and push the newly created file(s).

## File naming rules

- Journal entries: `journal/DD-MM-YYYY-journal-entry-N.md`
  - Example: `journal/18-02-2026-journal-entry-1.md`
- If multiple sessions in one day, increment `N`.

## Scaling note (context)

As the journal grows, Copilot may not be able to read everything every time.
The source of truth for “current state” is `journal/CONTEXT_SNAPSHOT.md`, updated periodically (monthly recommended).
