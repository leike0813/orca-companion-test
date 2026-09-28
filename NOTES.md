# Notes

This file collects project notes for the orca-companion repository. It is the
stable, in-repo home for context, conventions, and observations that span
multiple work packages, so contributors do not have to dig through commit
history or chat transcripts to understand why the project is shaped the way it
is. Update the sections below whenever a new work package produces information
that future contributors will need.

## Project Context

The orca-companion project is an end-to-end loop demonstration for the Orca
multi-agent IDE. It currently ships three files at the repository root: a short
`README.md` that introduces the project, an `orca-companion.json` configuration
that drives the coordinator model and execution harness, and a `.gitignore`
that keeps the working tree tidy. There are no source files, build scripts, or
test suites yet; later work packages will layer them on top of this baseline.
Until those arrive, the repository exists primarily as a sandbox for exercising
the OpenSpec-driven workflow that Orca coordinates.

## Conventions

Files at the repository root are written in plain UTF-8 text and use
GitHub-flavored Markdown where formatting is required. Configuration lives in
JSON or YAML and is committed alongside the code it controls rather than
generated at runtime. The `openspec/` directory holds every change proposal,
specification delta, design note, and task list managed by OpenSpec, and it is
treated as the source of truth for in-flight and archived work. Branches that
arrive from a work package dispatch must stay focused on the scope envelope of
the change they implement; out-of-scope edits should be deferred to a separate
work package rather than folded in opportunistically.

## Work Package Notes

Work package `e2e-loop-scope#g1:notes-basics` establishes this baseline
`NOTES.md` so future documentation changes have a predictable surface to
extend. The section outline introduced here (`# Notes`, `## Project Context`,
`## Conventions`, `## Work Package Notes`) is intentionally minimal; later work
packages may add entries under `## Work Package Notes` to record observations
specific to their own scope without expanding the top-level structure. If a
future change needs a new baseline section, it should propose that addition
under its own OpenSpec capability rather than mutating this baseline silently.
