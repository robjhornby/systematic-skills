# Writing-style research synthesis

## Decision this research informs

The `writing-style` skill needs a reader profile for someone who knows the product's public behavior but not its implementation. The revision should also replace the opening units-and-error-cases example with a general example of prior knowledge.

This note proposes the shape of that revision. It does not change the published skill.

## What the evidence supports

| Finding | Evidence strength | Consequence for the skill |
| --- | --- | --- |
| Writers should account for what readers know and what they need to do. | Strong agreement across ISO/IEC/IEEE 26514, DITA, government guidance, company guides, and experiments. | Keep prior knowledge as the skill's central principle. Add the reader's goal as a separate question. |
| Product familiarity and repository familiarity are independent. | Explicit in DITA's separate audience dimensions and Google's role/proximity guidance; reinforced by release-note practice. | Add an experienced external reader. Remove the claim that all profiles form one least-to-most ladder of project context. |
| Needed context should appear before information that depends on it. | Direct experimental support from Bransford and Johnson, plus prescriptive support from Google and GitHub. | Keep the idea behind a `jump`, but define it as a missing prerequisite or connection for the intended reader. |
| Detail useful to a novice can burden an expert. | Direct experimental support from expertise-reversal studies and broad prescriptive support. | Keep audience-specific pacing. Do not call every repetition a stall because some repetition aids retrieval or prevents costly mistakes. |
| Information should be ordered by the reader's task and disclosed when needed. | Strong prescriptive agreement; conditional support for headings and progressive disclosure. | Add information order to `pace`. Do not imply that all missing context belongs near the start. |
| Release notes serve experienced external users. | Explicit first-party guidance and patterns from GitHub, IBM, AWS, and Stripe. | The new profile should name applicability, changed behavior, effect, required action, and migration detail while omitting repository internals. |

The detailed support and source limits are in [standards-and-research.md](standards-and-research.md), [company-style-guides.md](company-style-guides.md), and [audience-archetypes.md](audience-archetypes.md).

## What remains a house style choice

The research did not establish these rules as universal findings:

- `pace`, `stall`, and `jump` are useful editorial labels, not standard constructs from technical-writing research.
- No source sets two as the maximum number of audiences for one document.
- One idea per sentence and active voice are common standards guidance, but both need exceptions.
- No established source supplies the skill's complete set of reader archetypes.

The skill can keep these rules when they make editing faster. It should phrase them as operating heuristics and avoid implying that research discovered the exact taxonomy or thresholds.

## Audience-model options

### Option A: add one profile

Add an experienced external reader between `Adopter` and `Contributor`. Remove only the sentence that calls the profiles a single scale.

This is the smallest useful change. It fixes the reported gap but leaves the profiles mixing roles, knowledge, tasks, and communication state.

### Option B: add one profile and make the dimensions explicit

Add the profile, then define every profile with the same fields:

- relationship to the product or repository;
- assumed public-product knowledge;
- assumed repository and implementation knowledge;
- assumed task-conversation knowledge;
- current goal and typical documents.

This is the recommended option. It preserves fast profile selection while fixing the false linear model. It also makes future disagreements diagnosable. For example, an expert product user can be a novice repository contributor.

### Option C: replace profiles with a matrix

Ask writers to classify role, experience, goal, and information type separately, following DITA and the broader source consensus.

This has the strongest conceptual foundation but would make a lightweight editing skill slower to apply. The profiles currently work as shortcuts for recurring agentic-coding situations, so a full matrix would probably cost more than it returns.

## Name options for the missing reader

| Name | Advantage | Problem |
| --- | --- | --- |
| `Returning user` | Makes the contrast with `Adopter` and the changelog use case immediately clear. | A person returning after a long absence may no longer know the baseline. |
| `Experienced user` | Plain and directly matches DITA's separate user and experience concepts. | Two words, and experience needs a boundary. |
| `Practitioner` | Fits the existing one-word noun pattern and implies repeated use without internal access. | Sounds professional and is less immediately obvious. |
| `Product user` | Clearly separates public use from repository contribution. | Too broad unless the definition excludes new users. |

`Returning user` is the best label for the reported problem because a skill user can infer it without reading a new term's definition. The definition, not the label, should guard against the lapse problem:

> **Returning user.** Knows the product's public concepts and previous behavior, but not its internals. Reads changelogs, release notes, migration guides, how-to guides, and reference documentation.

`Experienced user` is the best alternative if the name should align more closely with standards terminology.

## Proposed replacement for the opening

The current opening introduces units and error cases before it has established the general audience principle. It frames the skill as API-contract guidance and asks the reader to interpret two specialist examples at once.

A direct replacement is:

> The **pace** of a passage depends on how much of its subject the reader already knows and what they need to do next. A first-time user needs the basic workflow and definitions of unfamiliar terms. A returning user already knows that baseline and needs a precise account of what changed. A file path can orient an agent starting a fresh session but repeats context for a colleague who has followed the work.

A shorter replacement, if the new profile has not yet been introduced, is:

> The **pace** of a passage depends on how much of its subject the reader already knows and what they need to do next. Define an unfamiliar term for a new reader. Use it directly for a reader who already knows the product.

The first version is better if the revision adds `Returning user` in the same change. It makes the missing profile do useful explanatory work immediately.

## Other examples worth simplifying

The units theme recurs in the Adopter example, and the Executor example introduces naive datetimes, time zones, daylight-saving transitions, exceptions, and `fold=0`. Each example is locally valid, but together they make a general writing skill feel specialized.

Possible replacements:

### Adopter

Ineffective:

> A powerful and flexible tool that makes previewing your work a breeze.

Effective:

> Preview Markdown files in a browser. The page reloads when you save the file.

This still demonstrates the difference between promotional adjectives and concrete behavior without requiring a library or domain concept.

### Executor

Ineffective:

> Add the output option we discussed to the status command.

Effective:

> Add `--json` to the `status` command in `src/cli/status.ts`. With the flag, print the same fields as the table using the existing API response names. Keep table output as the default. Add tests for both formats.

This demonstrates searchable vocabulary, scope, settled behavior, compatibility, and completion criteria without making error handling the focus.

### Maintainer

Ineffective:

```python
# Sort the jobs by creation time.
```

Effective:

```python
# Workers retry from the front of the queue, so keep the oldest job first.
```

This demonstrates the difference between translating code and recording a reason the code cannot express.

## Recommended next work session

Run one bounded Build session to revise `SKILL.md` and `READERS.md`:

1. Use option B and the label `Returning user`, unless the label is the one unsettled choice.
2. Replace the opening with the first proposed version.
3. Add a Returning user section with release-note and changelog examples.
4. Replace the Adopter, Executor, and Maintainer examples with simpler domains.
5. Refine the definitions of `pace`, `stall`, and `jump` to match the evidence limits.
6. Decide explicitly whether to retain the two-audience maximum as a house constraint or soften it to guidance about separating distinct needs.
7. Validate the skill, review the rendered Markdown, and compare the revised examples as a set.

That session should not expand into a general rewrite. The evidence supports the central prior-knowledge idea. The work is to repair the audience gap, improve information order, and keep the skill's memorable heuristics honest about their status.
