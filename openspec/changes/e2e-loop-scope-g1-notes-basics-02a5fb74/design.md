# Design

## Context

The repository is a documentation baseline: a one-line `README.md`, an empty
`.gitignore`, and an `orca-companion.json` configuration file. There is no build system,
no test runner, and no package manifest. See proposal.md for the motivation.

The scope envelope for this change allows writing exactly one file: `NOTES.md` at the
repository root. That constraint rules out the usual approach of also editing `README.md`
to link the new notes, and it rules out adding a lint or link-checker tool that would need
its own configuration and dependencies.

## Goals / Non-Goals

**Goals:**

- Produce a `NOTES.md` whose every factual claim can be checked against the repository.
- Keep the verification of that file to plain shell commands that run without any
  dependency the repository does not already have.

**Non-Goals:**

- Adding tooling, dependencies, or a continuous-integration configuration.
- Restructuring or renaming any existing file.
- Keeping `NOTES.md` in sync automatically; the file is maintained by hand like the rest
  of the repository's prose.

## Decisions

**Verify with POSIX shell commands rather than a test suite.** The repository has no test
runner and no package manifest, so introducing one would mean adding files outside the
scope envelope. The checks below are a sequence of `test`, `grep`, and `sed` invocations
that a reviewer can run directly in a shell.

Alternative considered: a small script committed alongside the notes. Rejected because it
adds an executable to the repository whose only job is to check a Markdown file, which is
more maintenance than the file itself.

**Use stable level-two headings as the section contract.** The spec requires the layout,
workflow, and conventions sections to be findable by topic, which makes the heading text
the thing worth asserting on. The checks therefore match on the headings rather than on
body wording, so the prose stays free to evolve.

Alternative considered: asserting on distinctive sentences from each section. Rejected
because it would make every rewording of the notes look like a spec violation.

**Check the groundedness requirement by enumerating paths and commands.** Rather than
trying to prove every sentence true, the verification extracts repository-relative paths
and inline commands out of `NOTES.md` and confirms each one exists or is runnable. That
turns the groundedness requirement into something checkable in a shell.

## Risks / Trade-offs

- [The file drifts from the repository as the repository changes] → Mitigation: the
  verification commands in tasks.md are cheap to re-run, and they fail loudly on a path
  that has been renamed or removed.
- [The groundedness checks depend on the format of `NOTES.md`] → Mitigation: constrain the
  writer to inline code spans for paths and commands, so the extraction patterns stay
  simple and predictable.
- [No link from `README.md` means the file is less discoverable] → Accepted for now; the
  scope envelope for this change does not permit touching `README.md`, and a follow-up
  change can add the pointer once it is in scope.

## Migration Plan

Not applicable. The change only adds a new file; there is nothing to migrate and removing
`NOTES.md` fully reverts it.
