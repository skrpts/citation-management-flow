---
type: skill
id: bibliography-formatting
title: Bibliography Formatting
description: "Formats citations and bibliographies according to major academic referencing styles"
tags: [Production, Tested, Academic, Citations]
connections:
  - target: llm-service
    type: runs_on
  - target: citation-style-reference
    type: references
metadata:
  estimated_duration: "15-30 minutes"
  avg_tokens: 3000
---

## Capability

Formats bibliographic entries and in-text citations according to the precise rules of major academic referencing styles. This skill handles the full complexity of citation formatting including author truncation, date formats, italicisation, punctuation, hanging indentation, and ordering rules. It supports style conversion — taking entries formatted in one style and converting them to another while preserving all metadata.

## When to Use

- Formatting a bibliography for journal submission in a specific citation style
- Converting an existing bibliography from one style to another (e.g., APA to Chicago for a different journal)
- Generating in-text citation forms for sources in the catalogue
- Checking existing citations against the rules of the target style
- Formatting edge cases: sources with unusual authorship, untranslated titles, retracted articles

## Inputs

- Structured bibliographic metadata (from the citation-extraction skill or manual entry)
- Target citation style: APA 7th, MLA 9th, Chicago 17th (notes-bibliography or author-date), Harvard, IEEE, Vancouver, or other specified style
- Source citation style (for conversion tasks)
- Specific requirements: numbered vs. alphabetical ordering, annotated vs. standard bibliography, "works cited" vs. "references" vs. "bibliography" heading

## Process

1. **Identify source type** — determine the correct citation template for each source type (journal article, book, chapter, website, etc.) in the target style
2. **Format author names** — apply the target style's author formatting rules:
   - Author order and separator (comma, ampersand, "and")
   - Truncation threshold (e.g., APA: list up to 20 authors; after 20, list first 19 + ... + last author)
   - Name format (Last, F.M. for APA; Last, Firstname for Chicago)
3. **Format dates** — apply date placement and format rules (year in parentheses for APA, year at end for MLA, year after author for Harvard)
4. **Format titles** — apply capitalisation rules (sentence case for APA, title case for MLA/Chicago), italicisation rules (journal titles, book titles), and quotation mark rules (article titles in some styles)
5. **Format publication details** — volume, issue, pages, DOI/URL according to style conventions
6. **Generate in-text forms** — produce the correct in-text citation for each source:
   - Parenthetical form: (Author, Year) for APA; (Author Page) for MLA
   - Narrative form: Author (Year) for APA; Author (Page) for MLA
   - Handle multiple authors, same-author-same-year disambiguation, and secondary citations
7. **Order the bibliography** — alphabetical by first author surname (APA, MLA, Chicago author-date, Harvard) or by order of first citation (IEEE, Vancouver)
8. **Apply formatting** — hanging indentation, double spacing, and other style-specific presentation rules

## Outputs

- Complete formatted bibliography in the target style
- In-text citation forms (parenthetical and narrative) for each source
- Style compliance notes flagging any entries that required manual decisions or deviate from standard rules
- For conversion tasks: a mapping showing what changed between the source and target styles

## Constraints

- Follow the most recent edition of each style guide precisely — do not mix conventions from different editions
- When a source type is not explicitly covered by the style guide, apply the closest analogous rule and note the decision
- Handle digital-only sources (no page numbers, no volume/issue) according to each style's conventions for online materials
- Preserve diacritical marks, non-Latin characters, and special symbols in author names and titles
- For styles that require access dates (e.g., APA for online sources without DOIs), include the date the source was last accessed
- Never abbreviate journal titles unless the target style explicitly requires it (e.g., Vancouver uses NLM abbreviations)
