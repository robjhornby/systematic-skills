---
name: skill-system-review
description: Review an agent skill system by mapping its skills, artifacts, handoffs, feedback loops, levels of work, and missing capabilities. Use when reviewing, redesigning, or extending a collection of agent skills.
license: MIT
---

# Skill system review

Review a collection of agent skills as one working system before recommending changes. Determine whether its skills help an agent and user solve problems. Check whether the skills identify surrounding systems, cover the appropriate levels of work and checks, define handoffs and feedback loops, and support sustainment. Do not modify the target skill system during the review.

## Target and inspection

If the user names a target path, review that path. Otherwise, inspect the current directory for plausible skill-system roots. A plausible root contains `SKILL.md` files, skill manifests, or skill documentation. Use the root if exactly one exists. If no plausible root exists or if several exist, ask the user which skill system to review.

Read in layers:

1. Read top-level files that explain intent, such as `README.md`, `AGENTS.md`, `CLAUDE.md`, setup documentation, manifests, and context documentation.
2. Read every `SKILL.md` in scope.
3. Read directly referenced files one level deep when they are needed to understand behavior, artifacts, handoffs, or feedback.
4. Read scripts only when a skill's behavior depends on them.

Stop after one level of directly referenced files. List excluded paths and unread referenced files in the report.

## Review model

Start with the target system's stated purpose. Examine how its skills guide an agent and user as they work on the user's problems.

Classify each skill with one or more roles:

- `orchestrator`: coordinates a multi-step workflow or user interaction
- `discipline`: provides a reusable working practice used inside other work
- `artifact producer`: creates or updates a durable artifact
- `router`: helps choose another skill or workflow
- `setup/configuration`: prepares conventions, labels, tools, or project state

Check whether the skills prompt the agent and user to answer these practical systems questions:

- What is the context around the problem?
- What are we building, changing, choosing, introducing, or removing?
- Who or what is involved in understanding, creating, checking, and learning from the result?
- What happens when the result is used in context?
- What existing systems, tools, people, data, workflows, or prior solutions should this work with or use?
- How will this be maintained, changed, operated, or kept useful over time?
- What alternatives already solve this, partly solve this, or could replace this approach?

Map levels of work and checks:

- `problem and context`: the user's problem and the conditions around it
- `requirements`: what needs to be true for the result to be good enough in context
- `system design`: parts, boundaries, relationships, responsibilities, tradeoffs, and surrounding-system fit
- `implementation`: the work that produces the result
- `local checks`: checks of a concrete part or narrow behavior
- `integration checks`: checks of how parts work together and interact with surrounding systems
- `in-context checks`: checks of whether the result solves the problem when used in context

A focused skill may cover only one or a few levels. Evaluate whether the system's coverage and handoffs fit its stated purpose.

Assess how well the whole skill system supports these capabilities:

- `context understanding`: understands the user's situation or problem
- `solution shaping`: defines what should be built, changed, chosen, removed, or decided
- `realization workflow`: guides execution, implementation, or production of work
- `sustainment`: supports maintenance, future change, migration, ownership, and documentation
- `collaborating systems`: discovers or integrates existing tools, code, data, APIs, people, or workflows
- `competing alternatives`: compares existing approaches or replacement options
- `feedback loops`: feeds results, checks, reviews, deployed signals, user feedback, and follow-on problems into later work
- `abstraction levels`: moves between problem/context, requirements, system design, implementation, local checks, integration checks, and in-context checks

Rate the system's support for each capability as `strong`, `partial`, `weak`, or `absent`. Ratings must include evidence and consequence.

## Feedback and findings

Distinguish these feedback loops:

- `process-internal feedback loop`: feedback generated or handled inside a skill-defined workflow, such as user clarification, test results, review findings, or revised artifacts
- `external signal feedback loop`: feedback imported from outside a skill-defined workflow, such as production logs, analytics, support requests, field observations, user research, competitor changes, or later maintenance pain

Do not rate the use of subagents by itself. Evaluate subagents only when they affect roles, handoffs, feedback loops, sustainment, or realization workflow.

Classify findings as:

- `gap`: a missing capability the target skill system appears to need for its declared intent
- `weakness`: an existing capability that is incomplete, unclear, hard to trigger, poorly handed off, or weakly connected to feedback
- `opportunity`: a useful improvement not required by the declared intent

Include evidence and consequence in every finding. Assign every recommendation exactly one of these actions: `create skill`, `modify skill`, `split skill`, `merge skills`, `change handoff`, `change trigger/description`, `change artifact`, `add feedback source`, or `no change`.

## Report

Unless the user specifies another location, write `skill-system-review.md` in the parent directory of the target skill system. Write the report inside the target only when the user explicitly asks for that location. Use these sections in this order:

1. `Scope`: target path, report path, included files, excluded files
2. `Declared intent`
3. `Observed behavior`
4. `Skill map`: skills, descriptions, roles, invocation style, purpose
5. `Artifact map`
6. `Handoff map`
7. `Feedback loops`
8. `Levels of work and checks`
9. `Capability ratings`
10. `Gap analysis`
11. `Recommendations`
12. `Open questions`
13. `Self-check`

## Self-check

Before delivering the report, verify that:

- Every `SKILL.md` in scope was considered or listed as excluded.
- The report states the target path and report path.
- The report maps relevant levels of work and checks.
- Every capability has a `strong`, `partial`, `weak`, or `absent` rating.
- Every finding includes evidence and consequence.
- Every recommendation uses one action from the fixed action vocabulary.
- The findings distinguish `gap`, `weakness`, and `opportunity`.
- The review did not modify the target skill system.
