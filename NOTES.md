# NOTES

## Project

`NOTES.md` is the project's working orientation document: a short,
human-authored "first read" that sits next to `README.md` so newcomers
can understand the repo's intent without having to dig through tooling
or manifests. It complements the placeholder `README.md` and the
`orca-companion.json` harness manifest, and it is intentionally
distinct from both.

## Status

The repository is at its baseline: only `README.md`, `.gitignore`,
`orca-companion.json`, and the `openspec/` skeleton exist at the top
level. No application code, tests, or CI configuration have landed yet;
this is the starting point from which subsequent OpenSpec changes will
extend the project.

## Next Steps

The next planned work is tracked as OpenSpec changes under
`openspec/changes/`. The currently active change is:

- `e2e-loop-scope-g1-notes-basics-02a5fb74` — introduce this
  `NOTES.md` file as the baseline orientation document.

Future changes will build on this baseline; their identifiers will be
appended to this section as they are added.

## References

For authoritative information beyond this orientation page, see:

- `README.md` — the formal landing page for the project; placeholder
  copy today, will grow in later changes.
- `orca-companion.json` — the harness manifest that declares the
  coordinator models, tracker, planning limits, and execution
  configuration used by the Orca orchestration loop.
- `openspec/` — the directory of OpenSpec specs and changes; this is
  where proposed and in-flight work is specified, reviewed, and
  archived.
