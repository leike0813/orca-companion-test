# Add NOTES.md With Project Basics

## Why

The `orca-companion` e2e-loop demonstration project ships with only a short
`README.md` placeholder and no companion notes file. New readers and dispatched
agents onboarding the repository have nowhere to look for maintainer scope
rules, contributor guidance, or agent-facing conventions beyond the brief
`README.md` sentence that promises "more sections (Installation, Usage, etc.)
will be added in later changes."

`NOTES.md` will become the durable home for project-basics material that does
not belong on the landing page: maintainer scope rules enforced by the Orca
companion harness, contributor guidance for opening follow-on changes, and
agent-facing conventions dispatched workers must follow. Putting these notes
behind their own file keeps `README.md` focused on orientation while making
the same facts easy to locate, reference, and validate from a single document.

## What Changes

- Add `NOTES.md` at the worktree root as a Markdown document covering project
  basics for the `orca-companion` e2e-loop demonstration project.
- Cover the maintainer scope rules referenced by the Orca companion harness:
  Work Package Scope Envelope rules, `scope_envelope_exceeded` admission
  rejection, and the dependency-change restriction that keeps follow-on
  changes self-contained.
- Cover contributor guidance for opening follow-on OpenSpec changes: where
  new specs live, how `proposal.md`, `tasks.md`, and `specs/` are expected to
  be structured, and what `proposal.md`'s `## Impact` may reference.
- Cover agent-facing conventions: a recommended read-first order, citation
  expectations, and the explicit no-archive directive that applies while a
  worker is operating inside a planning dispatch.
- Keep `NOTES.md` self-contained: no required links to private or external
  systems, no content that depends on later changes landing first.

## Capabilities

### New Capabilities

- `notes-basics`: Project-basics content delivered through `NOTES.md`,
  covering maintainer scope rules, contributor guidance, and agent-facing
  conventions for the `orca-companion` e2e-loop demonstration project.

### Modified Capabilities

None.

## Impact

- Adds `NOTES.md` at the worktree root.
- Does not modify any other tracked file, dependency, script, or runtime
  state inside or outside this Work Package Scope Envelope.
