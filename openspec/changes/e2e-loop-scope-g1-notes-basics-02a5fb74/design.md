# Design

## Context

The `orca-companion` repository currently exposes only `README.md` (public-facing overview) and `orca-companion.json` (harness configuration). There is no internal documentation channel, and the Orca harness scope-envelope check for the upcoming `notes-basics` work package has no document to validate against.

## Goals / Non-Goals

**Goals**

- Introduce a single new file (`NOTES.md`) at the repository root.
- Establish a two-section structure ("Project Layout" and "Conventions") that downstream changes can extend without restructuring.

**Non-Goals**

- Rewriting, reformatting, or relocating `README.md`.
- Adding tooling, scripts, configuration files, or any other artifacts beyond `NOTES.md`.

## Decisions

- **Use plain Markdown instead of a structured format**: keeps `NOTES.md` human-editable and consistent with `README.md`. Alternatives such as YAML front-matter or JSON were rejected because they push readers toward parsing the file rather than reading it.
- **Two required sections ("Project Layout", "Conventions")**: gives downstream changes stable anchor headings to extend and to validate against. A single free-form body was rejected because future edits would drift without leaving room for follow-up sections such as "Follow-ups".

## Risks / Trade-offs

- [Notes can drift from the real project layout over time] → Follow-up changes must update `NOTES.md` whenever a top-level file is added or removed, and the spec requires "Project Layout" to enumerate the four known top-level files.
- [Risk that `NOTES.md` duplicates `README.md`] → Scope envelope forbids touching `README.md`; this change keeps `NOTES.md` strictly internal and frames `README.md` as the public-facing overview inside the "Conventions" section.

## Migration Plan

Not applicable. This change only adds a new file at the repository root.

## Open Questions

None.
