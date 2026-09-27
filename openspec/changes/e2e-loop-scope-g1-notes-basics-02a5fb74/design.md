# Design

## Context

The repository starts from the isolated `e2e39` baseline (commit `968671b`) which only contains `.gitignore`, `README.md`, and `orca-companion.json`. There is no existing notes file or notes-related tooling, so this change has to introduce both the file and the convention for what it contains from scratch. The only files in scope for this Work Package are `NOTES.md` (new), which keeps the design narrow.

See `proposal.md` for motivation and `specs/project-notes/spec.md` for the behavior contract.

## Goals / Non-Goals

**Goals:**
- Produce a single `NOTES.md` at the repository root that satisfies every requirement in `specs/project-notes/spec.md`.
- Seed each baseline section with a small amount of realistic placeholder content so future changes have something concrete to extend.
- Keep the implementation minimal and auditable — no new tooling, no scripts, no nested directories.

**Non-Goals:**
- Wiring `NOTES.md` into any build, lint, or harness configuration.
- Adding tooling (Markdown linters, generators, CI checks) for `NOTES.md`.
- Introducing nested note files (e.g., `docs/notes/*.md`) or section taxonomy beyond the three baseline headings.
- Editing `README.md`, `orca-companion.json`, or any other file outside this change's scope envelope.

## Decisions

- **Single root-level file.** Place `NOTES.md` directly at the repository root. Alternatives considered: nested under `docs/` (rejected — adds directory overhead and breaks the simple "look at the root" mental model) and multiple per-topic files (rejected — out of scope and adds cross-file consistency work).
- **Three baseline sections.** Use the section set `Overview`, `Conventions`, `Open Questions` exactly as specified. Alternatives considered: a more elaborate section taxonomy (rejected — this generation only needs a stable spine, and adding sections can happen in later changes via MODIFIED requirements).
- **Markdown-only, no front matter.** Write `NOTES.md` as plain CommonMark without YAML/TOML front matter so the file renders identically on GitHub, IDE previews, and `cat`. Alternatives considered: front-matter for metadata (rejected — no consumer of that metadata exists yet, and the spec forbids non-Markdown constructs).
- **Seed content, not stubs.** Fill each baseline section with one short, factual paragraph or a single realistic bullet rather than a literal `TODO`. Alternatives considered: empty placeholders (rejected — would force the very next change to edit every section) and copy-paste from the README (rejected — README intentionally defers details to later changes).

## Risks / Trade-offs

- [Seed content drifts from reality] → Mitigation: keep each seed paragraph to one or two sentences tied to information that is already true in `README.md` and `orca-companion.json`, so a quick comparison catches drift.
- [Future changes over-stuff `Open Questions`] → Mitigation: the spec only requires at least one bullet, so additional changes can ADD or MODIFY requirements without breaking existing tests.
- [Tooling accidentally depends on `NOTES.md`] → Mitigation: this change intentionally does not reference `NOTES.md` from any config; any future reference belongs to its own change with its own scope envelope.

## Migration Plan

Not applicable. `NOTES.md` is a new file; nothing existing depends on it, so there is nothing to migrate or roll back beyond a normal `git rm NOTES.md`.

## Open Questions

None. The three baseline sections are fixed by the spec, the file location is fixed at the repository root, and there are no consumers to coordinate with in this generation.
