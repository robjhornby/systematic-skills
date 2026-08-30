# Contributing

This repository publishes portable agent skills that follow the [Agent Skills specification](https://agentskills.io/specification). Contributors need Node.js 22 to run the same validation used by CI.

## Repository structure

Each published skill has one directory under `skills/`:

```text
skills/
  skill-name/
    SKILL.md          # required metadata and instructions
    agents/           # optional client-specific metadata
    scripts/          # optional executable helpers
    references/       # optional on-demand documentation
    assets/           # optional templates and other resources
```

Keep portable instructions and the metadata allowed by the shared specification in `SKILL.md`. Put client-specific behavior in a client-owned file such as `agents/openai.yaml`.

## Writing style

Use [`skills/writing-style/SKILL.md`](skills/writing-style/SKILL.md) when writing or revising repository prose. Choose the intended reader before editing, then read that reader's section in [`skills/writing-style/READERS.md`](skills/writing-style/READERS.md).

Keep each document focused on its reader:

- `README.md` is for adopters deciding whether to install the skills and learning how to use them.
- `CONTRIBUTING.md` is for contributors changing this repository.
- Skill instructions are for the agent that will execute them. Supply the context that agent cannot infer from the target project.

## Validate changes

Run the same reference validator as CI against every skill:

```sh
for skill in skills/*; do
  test -d "$skill" || continue
  npx --yes skills-ref@0.1.5 validate "$skill"
done
```

Then check which skills the installer discovers:

```sh
npx skills@latest add . --list
```

Review the rendered Markdown and the final diff before submitting the change. CI runs the reference validator on pull requests and pushes to `main`.
