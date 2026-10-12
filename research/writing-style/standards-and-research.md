# Technical-writing standards and research

Collected 15 September 2026. This note examines evidence relevant to the `writing-style` skill, especially its treatment of audience, prior knowledge, information order, plain language, concrete examples, and the proposed ideas of pace, stalls, and jumps.

## Findings in brief

The central idea of adapting writing to what a reader knows has strong support. Standards define an audience through its purpose, tasks, education, abilities, training, and experience. Government guidance likewise asks writers to account for knowledge, expertise, interest, and the action the reader needs to take. Controlled experiments show that explanatory support which helps novices can become redundant and harmful for experienced readers.

The current reader ladder has a real gap. It treats project context as the main dimension and moves from a first-time external adopter to an internal contributor. ISO/IEC/IEEE 26514 separately recognizes reference information for people who are already familiar with a product. A returning product user who wants release notes, migration guidance, or quick reference material therefore has a standards-backed place in the model even if that person knows nothing about the repository.

Information order also matters. Experiments show that relevant context given before an unfamiliar passage improves comprehension and recall far more than the same context given afterward. Research on headings shows benefits for complex text structure and text search, but little or no effect in some simple passages. Progressive disclosure is established design guidance, yet hiding content has costs. GOV.UK requires evidence before using disclosure controls and warns against hiding information that everyone needs.

The labels `pace`, `stall`, and `jump` are not standard research terms. They are useful editorial names for several supported mechanisms:

- `pace` combines the amount of unfamiliar information, the connections between ideas, and the reader's prior knowledge;
- `stall` combines true repetition, irrelevant detail, and prose that does not help the reader's task;
- `jump` combines missing context, weak coherence, and an inference that the intended reader cannot readily make.

The evidence does not establish a universal rule that every sentence must add exactly one new idea, or that every redundancy is harmful. Nor does it support brevity as an end in itself. The effect of explanation, signaling, redundancy, and even active voice changes with the reader and the task.

## Normative standards and official guidance

These sources prescribe practice. They do not, by themselves, prove that each rule improves comprehension.

### ISO 24495-1:2023, Plain language, Part 1: Governing principles and guidelines

- **Owner:** International Organization for Standardization, ISO/TC 37.
- **URL:** [ISO 24495-1:2023](https://www.iso.org/standard/78907.html) and [ISO's public restatement of its four principles](https://www.iso.org/obp/ui#iso:std:iso:24495:-4:dis:ed-1:v1:en)
- **Claim or evidence:** The standard establishes principles and guidelines for plain-language documents. Its scope explicitly includes technical writing and controlled languages, not only public-facing prose. ISO's public material for the same series restates its four principles as relevance, findability, understandability, and usability.
- **Practical implication:** Treat plain language as a test of whether the intended audience can find, understand, and use information. Do not reduce it to short words or a fixed reading level. The skill's review questions should test task completion and information retrieval as well as sentence style.
- **Limit:** The complete standard is paywalled. The public abstract establishes scope, while the four principles are also stated in ISO's public material for the ISO 24495 series.

### ISO/IEC/IEEE 26514:2022, Systems and software engineering, Design and development of information for users

- **Owner:** ISO, IEC, and IEEE.
- **URL:** [ISO Online Browsing Platform entry](https://www.iso.org/obp/ui#iso:std:iso-iec-ieee:26514:ed-1:v1:en)
- **Claim or evidence:** The standard defines an audience as users with similar characteristics and needs that determine the content, structure, and use of information. Its examples of relevant characteristics include purpose, tasks, education, abilities, training, and experience. It requires audience and task analysis as part of information architecture. It also defines reference information as quick access to details for users who are generally familiar with the product.
- **Practical implication:** Model audience on at least two independent dimensions: familiarity with the product and familiarity with its implementation. Add an experienced external user profile, or replace the single ladder with a small classification that captures both dimensions. Release notes, upgrade guides, troubleshooting pages, and reference material should not inherit the pace of first-use documentation.
- **Limit:** Most normative clauses are paywalled. The public definitions and abstract are sufficient for the claims above but not for reconstructing the standard's full process.

### ISO House Style

- **Owner:** ISO Central Secretariat.
- **URL:** [ISO House Style](https://www.iso.org/ISO-house-style.html)
- **Claim or evidence:** ISO tells standards authors to use plain language so readers can find, understand, and use information. It recommends one idea per sentence, short sentences and paragraphs, descriptive structure, lists, and simple explanations for technical terms. It also says not to assume that document users share a technical committee's knowledge. ISO permits technical terminology when the sector requires it and permits passive voice when the actor is unknown, unimportant, or not the focus.
- **Practical implication:** The skill can keep `one idea per sentence` as a drafting check, but should present it as normative guidance rather than an empirically proven law. Its active-voice guidance should remain conditional. Its strongest general rule is to explain unfamiliar terms without stripping out the vocabulary readers need for their work.

### Principles of plain language

- **Owner:** United States General Services Administration, Digital.gov.
- **URL:** [Principles of plain language](https://digital.gov/guides/plain-language/principles/overview)
- **Claim or evidence:** Federal guidance calls audience the first rule of plain language. It directs writers to consider a reader's knowledge, expertise, and interest. It explicitly rejects the idea that plain language means writing every document for an eighth-grade audience. It recommends topic sentences, active voice, advance summaries for long documents, lists, tables, and organization that prepares readers for what follows.
- **Practical implication:** Avoid defining audience only by role labels. Record what the audience knows, why they are reading, and how much detail they need. Plain language for an experienced operator can and often should use established product terminology.

### Identify user needs

- **Owner:** UK Government Digital Service, GOV.UK.
- **URL:** [Identify user needs](https://guidance.publishing.service.gov.uk/writing-to-gov-uk-standards/plan-manage-content/identify-user-needs/)
- **Claim or evidence:** GOV.UK requires every published item to meet a valid user need. Writers should use research and operational evidence to learn who users are, what they are trying to do, how they do it now, what frustrates them, and what they need from the content. User groups should be separated when their needs differ, not merely because their demographic labels differ.
- **Practical implication:** Classify a passage by the reader's task, not just the document type. A changelog can serve a returning operator deciding whether to upgrade, an adopter evaluating current maturity, and a contributor tracing implementation history. Those needs may require separate sections even though the file is one document.

### Use clear language

- **Owner:** UK Government Digital Service, GOV.UK.
- **URL:** [Use clear language](https://guidance.publishing.service.gov.uk/writing-to-gov-uk-standards/writing-guidelines/clear-language/)
- **Claim or evidence:** GOV.UK requires plain English, familiar words, explanations when specialist terms first appear, active voice in most cases, and short text chunks. It allows specialist terminology when users need it and gives exceptions where passive voice better emphasizes the result or the person affected.
- **Practical implication:** Preserve domain terms that experienced users search for. Explain a term on first use for a new audience, then use it consistently. Do not turn plain language into a ban on technical vocabulary or passive constructions.

### Darwin Information Typing Architecture version 1.3

- **Owner:** OASIS DITA Technical Committee.
- **URL:** [DITA topics](https://docs.oasis-open.org/dita/dita/v1.3/os/part2-tech-content/archSpec/base/topicover.html)
- **Claim or evidence:** DITA makes a topic, which covers one subject, the basic unit of technical content. It distinguishes concept, task, reference, troubleshooting, and other information types because they answer different reader questions. Maps can assemble those topics into different hierarchies and deliverables.
- **Practical implication:** Separating reader profiles is useful, but separating information needs is equally important. A reader may need conceptual orientation in one passage and compact reference facts in the next. The skill should classify passages by both reader and purpose rather than treating every passage for one role as having one pace.
- **Limit:** DITA is an authoring and information-architecture standard, not an experiment showing that a given topic split improves learning.

### ASD-STE100 Simplified Technical English, issue 9

- **Owner:** Aerospace, Security and Defence Industries Association of Europe, maintained by the Simplified Technical English Maintenance Group.
- **URL:** [ASD-STE100 official site](https://asd-ste100.org/)
- **Claim or evidence:** ASD-STE100 is a controlled language created for maintenance documentation read by an international workforce. Its writing rules and dictionary constrain ambiguity, complex sentence structure, synonym choice, and word meaning. The owner says the standard is for technical documentation, not general writing, though some principles can transfer.
- **Practical implication:** Use ASD-STE100 as evidence that tightly controlled wording is warranted for safety-critical procedures and multilingual maintenance contexts. Do not import its full vocabulary restrictions into general developer prose. The skill should distinguish broad plain-language advice from controlled-language rules for a specific risk profile.

### Address your audience consistently

- **Owner:** Google.
- **URL:** [Google developer documentation style guide, second person and first person](https://developers.google.com/style/person)
- **Claim or evidence:** Google tells authors to identify who `you` refers to, such as a developer or system administrator, and to keep that audience consistent. It permits imperative instructions after the addressed reader is established and distinguishes the document's reader from the end user of software that reader develops.
- **Practical implication:** The current skill is right to make audience changes visible. It should also distinguish actor roles inside a passage. `User`, `operator`, `developer`, and `administrator` can refer to different people even when one reader profile applies.

### Accordion component guidance

- **Owner:** UK Government Digital Service, GOV.UK Design System.
- **URL:** [Accordion component](https://design-system.service.gov.uk/components/accordion/)
- **Claim or evidence:** GOV.UK allows disclosure controls when research shows that users need to compare or selectively reveal related sections. It warns that hidden content may go unnoticed and must not contain information all users need. It recommends testing plain, well-structured content before adding disclosure.
- **Practical implication:** Progressive disclosure is a conditional tool, not a general instruction to hide detail. Headings, separate pages, and concise sections often provide safer layering. If the skill recommends moving expert detail behind a visible boundary, it should require that the main path remain complete.

## Empirical evidence

These sources report experiments. Most study learning materials rather than production software documentation, so the practical implications are informed transfers, not direct replications in the skill's exact setting.

### Contextual prerequisites for understanding: Some investigations of comprehension and recall

- **Researchers:** John D. Bransford and Marcia K. Johnson.
- **Source owner:** Elsevier, *Journal of Verbal Learning and Verbal Behavior*.
- **URL:** [Original paper](https://doi.org/10.1016/S0022-5371%2872%2980006-9)
- **Claim or evidence:** Across four studies, relevant contextual information supplied before an ambiguous prose passage improved comprehension ratings and recall. Supplying the same context after the passage produced much smaller gains.
- **Practical implication:** Put the minimum orienting concept before details that depend on it. This supports the skill's `jump` diagnosis and argues against postponing a needed definition until after it has already been used.
- **Limit:** Participants listened to short experimental passages. The result establishes an ordering effect, not a universal documentation template.

### Levels of expertise and instructional design

- **Researchers:** Slava Kalyuga, Paul Chandler, and John Sweller.
- **Source owner:** Human Factors and Ergonomics Society, published by SAGE.
- **URL:** [Journal article](https://journals.sagepub.com/doi/10.1518/001872098779480587)
- **Claim or evidence:** Three experiments found that less experienced learners benefited when diagrams and explanatory text were integrated. As expertise increased, removing text produced the better instructional design because the explanation had become redundant.
- **Practical implication:** This is direct support for varying detail with prior knowledge and for the skill's notion that a sentence can stall an experienced reader while bridging a gap for a novice. It also warns against one permanent `best` version of instructional content when audiences differ sharply.
- **Limit:** The experiments studied diagram-and-text instructional materials, not arbitrary sentences in software documentation. The evidence does not justify removing every repeated statement.

### Are good texts always better? Interactions of text coherence, background knowledge, and levels of understanding in learning from text

- **Researchers:** Danielle S. McNamara, Eileen Kintsch, Nancy Butler Songer, and Walter Kintsch.
- **Source owner:** Taylor & Francis, *Cognition and Instruction*.
- **URL:** [Journal article](https://www.tandfonline.com/doi/abs/10.1207/s1532690xci1401_1)
- **Claim or evidence:** Two experiments varied the coherence of biology texts. Readers with little domain knowledge benefited from coherent, explanatory text. High-knowledge readers sometimes learned more from minimally coherent text, which prompted them to generate connections from their own knowledge.
- **Practical implication:** Supplying connections is especially important for unfamiliar readers. The result also complicates a blanket rule to maximize explicitness. Experienced readers can find fully spelled-out connections redundant, though technical documentation should not intentionally become obscure merely to induce effort.
- **Limit:** The outcome depended on the measure of understanding and on learner knowledge. The study does not show that gaps are desirable in operational instructions, safety information, or quick reference material.

### The Minimal Manual

- **Researchers:** John M. Carroll, Penny L. Smith-Kerker, James R. Ford, and Sandra A. Mazur-Rimetz.
- **Source owner:** IBM Research, published in *Human-Computer Interaction*.
- **URL:** [IBM Research publication record](https://research.ibm.com/publications/the-minimal-manual)
- **Claim or evidence:** In two experiments, a shorter, task-centered manual with explicit support for recognizing and recovering from errors produced more efficient learning than a comparable commercial self-instruction manual. The design coordinated attention between the system and manual and supported later reference use.
- **Practical implication:** Brevity worked as part of a larger design: authentic action, coordination with the interface, error recovery, and later lookup. Use examples that perform a recognizable task rather than examples chosen only to display a technical property. Do not cite minimalism as evidence for deleting context without replacing its function.

### How seductive details do their damage: A theory of cognitive interest in science learning

- **Researchers:** Shannon F. Harp and Richard E. Mayer.
- **Source owner:** American Psychological Association, *Journal of Educational Psychology*.
- **URL:** [Journal article](https://doi.org/10.1037/0022-0663.90.3.414)
- **Claim or evidence:** Across four experiments, students reading science passages with interesting but irrelevant additions recalled fewer main ideas and generated fewer transfer solutions than students reading the base passages. Highlighting, objectives, or signaling did not reliably cancel the damage. Moving the additions to the end reduced some harm compared with placing them first or throughout the explanation.
- **Practical implication:** This supports cutting prose that competes with the reader's task, one form of the skill's `stall`. It also supports the user's concern about introducing a narrow units-and-errors example before the general idea is established. Early examples frame how readers interpret what follows, so the opening example should represent the full concept rather than one specialist application.
- **Limit:** An irrelevant but entertaining detail is not the same as ordinary repetition. Apply the finding to off-task material, not to every sentence a knowledgeable editor considers obvious.

### Effects of organizational signals on free recall of expository text

- **Researchers:** Robert F. Lorch Jr. and Elizabeth Pugzles Lorch.
- **Source owner:** American Psychological Association, with an author record at the University of Kentucky.
- **URL:** [University of Kentucky research record](https://scholars.uky.edu/en/publications/effects-of-organizational-signals-on-free-recall-of-expository-te/)
- **Claim or evidence:** In three experiments, headings, overviews, and summaries had no effect on free recall when the text structure was simple. With complex topic structure, signaling changed recall distribution and organization. Selective signaling could reduce recall of unsignaled content.
- **Practical implication:** Use visible boundaries when structure or audience changes make them useful. Do not add headings or summaries mechanically to a short, simple passage. A heading also directs attention, so a poorly chosen heading may demote content that still matters.

### Signaling hierarchical and sequential organization in expository text

- **Researchers:** Robert F. Lorch Jr., Julie Lemarié, and Russell A. Grant.
- **Source owner:** Taylor & Francis, *Scientific Studies of Reading*.
- **URL:** [Journal article](https://www.tandfonline.com/doi/full/10.1080/10888431003747535)
- **Claim or evidence:** Four experiments found that headings which communicated hierarchy produced more complete and accurate outlines, while headings which communicated sequence improved search speed. The heading's organizational meaning, not merely its visual presence, drove different outcomes.
- **Practical implication:** Headings should state the relationship the reader needs. A sequence needs action or stage headings; a hierarchy needs category headings. `Add a heading` is too weak as a repair for a pacing problem unless the heading exposes the missing structure.

### The passive voice and comprehensibility of biomedical texts: An experimental study with two cohorts of chiropractic students

- **Researchers:** Neil Millar and Brian S. Budgell.
- **Source owner:** *Journal of Chiropractic Education*, archived by the US National Library of Medicine.
- **URL:** [PubMed record](https://pubmed.ncbi.nlm.nih.gov/30070902/)
- **Claim or evidence:** The researchers gave 161 second-year chiropractic students active and passive versions of two biomedical methods passages. They found no significant comprehension advantage for active versions. Participants rated passive sentences as marginally more comprehensible.
- **Practical implication:** Prefer active voice when it clarifies the actor or action, but do not treat grammatical voice as an independent readability score. Context, information focus, syntax, and audience familiarity can matter more.
- **Limit:** The allocation was not randomized, the sample was specialized, and the test covered two methods passages. The result challenges a universal rule but does not show that passive voice is generally better.

## Inferences for the skill

### Audience model

The evidence favors adding an experienced external user. `Operator`, `User`, or `Returning user` would all be clearer than stretching `Adopter`. The profile would know the product's public concepts and earlier behavior, use it rather than change it, and lack repository knowledge. Likely documents include release notes, changelogs, migration guides, reference pages, troubleshooting material, and advanced how-to guides.

A stronger revision would make the current ordering less absolute. The profiles now claim to run from least to most project context, but product familiarity and implementation familiarity are independent. A returning user can know far more about behavior than a new contributor and far less about source layout. At minimum, each profile should say what kind of knowledge it assumes:

- product purpose and public vocabulary;
- prior-version behavior;
- implementation and repository layout;
- current task or conversation context.

The reader's goal should be a separate classification. DITA and GOV.UK both support task-oriented grouping. Orientation, learning, completing a procedure, looking up a fact, diagnosing a failure, evaluating a change, and modifying the system produce different information needs even for the same person.

### Pace, stalls, and jumps

Keep the labels if they help editors notice problems, but define them as review heuristics rather than established cognitive constructs.

`Pace` should mean how quickly a passage introduces unfamiliar claims and the connections needed to use them. Avoid saying that pace is simply the number of new facts per sentence. Research supports an interaction among information, structure, prior knowledge, and task, not a fixed fact-count rule.

`Stall` should be narrower than `anything the reader already knows`. Some repetition signals structure or protects against costly mistakes. A stall is material that adds no value for the intended task, such as irrelevant detail, boilerplate praise, duplicate explanation with no retrieval benefit, or history in a current-state reference page.

`Jump` maps well to missing contextual prerequisites and omitted coherence links. The useful test is whether the intended reader can make the required inference accurately and without stopping. Put indispensable context before the dependent statement. Define searchable product terms, but do not explain standard domain terms to readers who already use them.

### Opening example

The units-and-error-cases example is too narrow for the first explanation because it makes the skill look like guidance for API contracts before the general audience principle is clear. Harp and Mayer's placement results make that concern more than aesthetic: early details can determine the frame readers use for the rest of a passage.

A more generic opening should contrast the same useful fact at two context levels. For example:

> A setup guide should name the prerequisite before using it. Release notes for returning users can name the same prerequisite without explaining what it is.

Or:

> A first-time reader needs to know what a command changes. A returning reader may only need the new option and how it differs from the previous release.

These examples introduce the general mechanism, missing versus shared prior knowledge, without pulling units, exception contracts, file paths, or agent sessions into the definition.

## What the evidence does not establish

- No source found validates `pace`, `stall`, and `jump` as a named three-part model.
- The studies do not establish an ideal number of audience profiles.
- No evidence supports a universal maximum of two audiences per document. Clear separation is well supported, but the number two is a design constraint chosen by the skill.
- `One idea per sentence`, fixed sentence-length limits, and active-voice defaults are common standards guidance. Their empirical basis is less direct and more context-dependent than their wording often suggests.
- Progressive disclosure evidence from interface design does not automatically transfer to prose. Hidden documentation can reduce clutter, but it can also make required content harder to find.
- The strongest studies here concern learning and recall. Changelogs and reference pages are often used for scanning, comparison, and decision-making, so revisions should also be tested against those tasks.

## Suggested validation

After revising the skill, test it on a small set of passages rather than relying only on expert review:

1. Give first-time users and returning users separate versions of a release-note entry. Ask each group what changed, whether action is required, and where they would look next.
2. Give contributors and maintainers a handoff with and without added context. Measure time to identify the target code and the completion condition.
3. Compare the current units-and-errors opening with a generic prior-knowledge example. Ask readers to describe the skill's main rule before showing them the reader profiles.
4. Record errors and lookup time, not only preference. Several studies above show that subjective ease and measured comprehension can diverge.
