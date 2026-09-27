# Design

## Context

The repository today is a near-empty harness baseline: it contains `.gitignore`, `README.md`, and `orca-companion.json`, with no other project documentation. The existing `README.md` explicitly defers further sections ("_More sections (Installation, Usage, etc.) will be added in later changes._"), so contributors need a separate, lower-churn surface for orientation, conventions, and pointers that should not live in the public-facing `README.md`.

The Work Package Scope Envelope constrains this change to a single path: `NOTES.md`. No other files may be added, removed, or restructured.

## Goals / Non-Goals

**Goals:**
- Land a single new file at the repository root (`NOTES.md`) that satisfies the `project-notes` spec.
- Keep the change self-contained: one file, plain Markdown, no tooling, no build step.
- Set a stable heading structure (title, Overview, Conventions, Pointers) so later changes can extend it without re-shaping it.

**Non-Goals:**
- Editing `README.md`, `orca-companion.json`, `.gitignore`, or any other existing file.
- Adding Installation, Usage, Contributing, or any other topical sections — those belong to later changes.
- Introducing Markdown linting, link-check CI, or any other tooling configuration.
- Changing the project's tooling or runtime behavior.

## Decisions

- **Plain GitHub-flavored Markdown, no front matter.** `NOTES.md` is human-authored orientation, not a generated or templated artifact, so YAML/TOML front matter is unnecessary and would only add noise. Alternatives considered: TOML front matter (rejected — not idiomatic for free-form notes), a separate `notes/` directory (rejected — outside the Work Package Scope Envelope).
- **Repository-root location, not a docs subdirectory.** `NOTES.md` sits beside `README.md` because contributors expect top-level Markdown to live at the root, and the Scope Envelope only permits a root path. A `docs/notes.md` location was considered and rejected (out of scope).
- **Stable four-section skeleton: title + Overview + Conventions + Pointers.** This gives later changes predictable anchors to extend (e.g., an Installation subsection under Overview) without inventing new top-level headings. A more elaborate skeleton was rejected as speculative.
- **No automated generation or templating.** The file is authored once by hand in this change. A template-driven approach was rejected as over-engineering for a single document.

## Risks / Trade-offs

- [Section names get re-litigated by later changes] → Mitigation: the spec pins the four top-level sections as normative, so any later change that wants a different heading has to update the spec first.
- [Content becomes stale without an owner] → Mitigation: keep the file small in this change; later changes can extend it under the same spec.
- [Readers confuse `NOTES.md` with `README.md`] → Mitigation: `README.md` keeps its stub role; `NOTES.md` is clearly labeled as orientation/conventions/pointers, not as the public entry point.

## Migration Plan

- Apply this change in the existing Git worktree.
- After the change is archived by the OpenSpec workflow, `NOTES.md` becomes part of the repository's `main` capabilities (no separate migration of data or config is required — there is nothing to migrate).
- Rollback: remove `NOTES.md` (single-file revert) if the change is rejected after merge.

## Open Questions

None. The Work Package Scope Envelope, the proposal's `## Impact`, and the spec all align on a single file with a fixed four-section skeleton. No decision in this design is deferred to a later change.
