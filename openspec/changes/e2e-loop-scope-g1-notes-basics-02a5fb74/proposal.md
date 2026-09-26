## Why

The `orca-companion` repository currently only ships a short `README.md` plus
the harness configuration file (`orca-companion.json`). There is no
maintainer-facing note explaining the intent of the repository, what it is
explicitly _not_, or where follow-up work is tracked. Without such a note,
new contributors and automated agents have to infer the project's purpose
from the commit history and the harness configuration, which makes the
e2e-loop test fixture harder to reason about.

## What Changes

- Add `NOTES.md` at the repository root.
- `NOTES.md` MUST summarise the project's purpose as the `orca-companion`
  agent-harness e2e-loop demonstration target.
- `NOTES.md` MUST describe what the repository deliberately does _not_
  contain (no real product code, no real install instructions, no real
  configuration beyond the harness file).
- `NOTES.md` MUST point maintainers at the open issues / follow-up changes
  that drive future iterations of the demo.

## Impact

- `NOTES.md` (new file at repository root; the only path declared in the
  Work Package Scope Envelope).
- No existing code, configuration, or specification files are modified
  by this change.
