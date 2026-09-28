# Notes

This file collects project notes for the `orca-companion` repository. It is the
canonical place to capture project context, document conventions, and record
observations that arise while implementing or reviewing a work package so that
the rationale stays discoverable for anyone working through the e2e-loop.

## Project Context

`orca-companion` is an end-to-end loop demonstration project for the orca-companion
agent harness. The repository currently ships only a short `README.md` and the
`orca-companion.json` configuration file, so contributors have no dedicated
surface to capture implementation rationale. The baseline `NOTES.md` provides a
single, predictable home for that content and lets future work packages extend
the file under the `project-notes` OpenSpec capability without altering the
readme or the harness configuration.

## Conventions

- Place the file at the repository root so it sits next to `README.md` and
  `orca-companion.json`, matching the conventions used by other GitHub-flavored
  documentation projects.
- Use plain Markdown: headings, paragraphs, and bullet lists only. Avoid
  embedded HTML, templating, or generated artifacts so the file stays
  diff-friendly across work packages.
- Keep the four fixed top-level headings (`# Notes`, `## Project Context`,
  `## Conventions`, `## Work Package Notes`) and add new sections only when a
  work package explicitly proposes them, rather than expanding the outline
  speculatively.
- When a topic outgrows `NOTES.md`, propose splitting it under its own
  capability rather than overloading this file.

## Work Package Notes

- `e2e-loop-scope#g1:notes-basics` introduces this baseline file with an
  introduction, project context, conventions, and an empty container section
  for follow-up entries. Later work packages should append their observations
  beneath this heading rather than replacing earlier content.
