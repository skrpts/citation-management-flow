---
type: service
id: claude-service
title: Claude Service
description: "Anthropic Claude integration for citation extraction, formatting, and bibliography generation"
tags: [Production, Tested]
connections:
  - target: anthropic-claude
    type: runs_on
metadata:
  provider: anthropic
  model: claude-sonnet
---

## Service Description

This skrpt uses Anthropic Claude as the primary reasoning engine for all citation management tasks. Claude handles source cataloguing, citation style conversion, in-text citation validation, bibliography generation, and citation gap analysis.

## How This Skrpt Uses Claude

### Citation Extraction
Claude parses source materials — PDFs, web pages, book entries, database records — and extracts structured bibliographic metadata including authors, title, year, journal/publisher, volume, issue, pages, DOI, URL, and access date.

### Style Conversion
Claude converts citations between major academic referencing styles (APA 7th, MLA 9th, Chicago 17th, Harvard, IEEE, Vancouver). It understands the nuanced formatting rules of each style including author truncation thresholds, date placement, italicisation conventions, and punctuation patterns.

### Validation
Claude cross-references in-text citations against bibliography entries to identify orphaned citations (in-text but not in bibliography), unused references (in bibliography but never cited), and formatting inconsistencies.

### Gap Analysis
Claude analyses the source coverage of a manuscript, identifying under-cited claims, over-reliance on single sources, temporal gaps in the literature, and missing perspectives.

## Configuration

- **Model:** Claude Sonnet or higher for accurate citation formatting
- **Context window:** Extended context needed for processing full manuscripts and bibliographies
- **Temperature:** 0.1 for citation formatting (precision-critical), 0.4 for gap analysis
- **Output format:** Structured markdown with citation entries in the target style
