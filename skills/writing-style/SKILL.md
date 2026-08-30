---
name: writing-style
description: "Technical writing guidance based on the reader's prior knowledge. Use it for comments, docstrings, READMEs, contributor docs, specs, tickets, commit messages, and chat replies, or when prose is vague, bloated, repetitive, or hard to follow."
license: MIT
---

# Writing style

Write at a pace the reader can follow.

The **pace** of a passage is the amount of new knowledge each sentence asks the reader to absorb. Each sentence should add one idea that connects to the reader's prior knowledge. The right pace depends on the reader. Units and error cases help someone editing the code but may distract someone deciding whether to install it. A file path can orient an agent starting a fresh session but repeats context for a colleague who has followed the work.

Before writing or revising a passage, identify its reader. Determine what that reader already knows and what the passage must help them do next. Choose the closest of the five profiles below. Classify passages separately because prose and code samples in the same document can address different readers.

## The five readers

The profiles run from the least project context to the most.

- **Adopter.** Knows neither the project nor its internal terms. Reads READMEs and user documentation.
- **Contributor.** Knows the language and tools but not this repository. Reads contribution guides, developer documentation, and ADRs.
- **Executor.** Knows the codebase but not the conversation that produced the task. Reads specs, tickets, plans, prompts, and handoffs to a fresh session.
- **Maintainer.** Has the relevant code in view. Reads comments, docstrings, commit messages, and log lines.
- **Peer.** Knows the codebase and the conversation. Reads chat replies, review comments, and handoffs between current participants.

After choosing a profile, read its section in [READERS.md](READERS.md). Each section defines the reader's prior knowledge, the information they need, and examples of ineffective and effective passages.

## Set the pace

Add context the reader lacks. Define a term on first use, put the unit beside the number, explain the constraint behind a rule, and add a small example when prose leaves a boundary unclear.

Remove context the reader already has. Use an established domain term without redefining it. Name a familiar file instead of describing its purpose. State a settled decision without replaying the discussion that produced it.

## Address at most two readers

A document may need two paces. For example, a README can introduce the project to adopters and include a separate setup section for contributors. Give each reader a continuous section under a clear heading. Change pace only at a visible boundary, such as a heading or code fence. A mid-paragraph change makes one reader wade through known material while another must infer missing context.

When both readers need the same information, write it once for the reader with less context. A knowledgeable reader can skim a familiar definition; a new reader cannot recover a missing one.

If a document addresses more than two reader profiles, suggest splitting it. If it must remain one document, separate the profiles with clear sections.

## Find stalls and jumps

A **stall** gives the reader no useful new information. Stalls usually take one of these forms:

- It repeats nearby material, such as a comment that translates the next line into English or a reply that restates the request.
- It could appear unchanged in any project, such as "This module is designed for flexibility and maintainability."
- It names an impression instead of a mechanism. Replace "queries stay fast" with a measured claim such as "a query over 10,000 rows returns in under 50 ms."

A **jump** requires knowledge the reader does not have. Jumps usually take one of these forms:

- It leaves a reference ambiguous. "Needing a router change means the design drifted" does not identify the router, the change, or the design.
- It compresses two ideas into one clause and omits the words that connect them.
- It uses a new term as part of the argument before defining it.

Revise in this order:

1. Identify the intended reader before changing any words.
2. Mark every stall and jump.
3. Cut stalls and supply the context needed to bridge jumps.

Do not pursue brevity by itself. Readers can skim a redundant sentence, but missing context forces them to stop and reconstruct the argument.

## Write explicit sentences

Name the subject of each sentence. State how it relates to the rest of the sentence. Prefer concrete nouns such as "prior knowledge," "required information," and "example" to metaphors such as "what the reader holds" or "what moves them."

Introduce a category before listing its attributes. Keep the items in a list grammatically parallel:

> Definitions of five audience profiles for technical writing: their prior knowledge, the information they need, and examples of ineffective and effective passages.

This structure gives the reader a concrete category followed by three noun phrases that describe it. It is easier to scan than a fragment made from several abstract "what" clauses.

Use a complete sentence unless a heading, label, or short description makes the missing verb obvious. If a sentence makes the reader backtrack to find its subject or connect its clauses, split it.

## Use a factual voice

State the behaviour, invariant, or result. Omit praise, suspense, claims of importance, and announcements about what the next section will cover.

Explain what a thing is. Use contrast only when the difference is the point, such as a trade-off between two options or an invariant that readers often reverse. Otherwise, state the correct fact directly. After a correction, replace the old explanation instead of recounting why it was wrong.

Describe the current state unless the document records change. Changelogs record history, specs describe future work, and dated logs record events. Other documents should omit migration history, former behaviour, planned replacements, and progress reports.

Replace vague qualifiers with quantities when measurements exist. Replace "the tank may be full soon" with "the level sensor reads 95%, within its 2% accuracy range." State the uncertainty in the measurement instead of hedging the whole sentence.

Prefer plain words and active voice. Write "use" instead of "utilize," "help" instead of "facilitate," and "the loader parses the file" instead of "the file is parsed." Name the actor. Replace an adverb and weak verb with a precise verb or a measurement.

Use sentence case headings, straight quotes, no emoji, and commas or full stops instead of em dashes.

## Check the passage

Before finishing a passage, answer these questions:

- Which reader profile applies, and what does that reader already know?
- Which sentences repeat known information?
- Which sentences require missing context?
- Could any paragraph appear unchanged in another project's documentation?
- Does every "it," "this," and "that change" have one clear referent?
