# First-party technical writing guidance from technology companies

Evidence gathered on 2026-09-15 for a future revision of the `writing-style` skill. Every source below is published by the company or project that owns the guidance. The notes separate the source's published guidance from possible lessons for the skill.

## Findings across sources

The strongest shared finding is that an audience is not adequately described by job title alone. Google treats role as a first approximation, then adds proximity to the subject and time since the reader last used the knowledge. Microsoft starts with both the audience and the outcome they want. GitHub asks who will read the content and what they are trying to do. These models support the skill's focus on prior knowledge, but they suggest that a single ladder of increasing project context is too narrow.

Several sources explicitly recognize an experienced product user who does not need internal implementation detail:

- Red Hat separates the customer lifecycle into planning, installation, everyday management, monitoring, upgrading, and troubleshooting. Each stage creates a different information need.
- GitHub writes release notes for administrators and product users who need to understand and prepare for user-facing changes.
- IBM defines release notes by their effect on a user's daily work. IBM also distinguishes release notes from tutorials, how-to content, troubleshooting, and UI text.
- AWS says release notes must help a user decide whether to install an update.
- Stripe's changelog lets an experienced API user filter changes by product and breaking status, then gives precise old-to-new API differences.

This evidence supports a public-facing profile between a new adopter and a contributor. A working name is **returning user**: someone who knows the product's public concepts and previous behaviour, wants to use or upgrade it, and neither knows nor needs repository internals. "Operator" would fit some enterprise products but is too narrow for ordinary app or library users. "Established user" is accurate but less natural.

The research did not uncover a single industry-standard list of audience archetype names. The mature systems instead combine several dimensions:

- the reader's role;
- their goal or task;
- their proximity to the subject;
- the product-lifecycle stage;
- the content type needed at that moment.

That is a synthesis from the sources, not a formal rule published by any one company.

## Source notes

### Google: Audience

- **Owner and source:** Google, [Audience, Technical Writing One](https://developers.google.com/tech-writing/one/audience).
- **Published guidance, paraphrased:** Supply the knowledge and skills readers need for their task after accounting for what they already know. Start audience analysis with the reader's role, but do not stop there. People in the same role have different knowledge. Also consider their proximity to the subject and how recently they used that knowledge. List what readers must learn, put prerequisite tasks before dependent tasks, match vocabulary to the audience, and explain more as the audience becomes less close to the project.
- **Representative example:** Google's sample audience knows C++ and a related API, but has not used the new build environment and may need a refresher on matrix multiplication. The example records knowledge topic by topic instead of assigning one global level such as "technical."
- **Possible lesson for the skill, inferred:** Keep prior knowledge as the governing idea, but describe it along explicit dimensions. A profile can say that a returning user knows public concepts and normal workflows while lacking repository structure and implementation details. The source also supports ordering an explanation by knowledge dependencies rather than adding every caveat near the start.

### Google: Documents

- **Owner and source:** Google, [Documents, Technical Writing One](https://developers.google.com/tech-writing/one/documents).
- **Published guidance, paraphrased:** State the intended audience and any prerequisite knowledge. Start a long document with the facts that answer the reader's essential questions. Relate a new idea to something the audience already understands. Before outlining, identify the audience, their goal, their current knowledge, and what they should know or be able to do afterward. Then organize the document to meet those needs.
- **Representative example:** A version introduction leads with the meaningful difference that the forecast now covers two weeks instead of one. An unchanged, lower-priority detail does not belong in the opening.
- **Possible lesson for the skill, inferred:** "Pace" includes information priority as well as sentence-level density. The skill could say that familiar baseline behaviour is useful when it makes a change legible, but a changelog should lead with the change and its effect.

### Microsoft: Content planning

- **Owner and source:** Microsoft, [Content planning, Microsoft Writing Style Guide](https://learn.microsoft.com/en-us/style-guide/content-planning).
- **Published guidance, paraphrased:** Define the audience more narrowly than a broad label such as "developers." Ask what software they build, how they work, and which tools they use. Identify what they want to accomplish, such as evaluating a purchase, learning software, solving a problem, or preparing for a migration. Choose the content form and publication channel based on that need, its urgency, and how the audience will look for help.
- **Representative example:** Microsoft's planning questions distinguish a reader deciding whether to buy from one preparing for a migration. Both are product users, but they need different facts and formats.
- **Possible lesson for the skill, inferred:** Separate prior knowledge from purpose. A returning user's familiarity does not determine whether they need a changelog, migration guide, reference page, or troubleshooting procedure. The profile should capture the likely goal without treating it as the only possible goal.

### GitHub: Best practices for GitHub Docs

- **Owner and source:** GitHub, [Best practices for GitHub Docs](https://docs.github.com/en/contributing/writing-for-github-docs/best-practices-for-github-docs).
- **Published guidance, paraphrased:** Define who will read the article and what they want to do. Give an article one or two core tasks or concepts. Move secondary material later, to another article, or remove it. Put information in priority order and in the order readers need it. Introduce one concept at a time, put the conclusion before detail, and disclose complexity later. Choose a content type such as concept, reference, how-to, troubleshooting, quickstart, or tutorial according to the audience and purpose.
- **Representative example:** A concept article explains a feature's basics and how it helps. A procedure takes the reader through one task from beginning to end.
- **Possible lesson for the skill, inferred:** The current advice to add all context the reader lacks needs a priority test. Missing information belongs at the point where the task requires it. This source also provides a generic replacement for the opening units-and-errors example: a first-time user needs the basic workflow; a returning user can skip it and go directly to what changed.

### GitHub: Style guide, release notes

- **Owner and source:** GitHub, [Style guide, release notes](https://docs.github.com/en/contributing/style-guide-and-content-model/style-guide#release-notes).
- **Published guidance, paraphrased:** Release notes cover administrator-facing or user-facing changes in a versioned product. A feature note should answer, in sequence, whether the change applies to the reader's role or access, what need it meets, what the feature does, and where to learn more. A bug-fix note should identify the affected audience and the behaviour they previously experienced. A change note may also state the problem, new behaviour, and old behaviour. Notes should omit phrases already implied by context, such as "fixed a bug" or usually "now."
- **Representative example:** GitHub's feature notes begin with a role such as site administrator or enterprise owner, state what that person can do, and link to task documentation. Its retirement pattern names the removed function and its replacement.
- **Possible lesson for the skill, inferred:** This is direct evidence for the missing returning-user profile. Such readers know the product already, so they need applicability, impact, changed behaviour, action, and links. They do not need a fresh product introduction or codebase internals.

### Red Hat: Modular documentation reference guide

- **Owner and source:** Red Hat Documentation, [Modular documentation reference guide](https://redhat-documentation.github.io/modular-docs/).
- **Published guidance, paraphrased:** Base an assembly on a real user story and the outcome the user wants. Separate concept, procedure, and reference material. Explain only user-visible concepts. Keep a procedure focused on one task, provide only prerequisites the reader might not know, and add verification or troubleshooting only when useful. Model information needs across a customer lifecycle that includes planning, installation, configuration, development, daily management, monitoring, upgrading, and troubleshooting.
- **Representative example:** Red Hat's lifecycle asks one question for established users: after the product reaches production, how does the customer customize and change it during day-to-day use? A separate stage asks how the customer upgrades to a newer version.
- **Possible lesson for the skill, inferred:** Reader profiles should cover product lifecycle, not only entry into the project and repository work. Red Hat also supports delaying prerequisites, verification, and troubleshooting until the relevant procedure instead of placing such detail in a general explanation.

### IBM: Technical Content Model

- **Owner and source:** IBM, [Technical Content Model](https://www.ibm.com/docs/en/technical-content?topic=practices-technical-content-model).
- **Published guidance, paraphrased:** IBM's content model was built from user and subject-matter research. It separates content type, content subject, packaged content item, and delivery attributes. In its research, release notes, troubleshooting, training, overviews, UI text, how-to articles, and tutorials were high-value content types. Release notes help users understand how a release affects daily product use. How-to content follows how people use a product in practice. The model tells writers to organize around what users do, rather than around all product capabilities.
- **Representative example:** The release-notes row connects "what's new" with known issues, fix lists, requirements, security bulletins, downloads, and follow-up task content.
- **Possible lesson for the skill, inferred:** A familiar external user is a first-class reader, not an edge case between adopter and contributor. The skill could map returning users to changelogs, release notes, upgrade guides, known issues, reference material, and everyday operational help.

### IBM: Progressive Disclosure

- **Owner and source:** IBM, [Progressive Disclosure](https://www.ibm.com/docs/en/technical-content?topic=practices-progressive-disclosure).
- **Published guidance, paraphrased:** Show only the detail needed at the current point, leave a clear path to more, and add detail as the user proceeds. Plan the progression from a concrete understanding of user tasks. IBM's progression moves through automatic and inline assistance, task help, tours, and full web content.
- **Representative example:** A field can offer a default first, then inline context or an example, then task help, while a full conceptual or configuration article remains available on the web.
- **Possible lesson for the skill, inferred:** The existing phrase "add context the reader lacks" should be paired with "when they need it." Progressive disclosure provides established language for the skill's idea of pace and may be clearer than the new "stall" and "jump" vocabulary on first encounter.

### Apple: Apple Style Guide

- **Owner and source:** Apple, [Apple Style Guide](https://help.apple.com/pdf/applestyleguide/en_US/apple-style-guide.pdf), June 2026 edition.
- **Published guidance, paraphrased:** Decide whether to expand an abbreviation according to audience familiarity. In user material, expand it when introduced. Put the full term before the abbreviation in most cases, but lead with the abbreviation when readers know it better. Add a pronunciation guide when readers may not know how to say it.
- **Representative example:** Apple introduces "internet service provider (ISP)" in that order, but permits a familiar abbreviation such as URL to come first.
- **Possible lesson for the skill, inferred:** Audience adaptation is often a small local decision, not a wholesale rewrite. A concrete, generic opening example could use whether to define a familiar term. That is easier to grasp than units and error handling, and it applies across documentation types.

### AWS: Writing release notes

- **Owner and source:** AWS, [AWS Marketplace Seller Guide, Writing release notes](https://docs.aws.amazon.com/pdfs/marketplace/latest/userguide/aws-marketplace-ug.pdf).
- **Published guidance, paraphrased:** Every product update needs a specific description of its changes. Release notes should help the user decide whether to install the update. Label the update clearly, including labels such as critical for security updates and important or optional for other updates.
- **Representative example:** A security update is labelled by urgency so the reader can decide whether action is required before reading implementation detail.
- **Possible lesson for the skill, inferred:** A returning user needs decision-grade change information: severity, applicability, consequences, and required action. This reinforces a profile distinct from both a first-time adopter and a repository contributor.

### Stripe: Basil API changelog

- **Owner and source:** Stripe, [Basil API changelog](https://docs.stripe.com/changelog/basil).
- **Observed documentation pattern, not a published writing rule:** The changelog starts with a summary of notable breaking changes and additions, then groups detailed entries by dated release. Each entry has a short verb-led title, affected products, a breaking or non-breaking classification, and a category. Individual entries link to fuller change details and upgrade work.
- **Representative example:** Entries distinguish a removed list-expansion capability from a newly added default value, and mark which products each change affects.
- **Possible lesson for the skill, inferred:** Experienced users benefit from a delta-first structure and filtering dimensions. They already know the baseline API. The writing should name what was added, removed, renamed, or changed, identify scope, and expose migration detail without replaying introductory material.

## Concrete changes this evidence supports

These are recommendations derived from the sources, not company rules.

1. Add **Returning user** between **Adopter** and **Contributor**.

   Suggested definition: "Knows the product's public concepts and normal workflows, but not its internals. Reads changelogs, release notes, upgrade guides, known issues, reference pages, and advanced user documentation."

2. Treat the five or six reader profiles as convenient defaults, not a complete audience-analysis method. Ask four questions before choosing one:

   - What public or internal role does the reader have?
   - What do they already know, and how recently have they used it?
   - What are they trying to decide, understand, or do?
   - Where are they in the product or project lifecycle?

3. Replace the early units-and-error-cases example with a product-neutral contrast:

   > A first-time user needs the basic workflow and definitions of unfamiliar terms. A returning user already knows that baseline and needs a precise account of what changed.

   A shorter alternative is:

   > Define an unfamiliar term for a new reader. Use it directly for a reader who already knows the product.

4. Add information order to the definition of pace. Supply context at the point where readers need it, place prerequisites before dependent tasks, lead with the conclusion or material change, and link to deeper detail.

5. Keep reader identity separate from content type. A returning user might read release notes, troubleshooting, reference, or a how-to. The document's purpose determines what facts and structure they need on that occasion.

## Source reliability and limits

- All sources are first-party. Google, Microsoft, GitHub, Red Hat, IBM, Apple, AWS, and Stripe publish the linked pages.
- Google, Microsoft, GitHub, Red Hat, Apple, and AWS state prescriptive guidance. The Stripe section records an observed first-party documentation pattern and labels it as such.
- The IBM pages report a research-backed content model but do not publish enough methodological detail on those pages to independently assess the user study.
- The proposed "returning user" name and the multi-dimensional synthesis are recommendations from this review. None of the sources publishes that exact archetype set.
