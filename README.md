# Systematic Skills

Systematic Skills helps coding agents keep a project moving across sessions. The `work` skill completes one manageable task at a time, records what changed, and leaves a current status for the next session. It can call on your other installed skills for research, design, implementation, review, and maintenance.

The skills follow the [Agent Skills specification](https://agentskills.io/specification) and work with Claude Code, Codex, and other compatible agents.

## Install

The [`skills`](https://skills.sh/) CLI installs skills into a project by default. Add `--global` to either command to make them available in every project.

Install every skill in this repository for every detected agent:

```sh
npx skills@latest add robjhornby/systematic-skills --all
```

Or launch the interactive installer and choose the skills and agents:

```sh
npx skills@latest add robjhornby/systematic-skills
```

### Update

Update every installed skill at the scope you choose:

```sh
npx skills@latest update
```

The update command refreshes installed skills. If a later release adds a skill, run the installation command again to install it.

## Start a project

Invoke `work` using your agent's skill syntax, such as `/work`. On its first run in a project, `work` creates two files at the repository root:

- `STATUS.md` holds the current direction, active work, external dependencies, and parked work.
- `LOG.md` records observations, decisions, and completed results in chronological order.

The setup run stops after creating the project record. Invoke `work` again to choose and complete a task, or name the task when you invoke it.

Each later `work` session reads the current status, agrees on one task with a clear completion condition, does the work, and updates both files. If choosing the task consumes most of the useful session context, it writes a handoff for a fresh session instead of starting the task with too little room left.

## What `work` pays attention to

`work` classifies project activity into six areas so repeated implementation work does not hide missing research, verification, or feedback:

| Area | Question |
| --- | --- |
| Problem | What need are we addressing, for whom, and with what evidence? |
| Shape | What should change, what are its boundaries, and what should it work with? |
| Build | What implementation is ready to complete? |
| Prove | How will we check the completed work? |
| Field | What did real use, support, or production reveal? |
| Upkeep | What repeated friction or drift is making future work harder? |

The area guides `work` toward an appropriate installed skill. For example, a Shape task may use a research or design skill, while a Prove task may use tests, review, or direct use.

The six areas adapt [Product Systems Engineering](https://sebokwiki.org/wiki/Product_Systems_Engineering) to ordinary project work. They keep the problem, surrounding systems, alternatives, real use, and long-term maintenance visible alongside implementation.

## Included skills

| Skill | Use it when |
| --- | --- |
| [`work`](skills/work/SKILL.md) | A project spans several agent sessions and you want to complete one task without losing its direction or history. |
| [`maintain-project-record`](skills/maintain-project-record/SKILL.md) | Work happened outside a `work` session and the project's existing status and log need to reflect the result. |
| [`writing-style`](skills/writing-style/SKILL.md) | You want technical prose paced for its intended reader and stripped of repetition or missing context. |
| [`skill-system-review`](skills/skill-system-review/SKILL.md) | You want to assess how a collection of agent skills works as a system before changing it. |
