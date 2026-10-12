---
name: writing-style
description: "Technical writing guidance based on the reader's prior knowledge and goal. Use it for comments, docstrings, READMEs, contributor docs, specs, tickets, commit messages, and chat replies, or when prose is vague, bloated, repetitive, or hard to follow."
license: MIT
---

# Writing style

Give readers information at a rate they can understand, according to target audience profiles.

The skill uses the concept of **pace**, meaning the amount of new knowledge added by each piece of text in a passage. The right pace depends on the reader's prior knowledge and next action to determine the level of detail, what topics to focus on, and in what order. For example, a first-time user needs a basic introduction to a subject and its terminology. A returning user knows the basics and either wants a concise reference or a detailed account of any changes.

Before writing or revising a passage, identify the intended reader. Determine the reader's prior knowledge and next action. Choose the closest match among the profiles defined below. Each section of a document may have a different target reader. A prose explanation and its code sample may also target different readers. Classify each piece of text separately.

## The six readers

- **Adopter.** Adopters have no product or repository context. They read READMEs and user documentation to decide whether to engage with a project or product and learn about its features.
- **Returning user.** Returning users know the product's public concepts and previous behavior but not the internal implementation. They read changelogs, release notes, migration guides, how-to guides, and reference documentation.
- **Contributor.** Contributors know the language and tools but need an introduction to the repository. They read contribution guides, developer documentation, and ADRs before changing the repository.
- **Executor.** Executors, often agents, know the codebase but have no context from the conversation that produced the task. They use specs, tickets, plans, prompts, and fresh-session handoffs to complete the work.
- **Maintainer.** Maintainers can access the relevant code. They read comments, docstrings, commit messages, and log lines while changing the code.
- **Peer.** Peers know the codebase and the current conversations and ongoing work. They read chat replies, review comments, and handoffs while continuing work with current participants.

After choosing a profile, read the corresponding section in [READERS.md](READERS.md). Each section defines the profile's prior knowledge, required information, and examples of ineffective and effective passages.

## Set the pace

Add context the reader lacks. Define a term before using it in an argument. Put each prerequisite before the step that requires it. Give information immediately before the reader needs it. Explain the constraint behind a rule. Add a small example when prose leaves a boundary unclear.

Remove context the reader already knows. Use an established domain term without redefining it. Name a familiar file instead of describing its purpose. State a settled decision without replaying the preceding discussion.

## Separate sections by reader

A document may serve readers with different prior knowledge and goals. For example, a README can introduce the project to adopters and include a setup section for contributors. Choose the target reader for each section. Change the assumed reader at a visible boundary, such as a heading or code fence. If the assumed reader changes inside a paragraph, it's not possible to write with a pacing that suits both target audiences.

When readers need the same information, write the information once for the reader with less prior knowledge. A knowledgeable reader can skim a familiar definition. A new reader cannot recover a missing definition.

If differences in prior knowledge or goals make the document hard to navigate, split the document or add a clearly labeled section for each reader.

## Find stalls and jumps

The skill uses **stall** as an editorial label for a sentence that gives the intended reader no useful new information. The label does not make all repetition a problem. Repetition can help readers find information or prevent a costly mistake. A stall usually has one of these forms:

- A sentence repeats nearby material. For example, a comment translates the next line into English or a reply restates the request.
- A sentence could appear unchanged in any project. "This module is designed for flexibility and maintainability" gives no project-specific information.

The skill uses **jump** as an editorial label for an omitted prerequisite or connection. A jump usually has one of these forms:

- A reference has no identifiable antecedent. "Move it into the shared file" does not identify the item or the file.
- A clause contains two ideas but omits the logical or causal connection between the ideas.
- An argument uses a new term before defining the term.

Revise in this order:

1. Identify the intended reader before changing any words.
2. Mark every stall and jump.
3. Cut stalls and add the prerequisites or connections omitted by jumps.

Do not shorten a passage at the expense of required context. Readers can skim a redundant sentence.

## Write explicit sentences

Choose a subject that fits the fact. Use a person or running program as the subject when its action matters: "The editor removes repeated claims". For stored information, describe its state or contents: "The guide contains the installation steps". Attribute a claim to a document with "According to the release notes, the option is available in version 2.0". In instructions, address the reader: "Write the reason for the decision in the ticket".

Keep words that readers must connect close together. An anaphoric pronoun such as "it," "this," or "they" gets its meaning from an antecedent. Use a pronoun when a nearby noun phrase is the only plausible antecedent. Repeat the noun phrase when another antecedent is possible or when an embedded clause separates the pronoun from the antecedent.

State conditions and results in separate clauses: "If a link is broken, the site build fails". When the actor matters, state its action: "The link checker fails the build when it finds a broken link". Use passive voice when the actor is unknown or irrelevant: "The broken link is reported in CI".

Prefer literal descriptions of states and actions to spatial or mechanical shorthand. Use "The review is posted" for a review's status and "The reviewer posts the review" when the reviewer matters.

Introduce a category before listing its attributes. Keep the items in a list grammatically parallel:

> Definitions of six reader profiles for technical writing: their prior knowledge, the information they need, and examples of ineffective and effective passages.

The example begins with a concrete category and follows the category with three parallel noun phrases. Readers can scan the parallel noun phrases more easily than several abstract clauses beginning with "what".

Use a complete sentence unless a heading, label, or short description makes the missing verb obvious. Split a sentence when readers must look backward to find the subject or connect the clauses.

## Use a factual voice

State the behavior, invariant, or result. Omit praise, suspense, claims of importance, and announcements about what the next section will cover.

Describe behavior and properties directly. Use contrast when the difference is the point, such as a trade-off between two options or an invariant that readers often reverse. In other cases, state the correct fact directly. After a correction, replace the old explanation instead of recounting the reason for the correction.

Avoid the stock "X, not Y" construction. State X alone when it conveys the point. When a comparison matters, vary the sentence structure and explain the difference.

Describe the current state unless the document records change. Changelogs record history, specs describe future work, and dated logs record events. Other documents should omit migration history, former behavior, planned replacements, and progress reports.

Choose claims that remain useful as the work changes. Describe behavior or coverage at the level the reader needs. In a PR description, "Tests cover the new retry logic" remains accurate if more tests are added. State a goal as a goal: "The project aims for short build times to support quick iteration".

Use a measured result when the value helps the reader assess a decision or outcome. Give the method, input, environment, and date or revision so the result is tied to the run that produced it. Use past tense for that run: "On 12 October 2026, `scripts/benchmark.sh` measured 8% lower runtime for the example case after the change than before it on an M3 Mac with 16 GB of memory".

Prefer plain words. Write "use" instead of "utilize" and "help" instead of "facilitate". Use active voice when the reader needs to know who acts, and passive voice when the result matters more. Replace an adverb and weak verb with a precise verb.

Use sentence case headings, straight quotes, no emoji, and commas or full stops instead of em dashes.

## Check the passage

Before finishing a passage, answer these questions:

- Which reader profile applies, and what does that reader already know?
- What must the reader do next, and does the information appear before the required action?
- Which sentences repeat known information?
- Which sentences require missing context?
- Could any paragraph appear unchanged in another project's documentation?
- Does each claim help the reader, and can it remain accurate through routine edits? If a measurement matters, can the reader find how and when it was obtained?
- Does each causal sentence state the condition and result, or identify the actor and its action?
- Could a literal noun or verb replace any shorthand metaphor?
