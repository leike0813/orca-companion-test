# Notes

This file collects project notes for `orca-companion` — implementation rationale,
working conventions, and ongoing observations from individual work packages.
It complements `README.md` (which stays focused on introducing the project) and
`orca-companion.json` (which carries the harness configuration), and serves as
the single in-repo surface that downstream work packages can extend without
touching either of those files.

## Project Context

`orca-companion` is the end-to-end demonstration project for the Orca
multi-agent harness. The repository currently ships three root-level files —
`.gitignore`, `README.md`, and `orca-companion.json` — together with the
`openspec/` directory that holds the change proposals driving each work
package. The project intentionally keeps the root surface small so that every
new addition is justified by a scoped change rather than ad-hoc growth.

The `orca-companion.json` file pins the harness configuration: it declares the
coordinator model (`MiniMax-M3`), the worker model, the Codex sandbox policy,
the git remote/refs the harness may touch, and the execution limits that bound
how many work packages, attempts, or recoveries a single Dispatch may consume.
`openspec/` then captures the per-change artifacts (`proposal.md`, `design.md`,
`specs/<capability>/spec.md`, `tasks.md`) that planners, implementers,
validators, and finalizers all read from.

The change pipeline is spec-driven: every work package is described as an
OpenSpec change with its own capability path, its Scope Envelope restricts the
files the implementation may touch, and the validator checks that the diff
stays inside that envelope. This `NOTES.md` is itself introduced by such a
change (`project-notes` capability), so future documentation work can extend
it under the same capability without redefining the file's location.

## Conventions

- **Single file at the repository root.** `NOTES.md` lives next to `README.md`
  and `orca-companion.json`. It is plain GitHub-flavored Markdown; no embedded
  HTML, templating, or generated artifacts. The intent is to keep the file
  reviewable in any editor and diff-friendly across work packages.
- **Fixed top-level section outline.** The file uses `# Notes` followed by
  `## Project Context`, `## Conventions`, and `## Work Package Notes` in that
  order. Each section begins with at least one paragraph of prose so the
  outline is observable from the `project-notes` spec without reading the
  underlying intent. New top-level sections must be introduced by a future
  OpenSpec change rather than added speculatively.
- **Work package notes are append-only.** Each entry under `## Work Package
  Notes` identifies its work package (for example, the OpenSpec change ID) and
  records what was learned, decided, or deliberately deferred. Entries are
  never edited or removed retroactively; superseding notes go in a later
  entry so the history stays intact.
- **Scope Envelope respect.** Changes to this file must be authorized by an
  OpenSpec change whose Scope Envelope includes `NOTES.md`. Implementation
  workers must not edit it as a side effect of an unrelated change, and
  validators must flag any diff that escapes the declared envelope.
- **Plain language, no marketing copy.** Notes describe what the project is
  and how it is being built, not aspirations or roadmap promises. Keep the
  prose concrete and self-contained so each entry stands on its own.

## Work Package Notes

### e2e-loop-scope#g1:notes-basics

Introduces the baseline `NOTES.md` alongside the new `project-notes` OpenSpec
capability. The change is additive: it does not modify `README.md`,
`orca-companion.json`, `.gitignore`, or any file outside the declared Scope
Envelope. Establishes the four-heading outline (`# Notes`, `## Project
Context`, `## Conventions`, `## Work Package Notes`) that later work packages
will extend. No follow-up actions are required from this change — downstream
work packages simply append their own entries under `## Work Package Notes`
when they have observations worth recording.
