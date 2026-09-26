# Tasks

## 1. NOTES.md Content Draft

- [ ] 1.1 Draft the "Project overview" section: a top-level Markdown title that
  identifies the document as project notes for the `orca-companion` e2e-loop
  demonstration project and a one-paragraph orientation.
- [ ] 1.2 Draft the "Maintainer scope rules" section, including the Work
  Package Scope Envelope rule for `proposal.md` `## Impact`, the
  `scope_envelope_exceeded` admission rejection name, and the
  dependency-change restriction that keeps follow-on changes self-contained.
- [ ] 1.3 Draft the "Contributor guidance" section, including where new
  change proposals live (`openspec/changes/<change-id>/`), the
  `proposal.md` / `tasks.md` / `specs/` expectations for a Specification
  Unit, the spec delta header rules (`## ADDED Requirements` / `## MODIFIED
  Requirements` / `## REMOVED Requirements` / `## RENAMED Requirements`),
  and the requirement that every requirement include at least one
  `#### Scenario:` block.
- [ ] 1.4 Draft the "Agent-facing conventions" section, including the
  recommended read-first order (`README.md` → `NOTES.md` → active change
  directory), the citation expectation (every non-trivial claim must point
  to a file path, heading, or line), and the explicit no-archive directive
  for planning dispatches.
- [ ] 1.5 Draft the "Self-containment" section, including the
  no-required-external-links rule and the rule that `NOTES.md` MUST NOT
  depend on content from later, not-yet-archived changes.

## 2. NOTES.md File Creation

- [ ] 2.1 Create `NOTES.md` at the worktree root using the drafted sections,
  in the order: Project overview → Maintainer scope rules → Contributor
  guidance → Agent-facing conventions → Self-containment.
- [ ] 2.2 Ensure `NOTES.md` is valid Markdown, begins with a single top-level
  title, and contains no required links to private or external systems.

## 3. Verification

- [ ] 3.1 Confirm `NOTES.md` exists at the worktree root and is tracked by
  git.
- [ ] 3.2 Confirm no other tracked file in the Work Package Scope Envelope
  (`NOTES.md`) is modified or removed, and no tracked file outside the
  envelope is added or modified by this change.
- [ ] 3.3 Run `openspec validate e2e-loop-scope-g1-notes-basics-02a5fb74
  --type change --strict` and confirm the change passes.
- [ ] 3.4 Confirm the change directory remains at
  `openspec/changes/e2e-loop-scope-g1-notes-basics-02a5fb74/` and has NOT
  been moved into `openspec/changes/archive/`.
