---
type: skill
id: bibliography-generation
title: Bibliography Generation
description: "Producing a complete, publication-ready bibliography from the validated source catalogue in the target citation style"
tags: [Production, Academic, Citations]
connections:
  - target: llm-service
    type: runs_on
  - target: citation-style-reference
    type: references
metadata:
  estimated_duration: "10 minutes"
  avg_tokens: 2500
  trigger: manual
---

## Bibliography Generation

This skill produces the workflow's primary deliverable: a complete, publication-ready bibliography assembled from the validated source catalogue and formatted precisely to the target citation style's rules.

### Core Capability

Given the source catalogue and the target citation style, this skill filters to cited sources, orders entries by the style's conventions, formats each reference in full, and applies presentation rules (heading, hanging indentation, spacing) expected by academic journals and publishers.

### Method

1. **Filter sources:** Include confirmed-cited sources; separate any "works consulted" section where requested.
2. **Order entries:** Apply alphabetical or numerical ordering per the target style, with same-author and same-year disambiguation.
3. **Format entries:** Produce each full reference-list entry with correct author, date, title, publication, and DOI/URL formatting.
4. **Apply presentation:** Hanging indentation, correct heading ("References", "Works Cited", "Bibliography", "Reference List"), and spacing.
5. **Quality check:** Verify ordering, deduplicate, confirm DOI formatting, and check punctuation consistency.

### Output Structure

The complete formatted bibliography ready to paste into the manuscript, followed by a brief quality report noting total entries, special-formatting decisions, and any outstanding metadata issues.
