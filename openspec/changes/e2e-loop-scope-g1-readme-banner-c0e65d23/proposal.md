# Proposal — README Banner

## Why

The repository currently has no `README.md` at the integration baseline (commit `98af9bb`). Without a top-level document, downstream consumers (humans and agents) have no canonical place to find the project's identity, intent, and primary entry points. Introducing a README banner section fixes this gap with the smallest possible change: a clearly demarcated header block that can be extended later without rewriting the file.

This change is the first artifact (`g1`) of the `e2e-loop-scope` evaluation flow. Its purpose is to verify that the spec-driven loop can land a tightly scoped, single-file documentation change end-to-end.

## What Changes

- **Add `README.md`** at the repository root.
- The file begins with a **banner section** (a Markdown heading block) that identifies the project and signals where the reader is.
- Below the banner, leave a short placeholder line so future contributors know the document is intentionally minimal at this stage.
- No other files are created or modified.

## Capabilities

### New Capabilities

- `readme-banner`: Defines the structure and content of the banner section that opens `README.md`, so the file is recognisable as the project's entry point and is easy to extend later.

### Modified Capabilities

_None._ This change introduces a single new capability and does not alter any existing capability's requirements.

## Impact

- `README.md` _(new file at repository root — sole path in the work-package scope envelope)_
