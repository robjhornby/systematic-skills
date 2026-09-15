# The six readers

This guide defines six recurring reader profiles for technical writing. The profiles combine the reader's relationship to the work, public product knowledge, repository knowledge, and task conversation knowledge. Each profile also names the reader's goal and typical documents.

The profiles describe common situations rather than exclusive roles. A returning user who starts contributing code may fit the Returning user profile for release notes and the Contributor profile for repository setup. Choose a profile for each section according to the assumed knowledge and required action.

| Profile | Relationship and goal | Public product knowledge | Repository knowledge | Task conversation knowledge | Typical documents |
| --- | --- | --- | --- | --- | --- |
| Adopter | Prospective user deciding whether to adopt and learning the basic workflow | None assumed | None assumed | None assumed | READMEs, getting-started guides, user documentation |
| Returning user | Current or previous user deciding whether a change applies and what to do | Established public concepts and previous behavior | None assumed | None assumed | Changelogs, release notes, migration guides, how-to guides, reference documentation |
| Contributor | Repository participant preparing to change the project | None assumed | Knows the language and tools, but is new to the repository | None assumed | Contribution guides, developer documentation, ADRs |
| Executor | Repository participant completing a scoped task | Depends on the task | Knows the codebase | None from the discussion that produced the task | Specs, tickets, plans, prompts, fresh-session handoffs |
| Maintainer | Person changing an implementation without violating its contracts | Varies by implementation | Can access the relevant code | None assumed | Comments, docstrings, commit messages, log lines |
| Peer | Current participant continuing shared work | Knows the same public behavior as the writer | Knows the codebase | Knows the current conversation | Chat replies, review comments, current-session handoffs |

## Adopter

Adopters decide whether to use the project and learn the basic workflow. They read READMEs and user documentation.

Adopters have no product or repository context. Define internal terms on first use and explain the product's purpose before explaining the implementation. Tell adopters the product's purpose, prerequisites, installation steps, and first command. Use concrete claims instead of promotional adjectives.

The first description could apply to any library:

```
A powerful and flexible tool that makes previewing your work a breeze.
```

The revised description names the workflow and visible behavior:

```
Preview Markdown files in a browser. The page reloads when you save the file.
```

## Returning user

Returning users need to determine whether a change applies and which action the change requires. Returning users know the product's public concepts and previous behavior. Give brief recaps of familiar concepts, and describe changes without requiring knowledge of repository internals.

State the affected versions or configurations, the changed public behavior, the effect of the change, and any required action. Put migration details immediately before the step that requires those details. A returning user may have skipped releases, so name the relevant previous behavior.

The first release note neither defines the change nor tells the reader what to do:

```
The configuration loader has been improved. Update your configuration as needed.
```

The revised release note states the old behavior, new behavior, affected users, and required action:

```
Version 2.0 rejects unknown keys in `project.toml`. Version 1.x ignored them.
Before upgrading, run `tool config check` and remove each key reported as
`unknown`.
```

## Contributor

Contributors use contribution guides, developer documentation, and ADRs to learn how to change the repository correctly.

Contributors know the language and tools but need an introduction to this repository. Give contributors details they cannot infer, including commands, required checks, conventions that tools do not enforce, and reasons for unexpected rules. Do not repeat information that a tool displays at the point of failure.

The first instruction does not define the standard or required action:

```
Before opening a pull request, ensure your code meets our quality standards
and follows best practices.
```

The revised instruction names the command and explains the relationship to CI:

```
Run `make check` before opening a pull request. The command runs the same checks as CI.
```

## Executor

Executors act on instructions without access to the conversation that produced the instructions. They read specs, tickets, plans, prompts, and handoffs to a fresh session.

Executors know the codebase and can inspect its contents. They still need enough information to locate the work and determine whether the result meets the acceptance criteria. Name modules, interfaces, constraints, and acceptance criteria in the project's searchable vocabulary. Describe the required change without recounting the preceding discussion or rejected options. Follow any required document structure.

An agent starting a new session is an executor. Restate terms coined in conversation and identify agreed files by path. A human colleague who participated in the work is a peer.

The first handoff omits the context needed to execute the request:

```
Add the output option we discussed to the status command.
```

The revised handoff identifies the interface, scope, settled behavior, compatibility requirement, and completion criteria:

```
Add `--json` to the `status` command in `src/cli/status.ts`. When `--json` is present,
print the same fields as the table using the existing API response names. Keep
table output as the default. Add tests for both formats.
```

## Maintainer

Maintainers read comments, docstrings, commit messages, and log lines while changing the related code.

Maintainers can access all relevant code. Restating the code in prose slows them down. Use prose for information that the code cannot express, including the reason for a design choice, domain invariants, units, ranges, coordinate spaces, ownership, lifetime, ordering requirements, performance bounds, and error behavior that affects callers.

A public API docstring defines the API contract. State accepted inputs and units, the meaning of the return value, clamping or normalization, mutation, absence, and error cases.

Names should carry information that code can express. If a comment only translates an identifier into English, rename the identifier and delete the comment.

The first comment restates the next line:

```python
# Sort the jobs by creation time.
jobs.sort(key=lambda job: job.created_at)
```

The revised comment records the ordering constraint that the code cannot express:

```python
# Workers retry from the front of the queue, so keep the oldest job first.
jobs.sort(key=lambda job: job.created_at)
```

## Peer

Peers know the codebase and the conversation. They read chat replies, review comments, and handoffs between people who participated in the work.

Peers already know the request and the work completed during the current conversation. Start the reply with new information, such as the result or a point that still needs discussion.

Shared knowledge does not remove the need for precise references. A repository may contain two files named `config.py`. Name the relevant path, such as `src/cli/config.py`, instead of writing "the config file."

This reply leaves the cause and change ambiguous:

```
Fixed it. The design had drifted, which is why the change was needed.
```

This reply identifies both the cause and the change:

```
`save_report` wrote every report to `report.txt`, so each run replaced the
previous report. The function now includes the report date in the filename.
```
