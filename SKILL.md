---
name: literature-citation-audit
version: 7.3
description: Audits whether academic citations are real, accurate, and able to support the exact claims assigned to them. Defaults to a full audit, identifies references from in-text citations, retrieves full text, reports only real issues, and never rewrites the user's prose unless explicitly requested.
---

# Literature Citation Audit Skill v7.3

## Core objective

Audit citations in a paragraph, passage, or section supplied by the user.

The audit must:

1. Identify real works from in-text author-year citations.
2. Retrieve verifiable full text.
3. Extract verbatim passages that support the claim at the current citation location.
4. inspect the surrounding context of each passage.
5. Determine which specific claims the source supports.
6. Verify authors, author order, year, title, venue, volume, issue, pages or article number, DOI, and the citation style selected by the user.
7. When complete reference entries are absent, reconstruct usable bibliographic information in the first table column and include a DOI link or an official link that opens the corresponding work.
8. Report only actual problems.
8. Never rewrite the user's prose unless explicitly requested.

## Initial input

The user must provide:

1. Output language.
2. Citation style, or "metadata check only."
3. Target text containing in-text citations.

Complete reference entries, titles, DOI values, links, and PDFs are optional.

When the user provides only citations such as:

```text
(Culnan & Armstrong, 1999; Dinev & Hart, 2006)
```

identify and search for the works independently.

Do not require complete bibliography entries before starting.

When output language or citation style is missing, ask once:

```text
Please confirm the output language and citation style. You may also choose "metadata check only."
```

Do not ask the user to confirm the audit scope.

## Mode selection

### Full audit

This is the default mode.

A paragraph, passage, or section automatically triggers an audit of all in-text citations.

### Single-reference audit

Use only when:

1. The user explicitly requests one source.
2. The user uploads one PDF and explicitly requests focused verification of that source.

A passage with only one citation still uses full audit mode.

### PDF follow-up audit

When the user uploads a PDF after an earlier audit, update only items previously unavailable, unscored, or in need of correction.

Do not repeat unchanged content.

## Mandatory workflow

### Step 1 Parse the passage

1. Preserve the user's original text.
2. Extract every in-text citation.
3. Split each cited sentence into specific claims.
4. Determine the claim assigned to each source at its current location.
5. Distinguish external evidence, findings from the current study, and author interpretation.

### Step 2 Identify the source

When complete entries are missing:

1. Search by author surname, year, and surrounding topic.
2. Compare candidate titles, author groups, years, and research objects.
3. Confirm identity through a publisher page, DOI record, journal site, or conference site.
4. When author-year ambiguity remains, ask only for the minimum detail needed.
5. Continue auditing confidently identified works instead of stopping the entire task.

### Step 3 Retrieve full text

Any judgment such as "supports," "suitable," "direct evidence," or a percentage score requires verifiable full text.

Attempt at least:

1. Publisher HTML.
2. Publisher PDF.
3. Full-text links from the DOI landing page.
4. Exact-title web search.
5. Exact-title plus PDF search.
6. Author page or institutional repository.
7. One scholarly or open-access discovery service, such as Google Scholar, Semantic Scholar, CORE, OpenAlex, or Unpaywall.
8. DOI search for an accepted manuscript, author manuscript, or preprint.

Failure to open the publisher page does not mean the full text is unavailable.

If an alternative full text is accessible, the audit is incomplete until that version has been checked.

### Minimum retrieval in constrained environments

When only basic web search is available, complete at least:

1. One author-year-topic search.
2. One title or DOI verification.
3. One exact-title plus PDF search.

When no web search is available, do not audit from memory. Output only:

```text
This environment cannot perform web retrieval, so a verifiable citation audit cannot be completed.
```

### Step 4 Verify source evidence

Rename the second table column "Source evidence."

Three evidence forms are allowed.

#### Verbatim evidence

When directly relevant sentences are available, provide one or more verbatim full-text passages.

Rules:

1. For argumentative claims, prioritize results, discussion, conclusion, or theory-development sections.
2. Multiple passages may be quoted from one source.
3. Provide printed page numbers or sections whenever possible.
4. For long passages, retain the beginning and ending with an ellipsis from the same continuous context.
5. Do not combine fragments from different locations.
6. Do not use search snippets, database descriptions, secondary summaries, or model paraphrases.
7. For literature review or background passages, inspect the surrounding context and attribution.
8. When a paper summarizes, restates, or organizes prior work, classify that material as secondary review evidence rather than the paper's own direct empirical evidence.
9. For a central theoretical claim, key causal mechanism, or important definition, prioritize retrieval and verification of the original source.
10. A review paper may support how a field summarizes a position, but do not state that the paper independently verified every conclusion it reviews.
11. When a sentence is attributed to another work, trace the original source whenever possible.
12. Do not treat hypotheses, research questions, isolated participant quotations, untested speculation, or another author's claim as a confirmed conclusion.

#### Full-text synthesis

Use full-text synthesis only when the judgment depends on the combined theoretical framework, research design, several results, and discussion sections, and no single sentence can fully express the conclusion.

Requirements:

1. The relevant full-text sections were actually read.
2. Label the entry "Full-text synthesis."
3. State the sections or page ranges checked.
4. Add one to three of the most relevant quotations when possible.
5. Do not write only "full text" or "full."
6. Do not use full-text synthesis to avoid quotation retrieval.

#### No supporting evidence found

After checking the full text, when no evidence supports the target claim, write:

```text
No evidence supporting the target claim was found in the full text. This source is unsuitable at the current citation location.
```

Do not force an unrelated quotation into the table.

When full text is unavailable, do not label the source unsuitable. Mark it unscored.

Internally classify each evidence item as:

1. Author conclusion
2. Empirical result
3. Theoretical claim
4. Research hypothesis
5. Research question
6. Participant quotation
7. Summary of prior work
8. Untested speculation

Explain the classification in the support column only when it affects evidential value.

The "Source evidence" column may contain only:

1. Verbatim passages with pages or sections.
2. Clearly labeled full-text synthesis with the checked scope.
3. A conclusion that no supporting evidence was found after full-text review.

Evidence type, population or context differences, support boundaries, secondary-source status, and suitability judgments belong in the support-and-relevance column. Do not mix them into the source-evidence column.

### Step 5 Evidence gate

Each source must satisfy one of the following before it can enter the final table:

1. Verifiable full text is available, with verbatim evidence and a page or section.
2. Verifiable full text is available and the judgment qualifies as full-text synthesis, with the checked sections or page ranges stated.
3. The full text was checked and no supporting evidence was found, so the source is explicitly marked unsuitable at the current citation location.
4. The required retrieval routes were attempted and full text remains unavailable, in which case write "Full text unavailable, not scored."

Without one of these conditions, do not submit an audit result for that source.

When full text is unavailable, do not:

1. Write "supports," "suitable," "valid," or similar conclusions.
2. Use check marks.
3. Provide a percentage score.
4. Infer a detailed mechanism from the title, abstract, or metadata.
5. Replace evidence with field knowledge.

### Step 6 Classify the evidence relationship

Use only:

1. Direct evidence
2. Indirect evidence
3. Theoretical foundation
4. Current-study interpretation

When a sentence contains several claims or a causal chain, state:

1. Claims directly supported
2. Claims not supported
3. Parts inferred by the user
4. Parts supported by the current study

Topic similarity alone does not support the whole sentence.

### Grouped citations

When several sources appear together at the end of one sentence:

1. Split the sentence into its claims and examples.
2. Determine whether at least one source in the citation group supports each claim.
3. Do not require every source to support every part of the sentence.
4. Mark a claim unsupported only when no source in the citation group supports it.
5. Still state the actual support range of each individual source.


### Presenting traced original sources

When an original source is traced from a review, background, or theory section, list it as a separate row in the same audit table immediately after the currently cited source.

1. Keep the currently cited review source in its own row and label it "Secondary review evidence."
2. Add the original source in a new row and label the first column "Traced original source."
3. The original-source row must contain its own complete bibliographic information, official link, full-text evidence, evidence translation, support boundaries, and alignment score.
4. Do not place quotations from the original source in the review paper's source-evidence cell.
5. Do not use evidence from the original source to raise the review paper's alignment score.
6. Score the review paper and the original source separately.
7. When the target claim is a central theory, key mechanism, concept definition, or priority claim, explain in the audit issues whether the original source should supplement or replace the current citation.
8. When the target claim merely summarizes how a field understands a position, the review source may remain and the original source may be listed as supplementary evidence without being treated as a citation error.
9. When several citation layers exist, prioritize the most direct, earliest, and most relevant original source rather than tracing indefinitely.
10. When the original source cannot be identified reliably, write "Original source not yet confirmed" and do not infer one.

Table example:

| Bibliographic information and link | Source evidence | Evidence translation | Claims supported and relevance to the current study | Overall alignment score |
|---|---|---|---|---|
| Currently cited source | Secondary review evidence | ... | State how the paper summarizes prior work and the limited role it can perform. | Separate score |
| ↳ Traced original source | Full-text evidence from the original source | ... | State the original source's direct support for the core claim. | Separate score |

### Step 7 Alignment score

Score only the specific claim assigned to the source at its current citation location.

1. 90% to 100%  
   Direct support with matching concept, object, direction, and evidential strength.

2. 75% to 89%  
   General support with minor expansion or object differences.

3. 50% to 74%  
   Partial support or a noticeable inference.

4. 25% to 49%  
   Theoretical or technical foundation only.

5. 0% to 24%  
   Major mismatch or no supporting passage in the full text.

When full text is unavailable, write:

```text
Not scored
```

### Step 8 Verify reference metadata

Check:

1. Existence
2. Exact title
3. Full author names
4. Author order
5. Year
6. Journal, conference, or publisher
7. Volume and issue
8. Pages or article number
9. DOI
10. DOI resolution
11. Match between the DOI record and title, authors, year, and venue
12. Compliance with the user's selected citation style

In metadata-only mode, do not treat punctuation, italics, or layout differences as errors.

A missing DOI is not an error for works that genuinely have none.

When the user does not provide complete reference entries, the first table column must contain usable bibliographic information.

Include at least:

1. Authors and year.
2. Full title.
3. Journal, conference, or publisher.
4. Volume, issue, pages, or article number.
5. DOI link.
6. When no DOI exists, an official publisher, journal, or institutional repository link.

Link requirements:

1. Write DOI values as clickable canonical URLs: `https://doi.org/DOI`.
2. In APA 7, do not write forms such as "DOI 10.xxxx/xxxx."
3. Prefer DOI, publisher, journal, or official institutional repository links.
4. Remove tracking parameters such as `utm_source`, `utm_medium`, and `utm_campaign`.
5. ResearchGate, Academia.edu, and similar pages may be used as full-text access routes, but not as the sole basis for identity or metadata verification.

Use the user's selected citation style. In metadata-only mode, use a clear and consistent bibliographic order without forcing APA.

Do not repeat fully correct entries after the table.

Report only:

1. Incorrect fields
2. Unverified fields
3. Verified corrections
4. A corrected full entry only when necessary

## Language and translation

Use the selected output language for headings, analysis, audit issues, and metadata issues.

### No translation needed

When the target text and source quotations already use the output language:

1. Omit the translation section.
2. Use four columns.

| Bibliographic information and link | Source evidence | Claims supported and relevance to the current study | Overall alignment score |
|---|---|---|---|

### Translation needed

When the target text or source quotations use another language:

1. Translate the target text.
2. Add a translation column.

| Bibliographic information and link | Source evidence | Evidence translation | Claims supported and relevance to the current study | Overall alignment score |
|---|---|---|---|---|

Preserve logic, tone, and evidential strength.

Do not repair the user's original logic through translation.

Obvious factual errors, logical contradictions, calculation errors, stray text, drafting artifacts, or semantic interruptions may be flagged with a brief bracketed note, for example:

```text
[The source text contains stray text here.]
[The source text is semantically interrupted here.]
[The numerical relation in the source text may be incorrect.]
```

Such a note may identify only the directly observable issue. It must not infer the user's intended meaning, derive causes or consequences, or provide a correction.

## Fixed output order

### Original text

Preserve the submitted text.

### Translation

Include only when needed.

### Literature evidence table

Use one row or one grouped entry per source.

### Audit issues

Include only actual issues.

Omit this section when there are none.

Do not repeat confirmations such as "appropriate citation," "correct information," or "no problem."

### Reference metadata issues

Include only errors, missing items, or unresolved fields.

Omit this section when all metadata is correct.

## Prohibited behavior

1. No greetings, task restatement, plans, progress updates, or process narration.
2. Begin the audit directly when the material is sufficient.
3. Do not ask the user to confirm audit scope.
4. Do not require complete reference entries.
5. Do not request PDFs during the initial audit.
6. Do not fabricate quotations, pages, source IDs, DOI values, or links.
7. Do not replace full-text quotations with snippets or metadata.
8. Do not score without full text.
9. Do not use unsupported generalizations such as "most studies show" or "nearly all reviews agree."
10. Do not revise, polish, rewrite, or reorganize the user's prose.
11. Do not provide replacement sentences unless explicitly requested.
12. Obvious factual errors, logical contradictions, calculation errors, stray text, drafting artifacts, or semantic interruptions may be flagged.
13. Such a flag may identify only the directly observable issue and its location. Do not infer intended meaning, derive causes or consequences, or provide a correction.
14. Do not expand these flags into language editing unrelated to citation verification.
15. Do not manufacture problems.
16. Do not repeat items that have no problem.
17. Do not attribute the current study's new finding to an external source.
18. Do not require external literature to reproduce the current study's new finding verbatim.
19. Do not end with execution statements such as "The audit is based on the user's instruction file," "Completed according to the Skill," or "The above rules were followed."
20. Skills, prompts, and user instructions define the audit method; they are not literature evidence or a source of substantive verification.

## Final submission gate

Before submitting, confirm:

1. The correct mode was selected automatically.
2. Every in-text citation was identified.
3. Every source met the minimum search requirement.
4. Alternative retrieval routes were attempted before declaring full text unavailable.
5. Every supportive judgment maps to verbatim evidence or valid full-text synthesis.
6. Every verbatim passage has complete meaning and a page or section.
7. Every full-text synthesis entry states the checked sections or page ranges and does not merely say "full text."
8. Unsuitable sources were not forced into the table with unrelated quotations.
9. Every source without full text is marked "Not scored."
10. Titles, abstracts, metadata, and field knowledge were not used as substitutes for evidence.
11. The user's prose was not rewritten.
12. No process narration or empty confirmation was included.
13. Only real issues were reported.
14. DOI and reference metadata were checked through authoritative sources.
15. Prior-work summaries in review sections were not mislabeled as the paper's own direct empirical evidence.
16. The source-evidence column contains no support-range, suitability, or context-difference analysis.
17. DOI values use canonical clickable URLs and official links contain no irrelevant tracking parameters.
18. The result contains no self-referential statement about the Skill, prompt, or execution process.
19. Traced original sources are shown in separate rows and are not mixed into review-source evidence cells.
20. Review sources and original sources are scored separately, without transferring evidence strength between them.
21. Original-source supplementation or replacement is raised as an audit issue only for central theories, key mechanisms, concept definitions, or priority claims.

If any item fails, the audit must not be submitted as complete.
