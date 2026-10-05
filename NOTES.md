# Project Notes

## Purpose

This repository is a documentation-and-specification workspace driven by
OpenSpec. It holds the specifications, proposals, and design notes that
describe how the project is intended to work, plus the contributor notes in
this file. There is no application source code, no build pipeline, and no
deployable artifact here yet: the tracked content is Markdown, YAML, and
placeholder files that keep the OpenSpec directory layout stable.

This file exists so a new contributor has one place to answer three questions:
what the repository is for, what they need installed, and where the
specifications live. `README.md` stays a short project blurb and does not
duplicate anything beyond its own title line.

## Requirements

- Git, to read history, review diffs, and commit changes on the working branch.
- A text editor that handles UTF-8 Markdown and YAML. The notes and specs are
  plain text files; no IDE-specific tooling is required.
- Familiarity with Markdown headings and bullet lists, which is the only file
  format used for prose here.
- Optional: a Markdown or YAML linter of your choice. Nothing in the
  repository depends on a particular linter, and no lint configuration is
  committed.
- Optional: the OpenSpec command-line tooling, if you want to validate or
  archive changes from the shell instead of following the manual workflow
  described below.

There is no package manifest, dependency lockfile, or test runner in this
repository, so there is nothing to install and no build step to run before you
can read or edit the documentation.

## Getting Started

Clone the repository and confirm the working tree is clean before you start:

```sh
git clone https://github.com/leike0813/orca-companion-test
git status
```

Then read the entry points in this order:

1. `README.md` for the project title.
2. `NOTES.md`, this file, for orientation and workflow.
3. `openspec/config.yaml` for the repository's OpenSpec context and rules.
4. The active change under `openspec/changes/` for the work currently in
   flight.

Common day-to-day commands:

```sh
git status --porcelain
git diff
git log --oneline -10
git switch -c add-change-notes
```

Create a new change directory under `openspec/changes/` when you start new
work, naming it after the change in short kebab-case:

```sh
mkdir -p openspec/changes/<change-name>
```

Archive a finished change by moving its directory into
`openspec/changes/archive/` once its tasks are complete and its spec delta has
been folded into `openspec/specs/`.

## Repository Layout

- `NOTES.md` — this file, the contributor orientation notes.
- `README.md` — the project blurb; intentionally short.
- `.gitignore` — where build and editor artifacts are excluded. It currently
  holds no rules, so every file in the repository is visible to review.
- `openspec/config.yaml` — declares the OpenSpec schema and the repository
  context that every change inherits.
- `openspec/changes/` — one directory per in-flight change, each holding a
  proposal, design, task list, and a spec delta in a specs subdirectory.
- `openspec/changes/archive/` — the destination for changes that are finished
  and archived.
- `openspec/specs/` — the durable, archived specifications that describe the
  current agreed behaviour of the project.

Directory conventions worth knowing:

- Each change directory is named after its change in short kebab-case and
  holds a proposal, a design note, a task list, and a specs subdirectory whose
  capability folders carry the spec delta.
- Placeholder files keep otherwise empty directories such as
  `openspec/specs/` and `openspec/changes/archive/` present in version control.
- Work is done on a branch and merged through review; the repository has no
  release or tagging process to learn yet.

## OpenSpec Workflow

OpenSpec governs how this repository changes. Every behavioral change begins as
a change proposal and ends as an archived specification, and the summary of
those rules lives in `openspec/config.yaml`.

The stages of a change are:

1. **Proposal** — record the problem in the change's proposal file, the
   approach in its design file, and the deliverable as a spec delta in the
   capability folder under the change's specs subdirectory. The delta states
   requirements as ADDED, MODIFIED, or REMOVED blocks, with scenarios written
   as WHEN/THEN conditions.
2. **Planning** — break the work into numbered tasks in the change's task list.
   Each task names the files it touches and the command that verifies it, so
   progress is checkable rather than a matter of opinion.
3. **Implementation** — make the smallest change that satisfies the tasks and
   the spec delta, keeping each task's verification command green as you go.
4. **Validation** — re-read the spec delta against the delivered work and
   repair anything that drifted before the change is merged.
5. **Archiving** — once the tasks are complete, fold the delta into
   `openspec/specs/` and move the change directory into
   `openspec/changes/archive/` so `openspec/changes/` only ever shows work in
   progress.

The change that introduced this file and the project-notes capability is
currently in flight at
`openspec/changes/e2e-loop-scope-g1-notes-basics-02a5fb74/`; after archiving,
its project-notes spec delta lives under `openspec/specs/`.

Keep specification and notes text free of placeholder markers, and keep every
path a document mentions real: both rules are part of the acceptance criteria
for the project-notes capability and are checked by reviewing the file and
resolving the paths it names.
