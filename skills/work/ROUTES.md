# Areas and routes

Use these six areas to classify a task and select a skill route. Read this file when choosing or routing a task.

The skill names below identify the required capability. Use an installed skill with the same capability even if its name differs. If no installed skill matches, perform the listed action directly.

## Problem

Use **Problem** when the need is unclear, stakeholders disagree, or the discussion contains more opinion than evidence.

- Interview the user about the problem with `/grilling`.
- Research the context from primary sources with `/research`.
- If the user needs to gain domain knowledge, teach using `/teach`.

## Shape

Use **Shape** when the problem is clear but the solution remains open. Requirements may be unsettled, components and boundaries may lack names, alternatives may need comparison, or existing solutions may need review.

- Develop a spec with `/grill-with-docs` or `/to-spec`.
- If the next steps are unclear and it may take many sessions before it's possible to create a spec, then start by mapping out the unknowns with `/wayfinder`.
- Name components and boundaries with `/codebase-design` or `/domain-modeling` before splitting the work into tickets.
- Check for an existing library, competing product, previous solution, or a way to avoid building the feature.
- If discussion stalls, use `/prototype` to build a disposable example that exposes the design questions.

## Build

Use **Build** when the requirements and design are specific enough to implement.

- Split the work into tickets with `/to-tickets`, then implement one ticket per fresh session with `/implement` or `/tdd`.

## Prove

Use **Prove** when implementation is complete but still needs review, end-to-end exercise, or feedback from a person using it.

- Review the diff against its spec and repository standards with `/code-review`.
- Run the implemented behavior end to end.
- Ask a person to use the result.

## Field

Use **Field** for bug reports, support problems, user feedback, and regressions caused by the last change.

- Triage incoming reports with `/triage`.
- Diagnose failures with `/diagnosing-bugs`.
- Record observations that need no immediate action as `saw:` entries.

## Upkeep

Use **Upkeep** when repeated friction makes changes harder, documentation has drifted from reality, or tooling slows the work.

- Address the most prominent repeated friction with `/improve-codebase-architecture` or a direct fix.
- Improve the documentation, skills, or setup that the work depends on.
- In some cases, check recent logs to discover friction points or problems with ways of working which could be improved. This may lead to work in another area like identifying a new Problem, or changing the Shape of parts of the product, or gathering more feedback from the Field, etc.

## Handoff

**Handoff** is a route, not an area. Use it when a session must end before task execution begins. Write the task for a fresh session.

- Write the task for an executor without the current conversation by using `/to-spec` or `/handoff`.
- If several installed skills fit and the choice is unclear, ask the user which one to use.

The selected skill determines the handoff file's location. The handoff must include the thread and autonomy setting, the one task and its done-when condition, the first artifacts to load and why they matter, the route to follow, and an instruction to update `LOG.md` and `STATUS.md` before stopping.
