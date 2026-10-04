# Proposal

## Why

`README.md` is a single line — the project title and nothing else. That was a deliberate choice, and `NOTES.md` now carries the project's basics, so the README is not missing documentation. The problem is different: the README is indistinguishable from the README of any ordinary project, and it is the first file every reader and every agent opens. A reader who arrives cold has no way to tell that this is a recovered worktree still under recovery, that it deliberately contains no product code yet, or that `NOTES.md` is where the actual state is recorded. The absence of a codebase is exactly the kind of fact that is misread as a lost repository when nothing says otherwise.

A short banner directly under the title closes that gap. It is a status line, not a second documentation site: it says what state the project is in and points at the file that holds the detail, without restating any of it.

## What Changes

- Add a short banner to `README.md`, directly beneath the existing project title, that states the project's recovery status: this is a recovered Orca worktree, recovery work is specified under `openspec/changes/`, and no product code exists yet.
- Point the banner at `NOTES.md` as the single place where the project basics, the companion configuration, the working agreements, and the open recovery items are recorded, and at `openspec/changes/` for the outstanding specified work.
- Keep the banner a pointer rather than a copy: it MUST NOT restate `NOTES.md`, MUST NOT embed the Orca companion configuration, and MUST NOT grow into a section-structured document of its own.
- Add no product code, no build tooling, and no dependency changes. The only repository file this change touches is `README.md`.

## Capabilities

### New Capabilities

- `readme-banner`: The repository's `README.md` opens with the project title followed by a short, greppable status banner that declares the project's recovery state, names the absence of product code, and points to the notes file and the in-flight change directory as the sources of detail — verifiable with a single read-only shell command.

### Modified Capabilities

None. `readme-banner` is the first capability governing `README.md` in this repository; there is no existing `openspec/specs/` inventory to amend.

## Impact

- Affected file: `README.md` — the existing file at the repository root, which gains a banner block beneath its current title heading. It is the only product path this change creates or modifies, and the only path in this change's impact.
- No APIs, packages, dependencies, build configuration, or runtime systems are touched.
- No other repository file is created, edited, renamed, or deleted by this change.
- Verification is a read-only command (`test -f README.md` plus heading and pointer greps), so acceptance introduces no build or test dependency.
