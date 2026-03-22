---
type: skill
id: citation-extraction
title: Citation Extraction
description: "Extracts structured bibliographic metadata from source materials and validates citation accuracy"
tags: [Production, Tested]
connections:
  - target: llm-service
    type: runs_on
  - target: citation-style-reference
    type: references
metadata:
  estimated_duration: "10-20 minutes"
  avg_tokens: 2500
---

## Capability

Extracts, structures, and validates bibliographic metadata from diverse source formats. This skill parses PDFs, web pages, database records, and manually entered source details to produce standardised bibliographic entries. It also validates existing citations by cross-referencing in-text citations against bibliography entries and identifying discrepancies.

## When to Use

- Building a source catalogue from a collection of PDFs, URLs, or database exports
- Extracting citation metadata from a reference list in an existing document
- Validating that all in-text citations have corresponding bibliography entries (and vice versa)
- Cleaning up inconsistent or incomplete bibliographic records
- Importing sources from one reference manager format to another

## Inputs

- Source materials in any of: PDF metadata, URL, DOI, ISBN, manual entry, BibTeX, RIS, or plain text reference
- For validation: manuscript text containing in-text citations and the corresponding bibliography
- Target metadata schema (default: complete — authors, title, year, journal/publisher, volume, issue, pages, DOI, URL, access date, source type, abstract)

## Process

1. **Parse source input** — identify the input format and extract raw bibliographic fields. Handle multiple input formats (DOI lookup, PDF metadata extraction, URL scraping, manual parsing)
2. **Normalise metadata** — standardise author name formats (Last, First M.), date formats (YYYY), and publication venue names (full journal titles, not abbreviations unless specified)
3. **Validate completeness** — check each entry against the required metadata fields. Flag entries missing critical fields (author, year, title) as incomplete
4. **Verify accuracy** — where DOIs are available, cross-reference extracted metadata against DOI records. Flag discrepancies between the source text and the DOI metadata
5. **Classify source type** — categorise each source as: journal article, book, edited book chapter, conference paper, thesis/dissertation, technical report, government document, website, newspaper/magazine article, or other
6. **Deduplicate** — identify and merge duplicate entries (same DOI, same title+year+author combinations)
7. **For validation tasks** — scan manuscript text for in-text citations, match each against the bibliography, and produce a discrepancy report

## Outputs

- Structured bibliographic records in a standardised format
- Completeness assessment for each record (complete, partial, or minimal)
- Duplicate detection report
- For validation: matched citations, orphaned in-text citations, unused bibliography entries, and formatting inconsistencies

## Constraints

- Never fabricate or guess missing metadata — flag gaps for manual completion
- When parsing author names, handle edge cases: organisational authors, single-name authors, hyphenated names, particles (de, van, von)
- Distinguish between publication date and access date for online sources
- Preserve original language titles alongside English translations where applicable
- Handle sources with no author, no date, or no page numbers according to the conventions of the target citation style
