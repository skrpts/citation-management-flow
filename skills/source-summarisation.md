---
type: skill
id: source-summarisation
title: Source Summarisation
description: "Condenses academic papers into key findings, methods, and conclusions"
tags: [Production]
connections:
  - target: llm-service
    type: runs_on
---

## Capability

Reads academic papers and produces structured summaries covering research question, methodology, key findings, limitations, and relevance to the reviewer's topic. Extracts quotable passages and identifies how each paper contributes to the broader field.

## When to Use

- Processing a batch of papers identified through literature search
- Creating an evidence table for a systematic review
- Quickly assessing whether a paper is relevant enough to include in a review

## Inputs

Paper text (full or abstract), reviewer's research question, summary format preferences

## Outputs

Structured summary: citation details, research question, methodology, sample/data, key findings, limitations, relevance assessment, and notable quotes with page references
