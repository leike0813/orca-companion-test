## Purpose

The `notes-basics` capability defines the `NOTES.md` developer notes
that anchor downstream agents and humans to the current state of the
`orca-companion` baseline. It locks in where `NOTES.md` lives, which
sections it must contain, what durable surfaces it must reflect, and
how future Work Packages keep it in sync as the project evolves.

## ADDED Requirements

### Requirement: `NOTES.md` lives at the repository root
The repository MUST contain a top-level `NOTES.md` file whenever the
`notes-basics` capability is in effect. There SHALL be exactly one
`NOTES.md`, placed at the repository root (not nested under any
subdirectory).

#### Scenario: Inspecting the repository root
- **WHEN** a reader (human or agent) lists the contents of the
  repository root
- **THEN** a single `NOTES.md` file SHALL be present
- **AND** there SHALL be no second file named `NOTES.md` elsewhere
  in the repository

#### Scenario: Absent `NOTES.md`
- **WHEN** the `notes-basics` capability applies and `NOTES.md` is
  missing from the repository root
- **THEN** the repository SHALL be considered out of conformance

### Requirement: `NOTES.md` content sections
`NOTES.md` SHALL be valid CommonMark and SHALL organize its content
into the following top-level sections, in this order: `Project
Purpose`, `Repository Layout`, `\`orca-companion.json\`
Configuration`, `Current Baseline`, `Conventions for Future Changes`.

Each section MUST be present as a level-2 Markdown heading (for
example `## Project Purpose`). Sections MAY contain subsections,
lists, or tables beneath them; they MUST NOT be empty.

#### Scenario: Sections are present and ordered
- **WHEN** a reader parses `NOTES.md` for its `##`-level headings
- **THEN** the five required headings SHALL appear
- **AND** they SHALL appear in the order listed in this requirement
- **AND** each heading SHALL be followed by at least one non-blank
  line of body content

#### Scenario: Section is missing
- **WHEN** `NOTES.md` omits one of the required top-level sections or
  places it out of order
- **THEN** the file SHALL be considered out of conformance
- **AND** the missing or reordered section SHALL be cited by name in
  the remediation message

### Requirement: `Notes` content contract reflects the baseline
The `Project Purpose`, `Repository Layout`, and `Current Baseline`
sections of `NOTES.md` MUST faithfully describe the project as it
exists at the moment `NOTES.md` is updated. Specifically:

- `Project Purpose` SHALL identify the project as the
  `orca-companion` end-to-end loop demonstration target and reference
  the Orca agent harness as the orchestrating system.
- `Repository Layout` SHALL list every tracked file at the
  repository root and describe its role in plain language.
- `Current Baseline` SHALL record the current baseline commit SHA
  (the tip of the branch when the change is applied) as a
  fenced-code-block SHA with a short summary of what that commit
  contains.

#### Scenario: Baseline commit is recorded
- **WHEN** a reader reads the `Current Baseline` section
- **THEN** they SHALL find a fenced `git` or `text` block containing
  the 40-character commit SHA at the tip of the branch
- **AND** a one-line summary explaining the baseline commit's
  contents

#### Scenario: Repository Layout lists every root file
- **WHEN** a reader cross-references `Repository Layout` against
  `git ls-tree -r HEAD --name-only | awk -F/ '{print $1}' | sort -u`
- **THEN** every unique top-level path returned by that command
  SHALL be mentioned in `Repository Layout`

### Requirement: `Notes` documents the `orca-companion.json` configuration
The `\`orca-companion.json\` Configuration` section SHALL describe the
keys declared in `orca-companion.json` that materially affect how
agents execute against this worktree: at minimum
`execution.harness`, `execution.workerModel`, `execution.codexSandbox`,
`execution.git.remotes`, `execution.git.refs`,
`execution.limits.maxActiveWorkPackages`,
`execution.limits.concurrencyLimit`, and
`execution.acceptedRisks`. Each key SHALL be summarised in one
sentence, and no key referenced by the section may be removed from
`orca-companion.json` without a corresponding OpenSpec change.

#### Scenario: Configuration key is documented
- **WHEN** a reader inspects the `orca-companion.json` root
- **THEN** for each key listed in this requirement there SHALL be a
  matching one-sentence summary in the configuration section
- **AND** the summary SHALL be accurate against the current value
  in `orca-companion.json`

#### Scenario: Configuration drift
- **WHEN** a key listed in this requirement is added, renamed, or
  removed in `orca-companion.json`
- **THEN** that change MUST be accompanied by an OpenSpec change
  whose `MODIFIED Requirements` block updates this requirement
  before it is admitted

### Requirement: `NOTES.md` states conventions for future changes
The `Conventions for Future Changes` section SHALL state, in plain
language, that future Work Packages are expected to (a) author their
changes through OpenSpec, (b) keep their Scope Envelope narrow and
declarative, and (c) keep `NOTES.md` in sync with whatever durable
context it references — in particular the baseline commit SHA and
the contents of `orca-companion.json`.

#### Scenario: Future-change conventions are present
- **WHEN** a reader inspects the `Conventions for Future Changes`
  section
- **THEN** they SHALL find explicit guidance covering all three
  obligations (OpenSpec authoring, narrow Scope Envelope, and
  `NOTES.md` synchronisation)

#### Scenario: New durable surface appears
- **WHEN** a new durable project surface (file, config key,
  external system, etc.) is added beyond what `NOTES.md` describes
- **THEN** an OpenSpec change SHALL be opened to update
  `notes-basics` so that `NOTES.md` and the spec stay aligned
