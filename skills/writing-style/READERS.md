# The five readers

This guide defines five reader profiles for technical writing. Each section describes the reader's prior knowledge, the information they need, and examples of ineffective and effective passages. Choose a profile in [SKILL.md](SKILL.md), then read the matching section here.

## Adopter

Adopters decide whether to use the project and learn how to get it working. They read READMEs and user documentation.

They have no project context. Define internal terms on first use, give complete paths, and explain the project's purpose before its implementation. Tell adopters what the project does, what it requires, and how to run it. Use concrete claims instead of promotional adjectives.

This description could apply to any library:

```markdown
A powerful and flexible library that makes working with units a breeze.
```

This revision names the library's purpose and what users can do with it:

```markdown
A library for working with physical units in Polars. Convert column values
between units without writing the conversion arithmetic by hand.
```

## Contributor

Contributors read so they can change the repository correctly. They use contribution guides, developer documentation, and ADRs.

They know the language and tools. They need an introduction to this repository. Give them details they cannot infer: commands, required checks, conventions that tools do not enforce, and reasons for rules that would otherwise seem arbitrary. Do not repeat information that the tools display at the point of failure.

This instruction does not define the standard or the required action:

```markdown
Before opening a pull request, ensure your code meets our quality standards
and follows best practices.
```

This revision names one command and explains its relationship to CI:

```markdown
Run `make check` before opening a pull request. It runs ruff, ty, and the test
suite. CI runs the same target.
```

## Executor

Executors act on instructions without the conversation that produced them. They read specs, tickets, plans, prompts, and handoffs to a fresh session.

They know the codebase and can inspect its contents. They still need enough information to find the work and judge when it is complete. Name modules, interfaces, constraints, and acceptance criteria in the project's searchable vocabulary. Record settled decisions without replaying the deliberation. Follow any required document structure.

An agent starting a new session is an executor. Restate terms coined in conversation and identify agreed files by path. A human colleague who participated in the work is a peer.

This handoff hides every actionable detail:

```markdown
We talked through a few options here and eventually agreed that the timezone
handling probably needs to be centralised somewhere sensible.
```

This revision identifies the interface, behaviour, dependency, and error cases:

```markdown
Add `parse_local_datetime` to the shared pipeline utilities. It takes a naive
Europe/London wall-clock datetime and returns a UTC-aware datetime. Use
`zoneinfo.ZoneInfo("Europe/London")` so daylight-saving transitions use the
correct offset. Raise `ValueError` for an aware input. Ambiguous fall-back times
use `fold=0`.
```

## Maintainer

Maintainers read prose while changing the code beside it. They encounter comments, docstrings, commit messages, and log lines.

They have the code in view, so prose that restates it stalls them. Explain what the code cannot express by itself: the reason for a design choice, a domain invariant, units, ranges, coordinate spaces, ownership, lifetime, ordering requirements, performance bounds, and error behaviour that affects callers.

Docstrings for public APIs define their contracts. State accepted inputs and units, the meaning of the return value, clamping or normalisation, mutation, absence, and error cases.

Names should carry information that the code can express. If a comment only translates an identifier into English, improve the identifier and delete the comment.

```python
# Restates the code and adds no information.
# Loop over the sensors and average their readings.

# Explains an invariant that the code cannot express.
# Sensor readings arrive at irregular intervals, so the mean is time-weighted.
# A plain mean over-counts the sensors that report most often.
```

## Peer

Peers know the codebase and the conversation. They read chat replies, review comments, and handoffs between people who participated in the work.

Use the shared vocabulary and name familiar files directly. Do not restate the request, narrate the next action, or summarise work the reader just watched.

Do not let fast pacing omit a necessary reference. Shared context does not tell a peer which of four routers a sentence means.

This reply leaves the cause and change ambiguous:

```markdown
Fixed it. The design had drifted, which is why the change was needed.
```

This revision identifies both:

```markdown
`ingest_router` was dispatching on file extension, so the new Parquet path fell
through to the CSV branch. It now dispatches on the event type enum.
```
