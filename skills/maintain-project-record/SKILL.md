---
name: maintain-project-record
description: "Maintain an existing project's STATUS.md and LOG.md after project work performed outside the work skill. Use during a long session when an important observation might be lost, and before ending a session that produced a durable observation, decision, completed result, or factual change to an existing status entry. Do not use while work is active."
---

# Maintain project record

Carry useful results from an ordinary project session into `LOG.md` and reconcile existing entries in `STATUS.md`. Record what happened without choosing what the project should do next.

## Maintain the record

1. **Check the record.** Confirm that both `STATUS.md` and `LOG.md` exist at the repository root and follow the formats below. If either file is missing or malformed, do not create or repair it. Tell the user to invoke `/work` to establish or repair the record, then stop.

2. **Identify durable events.** Review what has happened in the session. Keep only information another session could use:

   - an observation about the problem, product, use, or way of working;
   - a decision that was actually made, including its reason or a rejected option;
   - completed work and what became true because of it;
   - a factual change to the state or ownership of an existing status entry.

   Do not log commands, file reads, routine test runs, transient theories, or narration of the session. If there is no durable event and no existing status entry needs reconciliation, make no changes and stop.

3. **Append to `LOG.md`.** Use the exact name from `STATUS.md` when an event belongs to a current thread. Otherwise search `LOG.md` for a likely existing thread name and reuse it. If no thread exists, choose a concise stable name; a new log thread does not create a status entry. Assign one primary area to each event and append the entries in the order they occurred. Never edit an existing log entry.

4. **Reconcile existing status entries.** Change only entries already present in `STATUS.md`:

   - rewrite an entry when its factual state has changed;
   - move a thread to **Awaiting** when its next action belongs to someone or something outside the current work;
   - move an awaiting entry back to **Threads** when its evidence arrives and more work remains;
   - remove an entry when it is complete or its awaited evidence has arrived and no further action remains.

   Do not change the heading. Do not create a thread, park or unpark work, reprioritize anything, or turn a `saw:` entry into planned work. Those are planning decisions for `/work`. Do not change a parked item.

When this skill runs during a long session, append an important observation that might otherwise be lost. Run the workflow again before ending the session to record the completed result and reconcile status.

## The record

Two files at the repository root carry the project between sessions. Both are indexes. Each entry summarizes the state or event and links to the detailed spec, ticket, map, ADR, or code.

### STATUS.md: current state

Keep `STATUS.md` current and small enough to read in one screen. Rewrite existing entries as the state changes. Sort live work into three sections according to who owns the next action.

```markdown
# Status

## Heading

<where the project is pointed right now — one or two lines>

**Autonomy:** ask <!-- ask | go -->

## Threads

<!-- Unblocked items currently being worked on: name — area — one-line state — [artifact](path) -->

- <name> — <area> — <state> — [<artifact>](<path>)

## Awaiting

<!-- Items blocked by an external factor: name — area — the evidence wanted and who owns getting it — [artifact](path) -->

- <name> — <area> — <evidence> — [<artifact>](<path>)

## Parked

<!-- Items which are not currently being worked on: item — the reason -->

- <item> — <reason>
```

Prune `STATUS.md` after project work. Move a thread to **Awaiting** as soon as its next action belongs to someone else, such as a person who must use the result, a run that must finish, or a reply that must arrive. Move it back to **Threads** when the evidence arrives and more work remains. Remove it when the work is complete or the evidence has arrived and no further action remains. Rewrite any entry that no longer states the current condition precisely. `LOG.md` retains the history removed from `STATUS.md`.

### LOG.md: project history

`LOG.md` is append-only. Every entry has fields in this order: date, who, thread, area, verb, what, and link. Add new entries at the bottom. Write the area in square brackets so it can be searched independently. Search the log with `grep`; do not reorganize or edit existing entries.

```markdown
- 2026-07-14 (rob) netcode [Shape] chose: lightyear + WebSocket, server-authoritative; burst-mode Hetzner beats always-on billing [docs/netcode-research.md]
- 2026-07-14 (research) netcode [Shape] saw: low-APM economy may need interpolation only, not full prediction [docs/netcode-research.md#risks]
- 2026-05-23 (agent) pointer-routing [Build] did: all input through one router, 8/8 issues [docs/prds/deepen-pointer-routing.md]
```

Every entry uses one of these verbs:

- `saw` records an observation when it occurs, including friction, feedback, surprises, ideas, and artifacts that have drifted from reality.
- `chose` records a decision and its reason. It also records an option that was rejected and why.
- `did` records work that landed and the resulting state.

The thread name and area are the entry's two tags. Keep the same thread name throughout a line of work. Before adding an entry, search `LOG.md` for the thread name and reuse the name in the results. For example, `grep netcode LOG.md` returns the history of the `netcode` thread, `grep '\[Build\] did:' LOG.md` returns completed Build work, and `grep ' chose:' LOG.md` returns every recorded decision.

The area describes the primary kind of attention recorded by that entry, not the thread as a whole. A thread can move between areas, such as from Shape to Build to Prove, and one session can produce entries in different areas. A `did:` or `chose:` entry normally uses the task's area. A `saw:` entry uses the area the observation most directly concerns, so a Build session can record an Upkeep observation. Classifying the observation does not turn it into a task. When an observation touches several areas, choose the primary one. When a line contains two distinct observations, split it into two entries.

## The six areas

- **Problem** clarifies the need, its context, stakeholders, and the evidence that the problem exists.
- **Shape** decides what to make or change, including requirements, boundaries, alternatives, and existing systems to use or fit with.
- **Build** implements work whose requirements and design are specific enough to act on.
- **Prove** checks completed work through review, tests, end-to-end exercise, or feedback from a person trying it.
- **Field** records what actual use reveals, including bugs, regressions, support problems, and user feedback.
- **Upkeep** improves maintainability when repeated friction, drifting documentation, or weak tooling makes future work harder.
