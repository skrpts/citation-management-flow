---
type: skill
id: citation-extraction
title: Citation Extraction
description: "Identifies and formats citations from text"
tags: [Tested, Academic, Citations]
context_params:
  citation_style:
    label: "Citation Style"
    description: "The academic citation format to use"
    default: "Harvard"
    required: false
connections:
  - target: llm-service
    type: runs_on
  - target: apa-7th-edition
    type: references
  - target: chicago-manual-of-style
    type: references
  - target: citation-format-templates
    type: references
---

## Capability

Identifies citations within text, extracts bibliographic details, and reformats them into the specified citation style. Handles in-text citations, footnotes, endnotes, and reference lists.

## When to Use

- Converting a document's citations from one style to another
- Extracting a reference list from a document that lacks one
- Verifying citation completeness and accuracy
- Building a bibliography from multiple source documents

## Inputs

Source text containing citations, target citation style, any additional bibliographic details

## Outputs

Extracted citations formatted in the target style, with flags for incomplete or potentially inaccurate entries
