# Project Notes

These notes record the basics of the repository: what the project is, how the
tree is laid out, and which commands to run. They intentionally cover only the
essentials; deep architecture and onboarding material lives elsewhere.

## Overview

This is a spec-driven development workspace. Work is proposed and described in
OpenSpec before any code changes: each unit of work is written up as a change
containing a proposal, a design, a task list, and a spec delta, and that change
is implemented and validated before it is archived into the main specs. The
repository ships no application code or build system at this point; the
`openspec/` directory is the entire working surface, and the top-level
`README.md` is a one-line project header.

## Repository Layout

- `openspec/` - the OpenSpec workspace that holds all project specifications
  and in-flight changes.
- `openspec/changes/` - one directory per in-flight change proposal. Each holds
  the proposal, design, task list, and its spec deltas, plus a `.openspec.yaml`
  file recording the schema and goal for that change.
- `openspec/changes/archive/` - changes that have been completed and archived.
  Archived changes are kept for history; their requirements have been folded
  into the main specs.
- `openspec/specs/` - the main capability specs, after `openspec archive` has
  merged archived change deltas into them.
- `README.md` - the one-line project header at the repository root.

## Commands

The following OpenSpec commands are the everyday tools. Run them from the
repository root.

List the in-flight changes and their task progress:

```sh
openspec list
```

List the main capability specs:

```sh
openspec list --specs
```

Validate a change against its spec deltas:

```sh
openspec validate e2e-loop-scope-g1-notes-basics-02a5fb74
```

`openspec validate` exits 0 when the change is valid and non-zero with a list of
problems otherwise, so it can be used directly as a check in a script.
