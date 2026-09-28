## Scope

This repository hosts the orca-companion agent harness and the supporting
fixtures used to exercise its end-to-end dispatch loops. Work under way
here is limited to the harness configuration, the OpenSpec change that
drives each iteration, and the developer notes captured in this file.
Anything outside that surface — productionising the harness, packaging
releases, integrating with downstream orchestrators, or adding
user-facing product copy beyond the existing [README.md](README.md)
placeholder — is explicitly out of scope for now and will be picked up
by separate changes with their own proposals.

## Intent

The project exists to demonstrate, in a minimal and reproducible shape,
how a planning agent, an implementation worker, and a validator
cooperate through the orca orchestration protocol. Each generation of
the change graph is meant to add exactly one self-contained artifact
so that the lifecycle from proposal to merged change can be observed
step by step. Readers should be able to clone the repository, read
this file together with [README.md](README.md), and understand both
what the harness does and why the change-driven cadence was chosen.

## Conventions

Every change that lands in this repository MUST travel as an OpenSpec
change directory under `openspec/changes/` and MUST respect the scope
envelope declared in its proposal — touching only paths listed in
`include` and none of the paths listed in `exclude`. Contributors MUST
not copy prose verbatim between `README.md` and `NOTES.md`; the two
files are complementary, with `README.md` holding the user-facing
overview and `NOTES.md` holding the internal developer-facing record.
Validation of any change MUST be performed with `openspec validate`
and `openspec status` before the change is reported as done.
