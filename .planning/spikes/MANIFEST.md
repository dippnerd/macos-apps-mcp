# Spike Manifest

## Ideas

### eventkit-depth
Phase 3 of milestone v0.11.0 takes Calendar and Reminders to Mail-level depth: alarms and real
recurrence on events, deletion, lists, subtasks and tags on reminders. Two parts of that scope
must be proven on device before any code: whether Reminders tags have a public write route, and
whether EventKit stores all-day events and RRULE shapes exactly as asked.

**Requirements:**

- No private-API write, in any outcome (REM-04, owner decision in REQUIREMENTS.md).
- A recurrence shape EventKit cannot express is rejected loudly with a typed error, never saved
  in a changed form (Phase 3 success criterion 2).

### notes-semantic-search
NOTE-01: a written decision on Notes semantic search (embedding model, chunking, index build and
refresh policy, size cap, optional-extra boundary) before any indexing code. The spike measures
the real corpus so the decision rests on numbers, not guesses.

**Requirements:**

- The base install gains no ML dependency; semantic search lives behind a `[semantic]` extra.
- The index is a sidecar in the server's own state dir, the same shape as the Mail FTS sidecar.

## Spikes

| # | Idea | Name | Type | Validates | Verdict | Tags |
|---|------|------|------|-----------|---------|------|
| 002 | eventkit-depth | reminders-tags-route | standard | Given macOS 27, when every public surface is checked for a tag write and sqlite for a tag read, then REM-04 resolves | ✓ VALIDATED — read-only from sqlite; `parentReminder` is not public (REM-03 premise false) | reminders, tags, subtasks, sqlite, app-intents |
