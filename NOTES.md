# Working notes

Basic conventions for this repository. Every claim here is checkable against the tree.

## Repository layout

The project is documentation-first and has no build system, test runner, or package manifest.
The repository root holds `README.md`, `.gitignore`, this file, the `openspec/` directory, and
`orca-companion.json`, which is written by the Orca worktree tooling rather than by hand.

- `openspec/config.yaml` declares `schema: spec-driven` and holds the project context and
  per-artifact rules that guide how changes are written.
- `openspec/changes/` holds one directory per change.
- `openspec/specs/` holds the accepted specs. It currently contains no accepted spec, since no
  change has been archived yet.

## The OpenSpec change flow

Changes are specified before they are applied. Each directory under `openspec/changes/` carries a
`proposal.md` explaining the motivation and the impact, a `design.md` recording the decisions and
trade-offs, a `tasks.md` listing the work, and a `specs/` directory holding the requirement
changes for the capability being touched. Work then follows `tasks.md`, and the directory is
moved to `openspec/changes/archive/` once the tasks are complete and the specs are synced into
`openspec/specs/`.

## Conventions a change follows

- A change only edits the paths inside its declared scope. The scope is listed in the change's
  `proposal.md` under Impact, and a change that needs to touch another path declares that path
  first rather than widening its edits implicitly.
- A change that describes a convention in this file updates this file in the same change as the
  convention itself. If a change adds, moves, or removes something described here, this file is
  edited alongside it.
- Planning detail stays in the change directory. Proposal, design, spec, and task content is not
  copied into this file, which stays a short conventions-only document.
- Only files that exist are referenced. A path named here must resolve in the repository at the
  commit that mentions it.
