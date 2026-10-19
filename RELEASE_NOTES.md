# Release Notes

## v1.1.27
GH#1044 — document the inputs this workflow's prompts REQUIRE but its Inputs table never listed. A user supplying exactly what the table asked for was running with required parameters unsatisfied — a silent wrong run, not a documentation nicety. documented 1 input(s): research_question. Every row is generated from the requiring prompt's own declared description, example and required flag — none invented. No behaviour change; documentation only.

## v1.1.26
GH#863 Wave 1 (batch 2, #858-A1 class) — fix the intent/output mismatch (K-045): the bundle shipped `in-text-citation-checker`, `citation-gap-analyser`, and `bibliography-generator` prompts and the docs described running them, but the `execution:` block never did — so the skrpt emitted a polished intermediate (the source summaries) instead of the promised publication-ready bibliography. Restored the intended bound graph: added three producer steps — **In-Text Citation Validation**, **Citation Gap Analysis**, and **Bibliography Generation** — each with a backing skill so it is `from_step`-addressable, ordered `Citation Extraction → Source Summarisation → Bibliography Formatting → In-Text Citation Validation → Citation Gap Analysis → Bibliography Generation`. Rewired the wired prompts' cross-step refs from positional/title `{{steps.<Title>.output}}` and `{{steps.previous.output}}` to explicit `from_step` bindings via `{{step.context.*}}` context params. Completed the tail: repinned `polish-language` 1.0.1→1.0.6 (the version exposing the bindable `source` slot) and bound `language-polish`'s `source` ← the Bibliography Generation output, so the `output_step` polishes the actual deliverable (the final bibliography) rather than its positional previous. No new required inputs.

## v1.1.25
GH#845 — republish with American English (en-US) content, completing the source-only GH#805 flip that never reached the Hub. Copy only — no functional or behaviour change.

## v1.1.24
GH#749 Phase 2 — supply summarise-source via `bindings: source_text { from_input: source_materials }` (#750/#752) and re-pin the dep to v1.0.3 (position-safe), fixing the previously-dangling {{steps.Literature Search.output}} ref. Also declare per-step `output: {name,type}` (GH#745, deferred until #749). Canonical scan clean.

## v1.1.23
GH#645 Row 3b — migrate to K-037 dep-referenced schema. Strip 9 inline shared-content files and declare 9 hub-shared deps (UUID id + slug name + version + checksum from `gen-dep-checksums.mjs`). Closes pre-Step-3 inline-vendoring for this bundle.

## v1.1.22
Wave 2: re-signed with canonical engine signing pipeline.

## v1.1.21
Tags migrated inline into manifest (GH#586). tags.yaml retired.

## v1.1.20
Bundle re-signed with canonical engine signing pipeline (Wave 2 migration).

## v1.1.19
Signature fix — RELEASE_NOTES.md now included in integrity checksum.

## v1.1.18
Initial catalog release with full structural and content-quality validation. All scanner checks pass.
