---
type: skill
id: in-text-citation-validation
title: In-Text Citation Validation
description: "Auditing a manuscript's in-text citations against the formatted bibliography for completeness, accuracy, and formatting consistency"
tags: [Production, Academic, Citations]
connections:
  - target: llm-service
    type: runs_on
metadata:
  estimated_duration: "5 minutes"
  avg_tokens: 2500
  trigger: manual
---

## In-Text Citation Validation

This skill audits every in-text citation in a manuscript against the formatted bibliography, catching the errors that most often survive to submission: orphaned citations, unused references, and inconsistent formatting.

### Core Capability

Given the manuscript text and the formatted bibliography, this skill inventories every in-text citation, cross-references each against the reference list, and reports discrepancies with a clear severity ranking.

### Method

1. **Citation inventory:** Record every in-text citation with its exact text, location, and format (parenthetical or narrative).
2. **Cross-reference:** Match each citation to a bibliography entry, verifying author, year, and page details.
3. **Discrepancy detection:** Surface orphaned citations (no matching entry), unused references (never cited), and formatting inconsistencies.

### Output Structure

A structured validation report grouped by check type, with counts (found, matched, orphaned, unused, formatting errors) and issues prioritised by severity. The report feeds the downstream gap analysis and final bibliography stages.
