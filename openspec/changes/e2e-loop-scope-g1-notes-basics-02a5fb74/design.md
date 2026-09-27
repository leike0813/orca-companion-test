# Design

## Context

See `proposal.md` — Why and What Changes for the motivation behind introducing `NOTES.md`.

The repository currently ships only `README.md` at the root, which already defers deeper sections ("Installation", "Usage", etc.) to later changes. The orca-companion baseline therefore has no canonical home for project-level notes, and the `notes-basics` capability has no implementing artifact.

Constraints that shape this design:

- The work-package scope envelope only allows creating `NOTES.md`; no other tracked file may be modified in this change.
- The spec (`specs/notes-basics/spec.md`) requires the file to exist at the root, declare the identity/purpose headings, reserve `Installation` and `Usage` placeholders, and remain a valid Markdown document.
- Downstream changes will fill in the reserved placeholders, so the placeholders must be explicit and easy to locate.

## Goals / Non-Goals

**Goals:**

- Produce a single new file, `NOTES.md`, at the repository root that satisfies every scenario in the `notes-basics` spec.
- Make the reserved `Installation` and `Usage` sections visually and semantically distinct from finalized content so future authors can locate them.

**Non-Goals:**

- Editing or referencing any file outside `NOTES.md` (including `README.md`); the scope envelope forbids it.
- Filling in real installation or usage instructions; that content belongs to later changes.
- Introducing tooling, linters, or CI hooks to validate `NOTES.md`; the spec is satisfied by the file's static structure alone.

## Decisions

- **Single-file change** — Implement `notes-basics` by writing exactly one new file, `NOTES.md`. Considered splitting across multiple files (e.g., separate identity/purpose docs) but rejected because the spec mandates a single root-level artifact and splitting would force later changes to consolidate.
- **Top-level (`#`) headings throughout** — Use only `#`-level headings inside `NOTES.md` so that the Markdown validity requirement (no skipped heading levels) is trivially satisfied and the section list is uniform.
- **Explicit placeholder copy** — Phrase the `Installation` and `Usage` bodies as unambiguous placeholders (e.g., `_Reserved for a future change._) so they cannot be confused with final documentation and so future authors can grep for the exact strings.
- **No automated validation hook** — Accept manual verification for this change. A Markdown linter or pre-commit check would expand the change beyond the scope envelope and is unnecessary while the file's structure is small and statically defined.

## Risks / Trade-offs

- [Risk] Future authors may forget that `Installation` and `Usage` are placeholders and treat them as final docs. → Mitigation: the placeholders state "Reserved for a future change." explicitly, and the spec's Reserved Future Sections requirement is reviewed by admission.
- [Risk] Without a linter, drift between `NOTES.md` and the `notes-basics` spec could go undetected. → Mitigation: the spec's Markdown Validity requirement is narrow (top-level headings only, valid UTF-8), so visual review during admission is sufficient for this baseline change.
- [Trade-off] Keeping `README.md` untouched means `NOTES.md` duplicates the project's identity/purpose framing already present in `README.md`. Accepted because the scope envelope forbids touching `README.md` and the duplication is intentional until a later change reconciles the two files.

## Migration Plan

Not applicable — this change introduces a new file only and has no rollback impact beyond deleting `NOTES.md` if the change is reverted. No data migration, deployment step, or runtime configuration is involved.

## Open Questions

None — the scope envelope, the spec, and the placeholder strategy leave no deferrable unknowns.
