---
name: literature-citation-audit
description: Audits whether academic citations are real, accurate, and aligned with the claims they support. Adapts the output language and translation structure to the user's preference, verifies full-text quotations, evaluates claim-level evidence, checks alignment, and validates reference metadata. The default task is verification only, with no rewriting.
---

# Literature Citation Audit Skill

## Purpose

Audit academic paragraphs, target sentences, and references supplied by the user. Confirm the following points.

1. Whether each cited work actually exists.
2. Whether the source text supports the specific claim assigned to the citation at its current location.
3. Whether external evidence, findings from the current study, and the author's interpretation are clearly distinguished.
4. Whether the citation logic, causal strength, and conceptual scope are accurate.
5. Whether the reference metadata is ready for direct use in an academic reference list.

This task is for verification by default. Do not rewrite, polish, restructure, or provide replacement sentences unless the user explicitly asks for revision.

## Language setup and user intake

Before the first audit, determine the user's required output language.

1. If the user explicitly names an output language, use it.
2. If the user has not named one, ask one concise question:
   "What language should I use for the audit output?"
3. In the same message, provide the user intake template so the user knows what material to submit.
4. Wait for the user to confirm the language and provide the material before beginning the audit.
5. If the user has already supplied both the language requirement and enough material, begin directly and do not ask again.
6. Use the selected output language for all headings, table analysis, audit issues, metadata issues, and explanatory text.

### Translation decision

Translation is conditional.

1. If the user's target text and the quoted source passages are already in the selected output language, omit translation.
2. When translation is unnecessary, omit both the separate translation section and the translation column in the evidence table.
3. If the target text or source passages are in a different language, translate them into the selected output language.
4. When the material is mixed-language, translate only the parts that differ from the selected output language.
5. Include a translation column only when at least one quoted source passage requires translation.
6. If the selected output language is English and all audited material is already in English, use English throughout and provide no translation section or translation column.
7. If the selected output language is Chinese, Korean, Japanese, or another language, translate all material that is not already in that language and conduct the audit in the selected language.

### Material requested from the user

Ask the user to provide the following.

Required:

1. Output language.
2. Citation style or reference-format requirement, such as APA 7, Chicago, Harvard, IEEE, Vancouver, a journal-specific style, a custom institutional style, or "metadata check only."
3. The exact paragraph, passage, or section to be audited, including all in-text citations.

The audit scope is inferred automatically.

- A submitted paragraph, passage, or section enters full audit mode by default.
- Single-reference mode is used only when the user explicitly requests it or uploads one PDF for focused verification of that source.
- PDF supplementary mode is used when a PDF is supplied after an earlier audit or when the user asks to update an earlier result.

Full reference entries are optional.

When the user provides only in-text citations such as "(Culnan & Armstrong, 1999; Dinev & Hart, 2006)," independently identify and locate the cited works using the available author names, years, surrounding claims, DOI records, publisher pages, databases, and full-text sources.

Do not require the user to provide complete reference entries before starting.

If several works share the same author-year pattern or the citation cannot be identified reliably, report the ambiguity and request only the minimum additional detail needed.

Optional but useful:

1. Any reference information the user already has, such as a title, DOI, URL, journal, conference, or full reference entry.
2. The exact sentence or passage from the cited source that the user believes supports the claim. This helps locate the relevant context but does not replace independent verification.
3. A previous audit result when the task is a PDF follow-up.

Do not request a PDF for the initial audit. Search first. Request a PDF only when the full text cannot be accessed or verified.

## Audit modes

Select the mode automatically from the material the user provides.

### Full audit mode

This is the default mode.

Use it whenever the user submits a paragraph, passage, or section containing one or more in-text citations, even when no full reference entries are provided.

Do not ask the user to confirm the audit scope in this situation.

Output in this order.

1. Original text
2. Translation, only when required by the selected output language
3. Literature evidence table, using the four-column or five-column layout as appropriate
4. Audit issues, including only actual problems
5. Reference metadata issues, including only errors or items that remain unverified

### Single-reference audit mode

Use this mode only when the user explicitly asks to check one source, one citation, or one specific reference, or when the user uploads a single PDF specifically for focused verification of that source.

Do not switch to this mode merely because the paragraph contains only one citation.

Requirements:

1. Retain only the target sentence associated with that reference. Translate it only when it differs from the selected output language.
2. Include only the target reference in the table.
3. Evaluate only the specific claim that the reference is expected to support at its current citation location.
4. Do not recheck other references in the same paragraph that have already been confirmed.
5. Report only problems concerning the target reference.

### PDF supplementary audit mode

Use this mode when the user uploads a PDF after an initial audit or asks to update an earlier result.

Requirements:

1. Update only items previously marked as unavailable, unverified, unscored, or in need of correction.
2. Add verifiable quotations, page numbers, contextual classification, alignment scores, and corrected metadata.
3. Do not repeat the full paragraph, all references, or unchanged findings.
4. If the PDF changes an earlier judgment, state what changed and identify the supporting evidence.
5. Recheck the source using the actual PDF content. Do not preserve conclusions that were previously based on incomplete evidence.

## Original text and conditional translation

### Original text

Reproduce the user's target paragraph or sentence exactly. Only repair obvious line-break artifacts caused by copying. Do not rewrite the wording.

### Translation, when required

Include this section only when the target text is not already in the selected output language.

Requirements:

1. Preserve the original logical relations, degree of certainty, and causal strength.
2. Use established terminology from the relevant discipline.
3. Do not insert interpretation, criticism, or corrections into the translation.
4. Translate quotations faithfully without strengthening or weakening them.
5. Do not silently repair logical problems in the original sentence.
6. Translate into the output language confirmed by the user.
7. Omit this section entirely when the target text is already in that language.

## Literature evidence table

Choose the table layout according to the language rule.

### Layout without translation

Use this four-column layout when all quoted source passages are already in the selected output language.

| Reference title and authors | Verbatim source passages | Claims supported and relevance to the current study | Overall alignment score |
|---|---|---|---|

### Layout with translation

Use this five-column layout when at least one quoted source passage is not in the selected output language.

| Reference title and authors | Verbatim source passages | Translation into the selected output language | Claims supported and relevance to the current study | Overall alignment score |
|---|---|---|---|---|

### First column

Provide the full title, authors, and year.

Example:

*Article Title*, Author A, Author B, & Author C, 2020

### Second column

Include only verbatim passages that can be located in the source itself.

Follow all rules below.

1. Prioritize the full text. Do not rely only on the abstract.
2. Preserve the exact wording. Do not paraphrase, summarize, or add commentary.
3. A single source may include multiple quotations when several passages jointly support the target claim.
4. Keep each quotation semantically intact and provide its page number or section whenever possible.
5. For argumentative claims, prioritize the results, discussion, conclusion, or the section where the theory is formally developed.
6. When using a sentence from the literature review, background, or theoretical overview, inspect the surrounding context.
7. Confirm that the statement is accepted, adopted, synthesized, or explicitly advanced by the authors.
8. If the sentence is explicitly attributed to another source, trace and audit the original source whenever possible.
9. Treat the current paper as the main supporting source only when it synthesizes, extends, or explicitly adopts the idea as part of its own framework.
10. Do not treat a passage as an established author conclusion when it merely summarizes prior research, presents a dispute, introduces an opposing view, states a research question, states a hypothesis, or raises an untested possibility.
11. Participant quotations may illustrate a reported finding, but one participant statement cannot independently represent the author's overall conclusion.
12. Do not use search snippets, database descriptions, summaries written by other papers, or model-generated text as source quotations.
13. When a passage is too long, retain the beginning and ending with an ellipsis. Both parts must come from the same continuous context, and the omission must not change the meaning.
14. Do not combine fragments from different locations into a single apparent quotation.
15. Page numbers must come from the PDF or the page numbering printed in the article.
16. When PDF sequence numbers and printed page numbers differ, prefer the printed page number and add the PDF page number only when useful.
17. If the full text is unavailable, write:
   "No verifiable full text is currently available, so a full-text quotation cannot yet be provided. Please upload the PDF for supplementary verification."
18. If the full text is available but no passage directly supports the target claim, write:
   "No passage directly supporting this claim was found in the full text."
19. Do not place phrases such as "the authors argue," "the study shows," or "this indicates" in this column.

### Translation column, when used

Add this column only when at least one source passage differs from the selected output language.

Requirements:

1. Maintain a one-to-one correspondence with the quoted passages.
2. Do not add interpretation.
3. Preserve ellipses when the source column uses them.
4. Preserve the evidential strength of the original wording.
5. Translate into the output language confirmed by the user.
6. For mixed-language evidence, mark passages already in the output language as "No translation needed" or leave the corresponding cell segment unchanged.

### Fourth column

Assess the specific claim assigned to the reference at its current citation location.

When the target sentence contains several propositions or a causal chain, split it into separate claims before judging support.

Use the following structure when relevant.

1. Claims directly supported
2. Claims indirectly supported
3. Parts for which the source provides only theoretical or technical grounding
4. Claims not supported
5. Parts supported by findings from the current study
6. Parts that remain the author's interpretation of the current study

Classify the evidence relationship using the following four categories.

#### Direct evidence

The source explicitly states the target claim. The population, concept, direction of the relationship, and evidential strength are consistent with the cited sentence.

#### Indirect evidence

The study findings can reasonably support the target claim, but the source does not use the same formulation, or the claim requires a limited inference.

#### Theoretical foundation

The source supplies a concept, mechanism, or technical basis. The user still derives the present conclusion from the user's own findings.

#### Current-study interpretation

This part must be supported by the user's own experiment, interviews, statistical analysis, or coding. External literature may provide an interpretive framework.

Check all of the following.

1. Whether one concept has been substituted for another.
2. Whether the population or research object has been broadened.
3. Whether an association has been written as causation.
4. Whether a specific emotion has been generalized to all negative emotions.
5. Whether a coping strategy has been expanded into a claim about behavioral intensity or extremity.
6. Whether a theory is applied beyond its original scope.
7. Whether a finding from the user's study has been incorrectly attributed to an external source.
8. Whether consistency with a theory has been written as proof by that theory.
9. Whether support for one link in a causal chain has been treated as support for the entire chain.

### Fifth column

The alignment score must correspond to the specific claim assigned to the reference at its current citation location. Do not score the general thematic similarity of the whole paragraph.

If the target sentence contains multiple propositions, split them first and then calculate the overall score for the citation's actual role.

Use the following guide.

1. 90% to 100%
   The source directly supports the central claim. The concepts, population, direction, and evidential strength are substantially consistent.

2. 75% to 89%
   The source generally supports the central claim, with minor conceptual expansion, population differences, or wording differences.

3. 50% to 74%
   The source supports only part of the claim or requires a noticeable inference. There is a clear expansion of scope, concept substitution, or causal strengthening.

4. 25% to 49%
   The source provides only theoretical or technical grounding and does not directly support the main claim assigned to the citation.

5. 0% to 24%
   The source is largely mismatched with the target claim, or no supporting evidence can be found in the full text.

Additional rules:

1. Calculate the score according to the claim assigned to the citation at its current location.
2. Do not raise the score merely because the topic is related.
3. Do not lower the score merely to appear strict.
4. Do not provide a percentage when no verifiable full text is available.
5. An abstract may confirm the research topic, population, and results explicitly reported in the abstract.
6. An abstract cannot confirm a detailed theoretical proposition, mechanism, or degree of wording used only in the body text.
7. When the full text is unavailable, write "Not scored pending full-text verification."
8. When only the title is available, write "Topic appears relevant; full text still requires verification."

## Context classification of quotations

For every quotation, identify its contextual status during the internal audit.

Available classifications:

1. Author conclusion
2. Empirical result
3. Theoretical claim
4. Research hypothesis
5. Research question
6. Participant quotation
7. Summary of prior research
8. Untested speculation

Do not place this classification in the verbatim quotation column.

When the classification affects evidential value, explain it briefly in the fourth column.

Do not treat a hypothesis, research question, isolated participant statement, another author's claim, or untested speculation as a confirmed conclusion of the current source.

## Findings from the user's own study

When the target paragraph interprets the user's experiment, interviews, or statistical results, distinguish the following.

1. Facts supported by the current study.
2. Mechanisms for which external literature provides theoretical grounding.
3. Connections that remain the author's interpretation.
4. New findings that constitute the contribution of the current study.

Do not require external literature to reproduce the user's new finding in full.

Do not attribute the user's new finding to an external source.

When an external source provides a suitable theoretical basis for a mechanism, do not reject it solely because it does not repeat the user's result verbatim.

## Audit issues

After the table, report only actual problems that require attention.

Omit all items that have no problem.

If the entire passage has no issue, omit this section.

Check only logical errors, principled errors, and problems that could affect academic credibility.

Possible issues include:

1. Whether the reference is suitable at the current citation location.
2. Whether it supports the central claim.
3. Whether there is concept substitution, scope expansion, causal strengthening, or object mismatch.
4. Whether citation placement is clear.
5. Which parts come from external literature.
6. Which parts come from the current study.
7. Which parts are the author's interpretation.
8. Which parts require support from the user's experiment, interviews, or coding.
9. Whether the wording is stronger than the evidence permits.
10. Whether the original source or a more suitable source is needed.

For excessive evidential strength, identify only the wording that is too strong and state the maximum level of support available from the source.

Do not provide a revised sentence.

## Identifying references from in-text citations

When complete bibliography entries are absent, reconstruct them from the in-text citations.

1. Search by author surname and publication year first.
2. Use the surrounding claim and research topic to distinguish among works with similar author-year combinations.
3. Confirm the final match through an authoritative source before treating it as identified.
4. Prefer publisher pages, DOI records, journal or conference websites, official repositories, and the full text.
5. Do not select a work merely because its title appears thematically related.
6. When identification remains ambiguous, list the plausible candidates and ask for the minimum missing information.
7. Continue auditing references that have been identified confidently while leaving only the ambiguous items pending.

## Reference metadata verification

Check every reference for the following.

1. Existence of the work.
2. Exact title.
3. Full and accurate author names.
4. Correct author order.
5. Publication year.
6. Journal, conference, or publisher name.
7. Volume and issue.
8. Page range or article number.
9. DOI accuracy.
10. DOI resolution.
11. Whether the DOI resolves to the cited work.
12. Whether the supplied link matches the cited work.
13. Compliance with the citation style or reference format selected by the user.

Use the following internal statuses.

1. Verified
2. Error found
3. Not yet verifiable

Mark an item as verified only when it is confirmed through a publisher page, DOI registration record, journal website, official conference page, or the full text itself.

If an authoritative source does not confirm an item, mark it as not yet verifiable. Do not complete it by convention or guesswork.

In the final output, list only items marked "Error found" or "Not yet verifiable."

If the user does not specify a citation style, ask for one before the first audit. The user may select "metadata check only." In that mode, verify bibliographic accuracy but do not treat formatting differences as errors.

Do not repeat metadata for references that are fully correct.

### DOI verification rules

Confirm at least the following five points.

1. The DOI resolves successfully.
2. The resolved title matches the cited title.
3. The first author or author group matches.
4. The publication year matches.
5. The journal, conference, or publisher matches.

Treat the DOI as incorrect when it resolves to a preprint, correction notice, book review, dataset, or a different work with a similar title.

The absence of a DOI is not an error for books, early publications, reports, and conference papers that genuinely have no DOI.

Depending on the document type, provide a publisher page, ISBN, persistent database record, or institutional repository link.

### Output for metadata issues

When a discrepancy exists, include only the following.

1. Field containing the problem
2. User's original entry
3. Verified information
4. Correct DOI or official link
5. Corrected full reference entry in the citation style selected by the user, only when formatting correction is requested or required

When the user selects "metadata check only," do not generate a reformatted reference merely because its punctuation or layout follows a different style.

A corrected reference entry applies only to the bibliography. It does not authorize rewriting the user's prose.

## Citation traceability

1. Every file or webpage citation must use a source identifier actually returned by the current tool.
2. Do not invent file numbers, page numbers, source IDs, or URLs.
3. Page numbers for quotations must come from the PDF or article.
4. When PDF sequence and printed pagination differ, prefer printed pagination and add PDF sequence only when useful.
5. Do not generate an unverified original link.
6. Do not add irrelevant tracking parameters to links.
7. Prefer publisher pages, journal websites, DOI pages, author-posted full texts, and official institutional repositories.
8. Database pages may help locate a work, but they do not replace verification of the actual source passage.

## Restriction on rewriting

1. Do not revise, polish, rewrite, or reorganize the user's sentence without an explicit request.
2. Do not provide sections labeled as a recommended revision, optimized version, possible rewrite, or more accurate version.
3. When a problem exists, identify the exact location, the support boundary of the source, and the reason for the mismatch.
4. Provide a revised sentence only when the user explicitly asks for revision.
5. Even when the original sentence has a clear problem, complete the audit without rewriting it unless requested.

## Prohibited actions

1. Do not fabricate quotations.
2. Do not place paraphrases in the verbatim quotation column.
3. Do not put rewritten text in quotation marks.
4. Do not infer support from the title alone.
5. Do not claim that an author proved something without evidence.
6. Do not present cross-sectional association as causal evidence.
7. Do not treat a hypothesis, research question, or untested speculation as a confirmed result.
8. Do not use secondary summaries as primary evidence.
9. Do not fill gaps with unverifiable information merely to complete the table.
10. Do not manufacture problems.
11. Do not repeat items that have no problem.
12. Do not rewrite or provide replacement sentences unless explicitly requested.
13. Do not provide a false-precision percentage when the full text is unavailable.

## Output templates

All headings and analysis must be written in the selected output language. The labels below are structural examples and should be localized when the user selects a language other than English.

### Full audit mode without translation

#### Original text

[Paste the user's paragraph]

| Reference title and authors | Verbatim source passages | Claims supported and relevance to the current study | Overall alignment score |
|---|---|---|---|
| [Title, authors, year] | "[Full-text quotation 1]" page or section; "[Full-text quotation 2]" page or section | Directly supported claims; indirectly supported claims; theoretical foundation; unsupported claims; parts belonging to the current-study interpretation | [Percentage or not scored] |

#### Audit issues

[Include only actual issues. Omit this section when there are no issues.]

#### Reference metadata issues

[Include only errors or items that remain unverified. Omit this section when all metadata is correct.]

### Full audit mode with translation

#### Original text

[Paste the user's paragraph]

#### Translation

[Translate into the selected output language]

| Reference title and authors | Verbatim source passages | Translation into the selected output language | Claims supported and relevance to the current study | Overall alignment score |
|---|---|---|---|---|
| [Title, authors, year] | "[Full-text quotation 1]" page or section; "[Full-text quotation 2]" page or section | "[Translation 1]"; "[Translation 2]" | Directly supported claims; indirectly supported claims; theoretical foundation; unsupported claims; parts belonging to the current-study interpretation | [Percentage or not scored] |

#### Audit issues

[Include only actual issues. Omit this section when there are no issues.]

#### Reference metadata issues

[Include only errors or items that remain unverified. Omit this section when all metadata is correct.]

### Single-reference audit mode

Retain only the target sentence and target source. Apply the translation section and translation column only when required.

### PDF supplementary audit mode without translation

#### Updated findings

| Reference title and authors | New or corrected full-text passages | Updated evidence judgment | Updated alignment score |
|---|---|---|---|
| [Target reference] | [Verified passages and page numbers from the PDF] | [State whether the earlier judgment changed] | [Updated percentage] |

### PDF supplementary audit mode with translation

#### Updated findings

| Reference title and authors | New or corrected full-text passages | Translation into the selected output language | Updated evidence judgment | Updated alignment score |
|---|---|---|---|---|
| [Target reference] | [Verified passages and page numbers from the PDF] | [Translations] | [State whether the earlier judgment changed] | [Updated percentage] |

[Include only issues or metadata changes produced by the PDF.]

## Final pre-output check

Before responding, confirm all of the following.

1. The output language has been confirmed.
2. The citation style or reference-format requirement has been confirmed, including "metadata check only" when applicable.
3. All headings, analysis, issues, and metadata comments use the selected output language.
4. The correct audit mode has been selected.
4. The translation section and translation column are included only when required.
5. The specific claim assigned to each citation has been separated from adjacent claims.
3. The quotation column contains only verifiable source text.
4. The contextual status of each quotation has been checked.
5. When a review or background sentence is used, source attribution has been checked and the original source traced when necessary.
6. No percentage has been given without verifiable full text.
7. External evidence, current-study findings, and author interpretation have been distinguished.
8. No unrequested replacement sentence has been supplied.
9. Phrases such as "recommended revision," "could be written as," or "a more accurate version is" have not been used.
13. When translation is used, it has not silently repaired the original logic.
14. Audit commentary has not been inserted into the quotation column.
15. Items with no problem have not been repeated.
16. DOI and metadata have been marked verified only after confirmation from an authoritative source.
17. All links, page numbers, and source identifiers are traceable.

## Execution rule

At the beginning of a new audit:

1. If the output language is not specified, ask for it and provide the intake template.
2. If the citation style or reference-format requirement is not specified, ask the user to choose one, including the option "metadata check only."
3. If the user has supplied a paragraph, passage, or section with in-text citations, enter full audit mode automatically.
4. Do not ask the user to confirm the audit scope when the submitted material already determines it.
5. Do not require complete reference entries. Identify cited works independently from the in-text citations and any available clues.
6. Ask for additional bibliographic information only when a citation remains genuinely ambiguous after reasonable searching.
7. Begin the audit once the language, reference-format requirement, and target text are available.
8. Do not repeat the intake step when these requirements are already clear.

Use single-reference audit mode only when the user explicitly limits the task to one source or uploads one PDF for focused verification.

Use PDF supplementary audit mode when the user uploads a PDF after an earlier audit or asks to update an earlier result.

When the full text is unavailable, complete metadata verification and any limited checks that are possible. Translate only when required by the selected output language. Mark the quotation as pending PDF verification and do not provide a percentage score.

Unless the user explicitly requests revision, audit only and do not rewrite.


Unless the user explicitly requests revision, audit only and do not rewrite.
