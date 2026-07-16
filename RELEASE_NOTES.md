# Release Notes

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
