---
name: work
description: "Run one project work session: read STATUS.md, settle on one task, do it, and update STATUS.md and LOG.md. Use only when the user explicitly invokes work, with or without naming the task."
license: MIT
---

# Work

Complete one task per session. The user may name the task when invoking this skill or select it with you. Start from the project's current status. End by recording the result and the project's new status.

## Run the session

1. **Read `STATUS.md`.** Read only this file. Step 3 loads the artifacts for the selected task. After reading `STATUS.md`, you must be able to state the heading, autonomy setting, live threads, and evidence listed under **Awaiting**. The **Awaiting** entries tell the user which progress depends on someone else. If `STATUS.md` or `LOG.md` is missing or malformed, establishing or repairing the record is the session's one task. Follow [REPO-SETUP.md](REPO-SETUP.md), then stop.

2. **Select one task.** Use the task the user named. If the user did not name one, review the six areas in [ROUTES.md](ROUTES.md) and inspect recent project history:

   - Read recent `saw:` entries. Look for unresolved observations, repeated friction, feedback, and ideas that have not led to later work.
   - Read recent `did:` entries. Look for a topic that has an uneven mix of areas of work, and consider addressing one of the areas which has had less attention.
   - For each plausible candidate, search its full thread history with `grep -F -- '<thread>' LOG.md`. Do not propose a `saw:` entry that a later entry resolved, rejected, or deliberately parked.

   Compare that history with the current threads and awaiting evidence in `STATUS.md`. Treat a quiet area or a thread that has remained in one area without progress as a reason to consider work there, not as an automatic priority. Propose your recommendation, one option the user has not suggested, and the strongest reason your recommendation may be wrong. Let the user choose. This step is complete when the task has a name, fits one session, and has an explicit done-when condition.

3. **Load the task context and do the work.** Name and read only the artifacts the task needs. If the user named a thread, start with the artifact linked from that thread's `STATUS.md` entry. Match the task to an area and follow its route in [ROUTES.md](ROUTES.md). Add each `saw:` and `chose:` entry to `LOG.md` when the observation or decision occurs. This step is complete when the task meets its done-when condition. If it cannot, add a `saw:` entry that records the reason.

4. **Update the record.** Add a `did:` entry for the work that landed, plus any `saw:` or `chose:` entries that step 3 did not record. Update `STATUS.md` to match the result. This step is complete when an executor who was not in the session can determine the project's current state from `STATUS.md`.

Task selection may require several rounds of discussion or enough artifact reading to consume the session's useful context. In that case, do not start the task. Follow the handoff route in [ROUTES.md](ROUTES.md), then tell the user to start a fresh session from the written handoff.

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

## `saw` logging is open to all, decisions about status are gated by an autonomy level

Anyone may add a `saw:` entry at any time. The entry records an observation but does not change `STATUS.md`. Turning an observation into a heading, thread, or parked item is a decision controlled by **Autonomy** in `STATUS.md`.

- `ask`: Get the user's approval before adding a new heading, thread, or parked item.
- `go`: Make the decision and record it as a `chose:` entry. At the next review, walk through every `chose:` entry added since the previous review.

Either autonomy setting permits updates to existing entries. Move a thread to **Awaiting**, remove a thread after its evidence arrives, and rewrite a vague entry to match the log.

## The six areas

Every piece of work belongs to one of six areas. Include the area in each thread, awaiting entry, and new log entry. Current status shows where work is now; the log shows how attention has moved over time.

- **Problem** clarifies the need, its context, stakeholders, and the evidence that the problem exists.
- **Shape** decides what to make or change, including requirements, boundaries, alternatives, and existing systems to use or fit with.
- **Build** implements work whose requirements and design are specific enough to act on.
- **Prove** checks completed work through review, tests, end-to-end exercise, or feedback from a person trying it.
- **Field** records what actual use reveals, including bugs, regressions, support problems, and user feedback.
- **Upkeep** improves maintainability when repeated friction, drifting documentation, or weak tooling makes future work harder.

[ROUTES.md](ROUTES.md) defines the skill routes for each area.
