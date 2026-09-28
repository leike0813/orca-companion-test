# Design

## Context

The orca-companion repository starts life with only `README.md`, `orca-companion.json`, and
an empty `.gitignore`. There is no agreed-upon place to record project context or
contributor conventions. This change adds the first such place — a root-level `NOTES.md` —
before any other content edits land.

## Goals / Non-Goals

**Goals:**

- Establish a stable, repository-root `NOTES.md` document.
- Capture the minimum information the rest of the e2e loop needs: what this project is,
  how contributors are expected to behave, and where active change artifacts live.

**Non-Goals:**

- Reorganize existing files (no changes to `README.md`, `orca-companion.json`, or
  `.gitignore`).
- Add new tooling, scripts, or build configuration.
- Replace or compete with `README.md`; `NOTES.md` is complementary contributor notes.
- Extend the notes surface beyond a single root-level file.

## Decisions

- **Single file at the repository root.** `NOTES.md` is added at the worktree root so it is
  immediately visible to anyone browsing the repository, alongside `README.md`.
- **Three sections only.** Project Context, Conventions, and E2E Loop. The set is the
  smallest one that satisfies the spec requirements without overspecifying future content;
  later Work Packages can extend `NOTES.md` if needed.
- **Plain Markdown, no embedded automation.** No links are wired into tooling, no
  preprocessors are introduced, and no section is machine-consumed in this change. This
  keeps the change purely documentary and free of hidden side effects.
- **Complementary to `README.md`.** `README.md` already states that more sections will be
  added in later changes; `NOTES.md` is the first such follow-on and is not a substitute
  for `README.md`.

## Risks / Trade-offs

- **Documentation drift.** Because `NOTES.md` is prose and not generated, future edits
  could let it drift from the actual harness behaviour. The E2E Loop section is therefore
  kept intentionally short and references the harness by name rather than describing
  detailed mechanics.
- **Over-extending the file.** Without explicit non-goals, contributors might be tempted
  to fold in installation, usage, or roadmap sections that belong in later Work Packages.
  The non-goals section explicitly defers those.
