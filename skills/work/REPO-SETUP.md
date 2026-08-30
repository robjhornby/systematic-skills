# Repo setup

Use the entire session to establish `STATUS.md` and `LOG.md` when either file is missing. Do not start another task. Reading an established repository for current work can consume the session's useful context, so the two files also serve as the handoff to the next session.

If both files exist but either is malformed, preserve every valid entry and draft the smallest changes that bring both files back to the formats in `SKILL.md`. Show the proposed repair and write only what the user approves. Then continue at step 5 and stop.

For a new record:

1. **Ask for two settings.** Ask the user for the heading, which states the project's current direction, and the autonomy setting, either `ask` or `go`.

2. **Find candidates for each status section.** Inspect the tracker, open TODOs, recent commits, active branches, and documentation that no longer matches the project. Put shipped work that still needs someone's confirmation under **Awaiting**. Propose only work that is currently active and fits in a one-screen `STATUS.md`. Identify the candidates you recommend parking or omitting.

3. **Draft both files and request approval.** The `STATUS.md` draft contains the heading, autonomy setting, threads, awaiting items, and parked items. The `LOG.md` draft contains the entries described in step 4. Show both drafts. Write only content the user approves. The user must approve every heading, thread, awaiting item, and parked item regardless of the selected autonomy setting, because that setting does not take effect until `STATUS.md` exists.

4. **Write the approved files.** Seed `LOG.md` with one `did:` entry for each of the last few pieces of work that landed and assign each entry its primary area. Add an `[Upkeep] did:` entry for establishing the record.

5. **Set up maintenance outside `/work`.** Check whether `maintain-project-record` is installed.

   If it is installed, offer this instruction for the project's `CLAUDE.md` or `AGENTS.md`:

   > After project work outside `/work`, use `/maintain-project-record` when an important observation might otherwise be lost and before ending a session that produced a durable observation, decision, completed result, or factual change to an existing status entry. It updates `LOG.md` and reconciles existing `STATUS.md` entries. Use `/work` to choose or add work.

   If the skill is not installed, explain that `/work` still maintains both records during explicit work sessions, but other sessions will not maintain them automatically. Offer this command, adding the same scope and agent flags used to install `work`:

   ```sh
   npx skills@latest add robjhornby/systematic-skills \
     --skill maintain-project-record
   ```

   If the user installs it during setup, confirm that it is available and then offer the instruction above. Otherwise do not add an instruction that names an unavailable skill. A later `/work` session can add the instruction after installation.

Then stop. Tell the user to start a fresh session with `/work` for the next project task.

Setup or repair is complete when both files follow the record format, the user has approved every changed entry, and the user knows to start the next task in a fresh session.
