# Design

## Context

See proposal.md - Why for motivation. The current repository root contains only `README.md`, `orca-companion.json`, and the OpenSpec configuration directories. The companion harness and downstream OpenSpec changes need a single, predictable Markdown document for project-internal notes, and the project currently has none.

The Scope Envelope for this Work Package is limited to `NOTES.md`, so any approach must avoid touching `README.md`, `orca-companion.json`, OpenSpec configuration, or tooling. The deliverable is purely a documentation baseline.

## Goals / Non-Goals

**Goals:**

- Introduce a single `NOTES.md` file at the repository root that satisfies every requirement in `openspec/changes/e2e-loop-scope-g1-notes-basics-02a5fb74/specs/notes-basics/spec.md`.
- Keep the initial baseline intentionally minimal so future changes can extend the document without rewrites.
- Provide stable section anchors (Purpose, Conventions, Decisions, Open Questions) that downstream tooling or follow-up changes can rely on.

**Non-Goals:**

- Adding any build, lint, CI, or automation around NOTES.md (out of scope for this Work Package).
- Editing or reorganising `README.md`, `orca-companion.json`, or any OpenSpec configuration.
- Establishing a content policy, review process, or contributor workflow for NOTES.md entries.

## Decisions

- **Document location at the repository root.** Place `NOTES.md` directly next to `README.md` rather than in a subdirectory so it is discoverable by anyone browsing the repository top level. Considered nesting it under `docs/` but rejected that because the project has no other files in such a directory and the root keeps the surface area minimal.
- **Use four fixed H2 sections.** Pick `Purpose`, `Conventions`, `Decisions`, `Open Questions` as the only required H2 headings. Considered letting contributors invent their own sections, but rejected that because the spec contract requires predictability for downstream tooling and follow-up changes.
- **Keep the baseline body content short.** Seed each section with one or two sentences that match the section's intent. Considered writing a long-form reference document, but rejected that because the Scope Envelope restricts the change to NOTES.md only and over-filling the baseline would make later extensions harder to track.
- **Encode the file as UTF-8 Markdown with no BOM.** This matches the existing `README.md` and keeps the document portable across the same editors contributors already use.

## Risks / Trade-offs

- [Future contributors may add content that drifts from the four required H2 sections.] → The spec contract pins the section ordering and headings, so drift is detectable by inspection and by any later `openspec validate` runs.
- [The baseline may feel redundant with README.md.] → The spec explicitly forbids duplicating README.md content, and the four-section structure keeps the document focused on development-only material.
- [A future change may need to introduce a subdirectory such as `docs/notes/` to host more detailed notes.] → The Scope Envelope forbids touching files outside `NOTES.md` in this change, so any such move is explicitly deferred to a later Work Package.

## Open Questions

_None — the spec, scope, and approach are all settled for this Work Package._

