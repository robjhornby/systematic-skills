# Audience archetypes for technical writing

Research question: which established audience models can inform the reader profiles in the `writing-style` skill, especially the missing reader who already uses a product, does not need its internals, and reads release notes to understand changes?

Sources were checked on 2026-09-15. The source notes below report what the sources say. The synthesis and recommendations are interpretations for this skill.

## Short answer

No established model maps cleanly onto `Adopter`, the missing returning product user, `Contributor`, `Executor`, `Maintainer`, and `Peer` as a single ordered scale.

The closest standards-based model is DITA's audience metadata. It treats audience type, current job, and experience level as separate dimensions. Google's technical-writing course adds proximity to the subject and time since exposure. Diátaxis classifies the reader's immediate need instead of the reader. These models suggest that the current profiles combine several variables:

- relationship to the product, such as prospective user, product user, or code contributor;
- familiarity with the product, repository, and current conversation;
- the task the reader is doing;
- the kind of information needed at that moment.

The missing reader is well established in the sources as an experienced product user or end user. GitHub explicitly names end users who use release notes to understand and prepare for new functionality. DITA can represent the reader as `type=user`, `job=using` or `migrating`, and `experiencelevel=general` or `expert`.

## Source findings

### DITA separates role, task, and experience

The OASIS DITA 1.3 specification defines three independent attributes for an intended audience:

- `type` describes the kind of person. Its sample values include `user`, `purchaser`, `administrator`, `programmer`, and `executive`.
- `job` describes the high-level task. Its sample values include `installing`, `customizing`, `programming`, `using`, `maintaining`, `troubleshooting`, `evaluating`, `planning`, and `migrating`.
- `experiencelevel` describes assumed experience. Its sample values are `novice`, `general`, and `expert`.

DITA also says that different audiences can read the same topic for different tasks, and that the experience expected from a programmer can differ from that expected from a user. Since DITA 1.2, the values are extensible rather than limited to the samples. [OASIS DITA 1.3, audience element, pages 256–257](https://docs.oasis-open.org/dita/dita/v1.3/os/part1-base/dita-v1.3-os-part1-base.pdf)

This is direct evidence against treating role and experience as one ladder. `user` and `programmer` are roles, while `novice` and `expert` are experience levels. A person can be an expert product user and a novice contributor to its repository.

### Google uses role, proximity, and elapsed time

Google's Technical Writing course says to begin audience definition with roles, but warns that roles alone are insufficient. Writers should also consider the reader's proximity to the knowledge. The course distinguishes familiarity with a related project from familiarity with the project being documented. It also notes that knowledge fades when people have not used it for some time. Its working formula is that documentation should supply the knowledge and skills needed for a task minus the audience's current knowledge and skills. [Google, "Audience"](https://developers.google.com/tech-writing/one/audience)

Google's guidance for document introductions says an audience declaration can name a role, prerequisite knowledge or experience, and required prior reading. [Google, "Documents"](https://developers.google.com/tech-writing/one/documents)

The role-proximity-time model supports a returning-user profile directly. Such a reader has high proximity to the public product and low proximity to its implementation. Neither fact implies the other.

### Diátaxis classifies needs, not stable personas

Diátaxis identifies four documentation forms from two questions. Content can support action or cognition, and it can support skill acquisition or skill application. The resulting forms are tutorial, how-to guide, reference, and explanation. [Diátaxis, "The compass"](https://diataxis.fr/compass/)

Diátaxis also says users do not move through these forms in a fixed sequence. A user can enter the documentation anywhere, and the content they want changes from moment to moment. [Diátaxis, "The map"](https://diataxis.fr/map/)

Diátaxis therefore complements an audience profile but does not replace it. The same experienced product user might consult reference while working, read an explanation to understand a changed design, or follow a how-to guide to adopt a new feature.

### Microsoft starts with audience and purpose

Microsoft's content-planning guidance asks writers to identify both the audience and what that audience wants to accomplish. Its examples distinguish deciding whether to buy a product, learning software, preparing for migration, troubleshooting, and receiving timely news or announcements. It maps those needs to different content forms. [Microsoft Writing Style Guide, "Content planning"](https://learn.microsoft.com/en-us/style-guide/content-planning)

This guidance recognizes evaluating, using, migrating, and keeping current as separate needs. It does not provide a reusable set of named software-documentation personas.

### GitHub describes the missing release-note reader explicitly

GitHub says release notes help readers understand and prepare for user-facing changes. It names two audiences: administrators planning controlled upgrades and end users preparing to use new features and functionality. [GitHub Docs, "Release note content type"](https://docs.github.com/en/contributing/style-guide-and-content-model/release-note-content-type)

GitHub's release-note guidance starts feature, behavior-change, retirement, and known-issue notes by asking whether the change applies to the reader's role or access. For a behavior change, it asks for the new behavior and, when relevant, the previous behavior. [GitHub Docs, "Style guide", release notes](https://docs.github.com/en/contributing/style-guide-and-content-model/style-guide#release-notes)

This reader matches the requested gap closely. They already understand the product well enough for a comparison with prior behavior to be useful. They need user-visible effects, applicability, actions, compatibility information, and migration guidance. They do not need repository structure or implementation rationale unless it changes how they use the product.

### GitHub's general model separates audience, goal, and content type

GitHub tells authors to identify who will read the content and what they are trying to do, then select a content type. Its content types include concepts, reference, how-to, troubleshooting, quickstart, and tutorial. It also recommends progressive disclosure, with basic information before details. [GitHub Docs, "Best practices for GitHub Docs"](https://docs.github.com/en/contributing/writing-for-github-docs/best-practices-for-github-docs)

Like Diátaxis, this is a model of needs and content forms rather than a fixed list of reader archetypes.

### Evidence-based personas are local to a product

The UK Government Service Manual says personas or user profiles should group people with similar behavior and needs. It treats suggestions not grounded in user research as assumptions to test. [GOV.UK Service Manual, "Learning about users and their needs"](https://www.gov.uk/service-manual/user-research/start-by-learning-user-needs)

The Office for National Statistics publishes four research-derived personas: expert analysts, information foragers, inquiring citizens, and technical users. It says these personas differ in knowledge and tasks. The information-forager persona keeps up with recent data, follows methodology changes, wants confidence that it has the latest information, and dislikes unnecessary technical tools or jargon. [ONS Service Manual, "User personas"](https://service-manual.ons.gov.uk/content/writing-for-users/user-personas)

The ONS information forager is a useful domain-specific analogue for the missing reader. It is not a suitable generic name, but it shows that an informed returning user who tracks changes without wanting implementation detail is a real, research-derived pattern.

### General expertise ladders cover only one axis

The Dreyfus and Dreyfus model describes five stages of skill acquisition: novice, competence, proficiency, expertise, and mastery. The original report concerns learning a skill through instruction and experience, not relationships to a software project or document types. [Dreyfus and Dreyfus, *A Five-Stage Model of the Mental Activities Involved in Directed Skill Acquisition*](https://apps.dtic.mil/sti/pdfs/ADA084551.pdf)

An expertise ladder can refine a product-user profile, but it cannot distinguish an expert user from a novice repository contributor. DITA's separate experience field is more directly applicable to documentation metadata.

## Comparison with the current profiles

The mappings in this section are interpretations, not labels used verbatim by the sources.

| Current or proposed profile | DITA approximation | Google proximity | Common need or content | Fit |
| --- | --- | --- | --- | --- |
| Adopter | purchaser or user; evaluating, installing, or learning; novice | Low product and repository proximity | Overview, tutorial, initial setup | Reasonably clean, though the current definition combines evaluation and first use. |
| Returning product user | user; using, troubleshooting, or migrating; general or expert | High public-product proximity, low implementation proximity | Release notes, how-to, reference, migration guidance | Clear gap in the current skill and directly supported by GitHub's release-note audience. |
| Contributor | programmer; programming or customizing; novice or general repository experience | Technical skill may be high, repository proximity low | Contribution guide, developer setup, architecture introduction | Reasonably clean once product experience and repository experience are kept separate. |
| Executor | No standard equivalent; often programmer with an assigned implementation task | High repository proximity, low conversation proximity | Ticket, spec, plan, handoff | A workflow-specific profile created for agentic coding, not a general documentation persona. |
| Maintainer | programmer or administrator; maintaining or troubleshooting; expert | High repository and implementation proximity | Comments, docstrings, commits, logs | Reasonably clean, though DITA's `maintaining` is a task and not necessarily a stable person. |
| Peer | No standard equivalent | High repository and conversation proximity | Review comment, current-session handoff, chat | A communication-context state, not a conventional product role. |

The six profiles can still be useful as shortcuts. They should not be presented as a pure progression from least to most project knowledge. `Adopter`, returning product user, and `Contributor` branch by relationship to the product, while `Executor`, `Maintainer`, and `Peer` add repository and conversation context.

## Names for the missing profile

### Practitioner

`Practitioner` is the strongest fit with the existing noun-based names. It implies active, repeated use without implying access to internals. It also leaves room for noncommercial tools and libraries, where `customer` would be wrong. Its drawback is a faint suggestion of professional or advanced use. The definition must say that product familiarity, not occupational status, is the criterion.

### Experienced user

`Experienced user` is the clearest and has direct support from DITA's user-plus-experience model. Readers will understand it without learning a new term. Its drawbacks are that it breaks the one-word naming pattern and that "experienced" needs a boundary. In this skill, the boundary could be "knows the product's public concepts and prior behavior, but not its internals".

### Returning user

`Returning user` makes the contrast with `Adopter` immediately visible and fits changelogs well. It does not necessarily mean experienced, though. Someone returning after one failed trial or after years away may need adopter-paced material. Google explicitly notes that time since exposure changes what a reader knows, so the name can misclassify readers.

### Product user

`Product user` is neutral and accurately separates use from contribution. DITA's `user` type and GitHub's `end user` language support it. The name is broad enough to include first-time adopters, however, so it only works if the definition adds established familiarity. Microsoft also advises choosing a more specific noun than `user` when possible, though it permits `user` when distinguishing a technology user from a developer or administrator. [Microsoft Writing Style Guide, "user, end user"](https://learn.microsoft.com/en-us/style-guide/a-z-word-list-term-collections/u/user-end-user)

## Recommendation for the skill

Add `Practitioner` between `Adopter` and `Contributor`, but stop describing the complete list as a single scale of project context.

A compact definition could be:

> **Practitioner.** Knows the product's public concepts and prior behavior, but not its internals. Reads changelogs, release notes, migration guides, how-to guides, and reference documentation.

The detailed profile should tell writers to assume established public terminology, compare new behavior with prior behavior when the document records change, state who is affected, and name any action the user must take. It should exclude repository paths, internal design history, and implementation details unless those facts affect use.

For a later structural revision, define every profile with the same fields:

- relationship to the product or repository;
- assumed prior knowledge;
- current goal;
- missing context the passage must supply;
- typical documents.

This keeps the profiles quick to apply while adopting the main lesson shared by DITA, Google, GitHub, Microsoft, and Diátaxis: role, experience, task, and information need are related but not interchangeable.
