# Project Notes

## Project

`orca-companion` is an end-to-end loop demonstration project for the
Orca multi-agent harness. The repository currently ships a placeholder
`README.md`, an `.gitignore`, an `orca-companion.json` manifest that
declares the project's coordinator and worker configuration, and an
`openspec/` directory that records the planned work through OpenSpec
change proposals. The aim of this repository is to exercise the
planner / implementation / validator / finalizer loop on a tiny but
real codebase rather than to ship a finished product.

## Status

The repository is at its isolated baseline (`8fa47ad`). It contains
only the files needed to start the planning loop: the placeholder
`README.md`, the empty `.gitignore`, and the `orca-companion.json`
harness manifest. No production code, tests, or third-party
dependencies are present yet. All planned work is recorded as
OpenSpec change proposals under `openspec/changes/`.

## Next Steps

The following OpenSpec change is currently active and will land next:

- `e2e-loop-scope-g1-notes-basics-02a5fb74` — Add this top-level
  `NOTES.md` file as the baseline orientation document for the
  repository.

Once that change ships, future changes will extend `NOTES.md` rather
than the placeholder `README.md`, and additional capabilities will be
introduced through further OpenSpec proposals.

## References

For further information about this project, see:

- `README.md` — the formal landing page and project description.
- `orca-companion.json` — the harness manifest that declares the
  coordinator and worker models, planning limits, and execution
  configuration.
- `openspec/` — the directory of OpenSpec change proposals and
  archived changes that document planned and completed work.
