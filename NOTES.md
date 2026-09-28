# Project Notes

This repository is a small demonstration project for the orca-companion agent
harness: it holds the harness configuration and the change documents that
drive the harness's planning, implementation, and validation loop. It is not a
library, a service, or an application with a runtime — nothing here is built,
published, or executed as part of a release.

The one-line description lives in `README.md`; this document fills in the
basics that `README.md` defers to later changes.

## Repository Layout

The repository root contains four files:

- `README.md` — the short project description.
- `NOTES.md` — this document.
- `orca-companion.json` — harness configuration: coordinator model and
  credential references, the tracker binding, planning and context limits,
  execution settings (harness, worker model, git refs), and concurrency
  limits.
- `.gitignore` — currently empty, so nothing is ignored yet.

Apart from `.git`, the one project directory is:

- `openspec/` — the change proposals the harness works through. Each change
  lives in its own directory under `openspec/changes/` and holds a proposal, a
  design, a task list, and a spec delta describing the requirements it adds.
  The change currently in flight is
  `openspec/changes/e2e-loop-scope-g1-notes-basics-02a5fb74/`.

## Verification

There is no test runner, build script, or linter in this repository. A reviewer
verifies it with standard shell checks against the working tree:

- Confirm the document is present and non-empty:

      test -s NOTES.md

- Confirm it has exactly one top-level title:

      grep -c '^# ' NOTES.md

- Confirm a required section has a non-empty body (substitute any `##`
  heading):

      awk '/^## Verification/{f=1;next} /^## /{f=0} f' NOTES.md | grep -q '[^[:space:]]'

- Confirm every path named in the Repository Layout section resolves. The
  section below is the list to test against the repository root:

      for p in README.md NOTES.md orca-companion.json .gitignore \
               openspec openspec/changes \
               openspec/changes/e2e-loop-scope-g1-notes-basics-02a5fb74; do
        test -e "$p" || echo "dangling: $p"
      done

- Confirm the working tree matches what this document describes:

      ls -a

- Confirm a change stayed in scope by reviewing what it touched:

      git status --porcelain

Because `NOTES.md` records the tree as of the revision it is written against,
re-run these checks whenever the root entries or the change set changes.
