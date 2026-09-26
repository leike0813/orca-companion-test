# Notes

## Project Purpose

The `orca-companion` repository exists as the harness-side target used by the
e2e-loop demos: it gives the orchestrator a small, isolated workspace where
each work-package dispatch can add or extend a single artifact and where the
planner, implementer, validator, and finalizer roles can be exercised
end-to-end without touching unrelated code.

## Current Status

Only the bootstrap commit is in place. A sparse `README.md` and the
`orca-companion.json` configuration ship today; the first notes work
package introduces this `NOTES.md` so later changes have a baseline to
build on. Sections such as installation, usage, and operational
guidance are deliberately deferred to subsequent work packages.
