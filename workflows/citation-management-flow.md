---
type: workflow
id: citation-management-flow
title: Citation Management Flow
description: "End-to-end citation tracking, formatting, and bibliography generation for academic writing"
tags: [Production, Tested, Academic, Citations, Writing]
connections:
  - target: citation-extraction
    type: uses
  - target: bibliography-formatting
    type: uses
  - target: source-summarisation
    type: uses
  - target: language-polish
    type: uses
  - target: llm-service
    type: runs_on
  - target: citation-style-reference
    type: references
  - target: citation-best-practices
    type: references
  - target: source-catalogue-template
    type: uses
metadata:
  estimated_duration: "30-60 minutes"
  trigger: manual
output_step: "language-polish"
composite_steps:
  - "citation-extraction"
  - "bibliography-formatting"
  - "source-summarisation"
  - "source-catalogue-template"
  - "language-polish"
execution:
  - skill: "citation-extraction"
    step_type: "synthesis"
    prompt: "source-cataloguer"
    context:
      citation_style: "Harvard"
  - skill: "bibliography-formatting"
    step_type: "synthesis"
    prompt: "citation-style-converter"
  - skill: "source-summarisation"
    step_type: "synthesis"
  - skill: "language-polish"
    step_type: "content"
---

## Overview

This workflow manages the complete citation lifecycle for academic writing projects. It takes researchers from initial source cataloguing through citation formatting, validation, and bibliography generation, with a final gap analysis to ensure thorough and balanced source coverage. The flow supports all major citation styles and can process sources at any stage of the writing process — from early literature collection through to final manuscript preparation.

## Pipeline Stages

### Stage 1: Source Cataloguing

**Input:** Raw source materials (PDFs, URLs, database records, book details), the **source-catalogue-template** asset

Invoke the **citation-extraction** skill via the **source-cataloguer** prompt. Extract structured bibliographic metadata from each source and compile it into a standardised catalogue. Each entry captures: authors, title, year, publication venue, volume, issue, pages, DOI, URL, access date, source type (journal article, book, chapter, conference paper, thesis, report, website), and a brief annotation summarising relevance to the research.

**Output:** Complete source catalogue with standardised metadata for all sources.

**Checkpoint:** Review the catalogue for completeness and accuracy. Verify DOIs resolve correctly. Flag any sources with incomplete metadata (missing author, year, or publication details) for manual completion.

### Stage 2: Citation Style Conversion

**Input:** Source catalogue from Stage 1, target citation style, manuscript text (if available)

Invoke the **bibliography-formatting** skill via the **citation-style-converter** prompt. Convert all catalogue entries into the target citation style, producing both in-text citation forms and full reference list entries. If the researcher needs to switch styles (e.g., submitting to a different journal), this stage can be re-run with a new target style.

**Output:** Formatted citations in the target style — both in-text and reference list forms for each source.

**Checkpoint:** Spot-check 5-10 citations against the style guide. Pay particular attention to edge cases: sources with more than 20 authors, sources with no author, sources with no date, translated works, and secondary citations.

### Stage 3: In-Text Citation Validation

**Input:** Manuscript text, formatted bibliography from Stage 2

Invoke the **citation-extraction** skill via the **in-text-citation-checker** prompt. Scan the manuscript to identify every in-text citation and cross-reference it against the bibliography. Flag any discrepancies.

**Output:** Validation report listing: matched citations, orphaned in-text citations (no matching bibliography entry), unused bibliography entries (never cited in text), and formatting errors.

**Checkpoint:** Resolve all orphaned citations and decide whether to retain or remove unused bibliography entries. Fix any formatting inconsistencies.

### Stage 4: Bibliography Generation

**Input:** Validated source catalogue, target citation style, list of sources actually cited in the manuscript

Invoke the **bibliography-formatting** skill via the **bibliography-generator** prompt. Produce a final, formatted bibliography ready for inclusion in the manuscript. Ensure correct alphabetical ordering (or numerical ordering for numbered styles), hanging indentation, and consistent formatting throughout.

**Output:** Complete, publication-ready bibliography in the target citation style.

**Checkpoint:** Verify ordering rules are correct for the target style. Check that all cited sources appear and no uncited sources are included (unless the target format requires a "works consulted" section).

### Stage 5: Citation Gap Analysis

**Input:** Manuscript text, source catalogue, research questions, field of study

Invoke the **citation-extraction** skill via the **citation-gap-analyser** prompt. Analyse the citation coverage of the manuscript to identify weaknesses in the source base.

**Output:** Gap analysis report covering: under-cited claims, over-reliance on single sources, temporal coverage gaps, geographic or methodological diversity gaps, and missing seminal works.

**Checkpoint:** Address critical gaps (unsupported claims, missing seminal works) before submission. Consider whether identified gaps reflect genuine weaknesses or deliberate scope decisions.

## Error Handling

- If source metadata is incomplete or ambiguous, flag the entry for manual verification rather than guessing
- If a citation style has conflicting rules across different editions, default to the most recent edition and note the version used
- If the manuscript uses inconsistent citation formatting (mixing styles), identify the dominant style and flag all deviations
- If DOIs do not resolve, retain them but flag for verification — they may contain transcription errors
- If the gap analysis identifies more than 10 critical gaps, prioritise by severity and recommend addressing the top 5 before submission

## Inputs

| Name | Required | Description | Example |
|------|----------|-------------|---------|
| `{{input.source_materials}}` | Yes | The sources or source metadata you want to catalogue and cite | `PDFs, URLs, DOI list, or bibliography export` |
| `{{input.target_citation_style}}` | Yes | The citation format you need to produce | `APA 7th edition` |
| `{{input.manuscript_text}}` | No | Draft manuscript text to validate in-text citations against | `Paste your draft introduction and literature review` |
| `{{input.research_topic}}` | No | The research topic these sources relate to | `Impact of social media on adolescent mental health` |
| `{{input.source_count}}` | No | Approximate number of sources to catalogue | `25` |
| `{{input.research_field}}` | No | The academic field or discipline of the manuscript | `Psychology` |
| `{{input.manuscript_authors}}` | No | Names of the manuscript authors for self-citation analysis | `Smith, J. and Jones, A.` |

## Outputs

| Name | Description |
|------|-------------|
| Complete source catalogue | Complete source catalogue with standardised metadata for all sources |
| Formatted citations in the target style — both in-text and reference list forms for each source | Formatted citations in the target style — both in-text and reference list forms for each source |
| Validation report listing: matched citations, orphaned in-text citations , unused bibliography entries , and formatting errors | Validation report listing: matched citations, orphaned in-text citations , unused bibliography entries , and formatting errors |
| Complete, publication-ready bibliography in the target citation style | Complete, publication-ready bibliography in the target citation style |
| Gap analysis report covering: under-cited claims, over-reliance on single sources, temporal coverage gaps, geographic or methodological diversity gaps, and missing seminal works | Gap analysis report covering: under-cited claims, over-reliance on single sources, temporal coverage gaps, geographic or methodological diversity gaps, and missing seminal works |

## Setup

Before running this workflow:

1. No external services required — paste your content directly and provide any supporting context as inputs or source nodes.
2. Review the included documents, assets, or source nodes and customise them to match your team, brand, or domain conventions where needed.
3. No specific AI provider or API key is required beyond your configured skrptiq LLM provider.

## Provider Notes

- Most stages work with any capable model; stronger models usually improve synthesis, judgement, and writing quality.
- Extraction, classification, and formatting steps generally run well on smaller or faster models.
- Because there are no vendor-specific integrations here, provider choice is mostly a trade-off between speed, quality, and cost.

## Example Input

To test this workflow immediately after import:

```
Source Materials: "PDFs, URLs, DOI list, or bibliography export"
Target Citation Style: "APA 7th edition"
Manuscript Text: "Paste your draft introduction and literature review"
```

