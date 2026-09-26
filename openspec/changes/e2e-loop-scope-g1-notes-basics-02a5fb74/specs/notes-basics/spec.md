## ADDED Requirements

### Requirement: NOTES.md exists at worktree root

The `orca-companion` e2e-loop demonstration project SHALL provide `NOTES.md`
at the worktree root as a Markdown document covering project basics.

#### Scenario: NOTES.md is present at the worktree root

- **WHEN** a reader or agent lists the worktree root
- **THEN** `NOTES.md` SHALL exist
- **AND** it SHALL be a non-empty Markdown file

#### Scenario: NOTES.md begins with a top-level title

- **WHEN** a reader opens `NOTES.md`
- **THEN** the first line SHALL be a top-level Markdown title (`# ...`)
- **AND** the title SHALL identify the document as project notes for the
  `orca-companion` e2e-loop demonstration project

### Requirement: NOTES.md covers maintainer scope rules

`NOTES.md` SHALL document the maintainer scope rules enforced by the Orca
companion harness, including the Work Package Scope Envelope rule that the
`## Impact` section of a `proposal.md` may only reference paths inside the
envelope, and the `scope_envelope_exceeded` admission rejection that fires
when that rule is broken.

#### Scenario: Maintainer scope rules section is present

- **WHEN** a reader consults the maintainer scope rules section of `NOTES.md`
- **THEN** that section SHALL exist under a stable heading
- **AND** it SHALL explain the Work Package Scope Envelope rule for
  `proposal.md` `## Impact`
- **AND** it SHALL name `scope_envelope_exceeded` as the admission rejection

#### Scenario: Dependency-change restriction is documented

- **WHEN** a reader consults the maintainer scope rules section of `NOTES.md`
- **THEN** the section SHALL explain that follow-on changes MUST NOT add,
  remove, or rewrite declared dependencies outside their Work Package Scope
  Envelope

### Requirement: NOTES.md covers contributor guidance

`NOTES.md` SHALL document contributor guidance for opening follow-on OpenSpec
changes, including where new specs live, how `proposal.md`, `tasks.md`, and
`specs/` are expected to be structured, and what `proposal.md`'s `## Impact`
must reference.

#### Scenario: Contributor guidance section is present

- **WHEN** a reader consults the contributor guidance section of `NOTES.md`
- **THEN** that section SHALL exist under a stable heading
- **AND** it SHALL point to `openspec/changes/<change-id>/` as the location
  for new change proposals
- **AND** it SHALL describe the `proposal.md`, `tasks.md`, and `specs/`
  expectations for a Specification Unit
- **AND** it SHALL restate that `## Impact` may only reference paths inside
  the current Work Package Scope Envelope

#### Scenario: Spec delta structure is documented

- **WHEN** a reader consults the contributor guidance section of `NOTES.md`
- **THEN** the section SHALL explain that capability folders under
  `specs/<capability>/spec.md` MUST use `## ADDED Requirements` (or
  `## MODIFIED Requirements` / `## REMOVED Requirements` / `## RENAMED
  Requirements`) and that every requirement MUST include at least one
  `#### Scenario:` block

### Requirement: NOTES.md covers agent-facing conventions

`NOTES.md` SHALL document the agent-facing conventions for dispatched workers
operating in this repository, including a recommended read-first order, a
citation expectation, and the explicit no-archive directive that applies
during a planning dispatch.

#### Scenario: Agent-facing conventions section is present

- **WHEN** a dispatched agent consults `NOTES.md`
- **THEN** it SHALL find an agent-facing conventions section under a stable
  heading
- **AND** that section SHALL recommend a read-first order starting with
  `README.md`, then `NOTES.md`, then the active change directory under
  `openspec/changes/`
- **AND** it SHALL state the citation expectation: every non-trivial claim
  must point to a file path, a heading, or a line inside the active change
- **AND** it SHALL state that a worker operating inside a planning dispatch
  MUST NOT execute `openspec archive` and MUST NOT move the change into
  `openspec/changes/archive/`

#### Scenario: No-archive directive is unambiguous

- **WHEN** a worker reads the agent-facing conventions section of `NOTES.md`
- **THEN** the section SHALL treat the no-archive directive as a hard rule,
  not a suggestion
- **AND** it SHALL NOT carve out silent exceptions for partial completion or
  failed validation

### Requirement: NOTES.md stays self-contained

`NOTES.md` SHALL remain self-contained so it can be read without resolving
links to private or external systems and SHALL NOT depend on later changes
landing first.

#### Scenario: NOTES.md has no required external references

- **WHEN** a reader follows the links inside `NOTES.md`
- **THEN** every required link SHALL resolve within the worktree
- **AND** no required link SHALL point to a private system or an external
  service that is not part of the public repository

#### Scenario: NOTES.md does not depend on later changes

- **WHEN** `NOTES.md` is read in isolation, before any change in the
  `e2e-loop-scope` series has been archived
- **THEN** every statement in `NOTES.md` SHALL remain true
- **AND** no statement SHALL depend on content that is promised by a later
  but not-yet-archived change
