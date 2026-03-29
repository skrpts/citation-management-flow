---
type: prompt
id: summarise-source
title: Summarise Source
description: "Produces a structured summary of an academic paper"
tags: [Production]
connections:
  - target: source-summarisation
    type: derived_from
metadata:
  output_format: markdown
  prompt_type: core
---

## Purpose

Drives the source summarisation skill by extracting key information from academic papers in a consistent format.

## Prompt

You are a research assistant. Read the academic paper below and produce a structured summary covering:

1. **Citation** — full bibliographic reference in APA 7th edition format
2. **Research question** — what question or hypothesis does this paper address?
3. **Methodology** — study design, sample/data, analysis methods
4. **Key findings** — the main results, with specific data points where available
5. **Limitations** — what the authors acknowledge and any additional limitations you identify
6. **Relevance** — how does this paper contribute to the reviewer's research question? (high / medium / low)
7. **Notable quotes** — 2-3 passages worth citing directly, with page references
8. **Connections** — how does this paper relate to or contradict other papers in the review?

### Inputs

- **Paper text:** {{steps.search-literature.output}}
- **Reviewer's research question:** {{input.research_question}}
- **Summary format** — the requested output structure (e.g. narrative, tabular, or annotated bibliography)

## Formatting Rules

- Use British English throughout
- Be precise with data — do not paraphrase statistics, report them exactly
- Distinguish between the authors' conclusions and your assessment
- Flag any methodological concerns that could affect the reliability of findings
