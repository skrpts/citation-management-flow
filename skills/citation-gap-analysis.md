---
type: skill
id: citation-gap-analysis
title: Citation Gap Analysis
description: "Assessing citation coverage across a document to surface uncited claims, orphan references, and gaps in the source base"
tags: [Production, Academic, Citations]
connections:
  - target: llm-service
    type: runs_on
metadata:
  estimated_duration: "5 minutes"
  avg_tokens: 2500
  trigger: manual
---

## Citation Gap Analysis

This skill assesses how well a document's claims are supported by its citations, identifying weaknesses in the source base before submission.

### Core Capability

Given the validated manuscript and its reference material, this skill scans every claim, checks its citation coverage, and reports the gaps — uncited assertions, orphan references, and incomplete entries — with a severity ranking.

### Method

1. **Claim scan:** Identify assertions of fact, statistics, attributions, and methodological choices.
2. **Coverage check:** Determine whether each claim carries a supporting citation and whether cited sources are fully referenced.
3. **Gap reporting:** Flag uncited claims, orphan citations, incomplete references, and self-evident claims that genuinely need no citation.

### Output Structure

A tabular gap report (claim, issue, severity, recommendation) followed by a summary of claims checked, fully cited, and needing attention. High severity marks core arguments left unsupported.
