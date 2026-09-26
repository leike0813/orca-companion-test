## 1. Authoring NOTES.md

- [ ] 1.1 Create `NOTES.md` at the repository root with a clear top-level
      heading identifying it as the maintainer notes file for
      `orca-companion`.
- [ ] 1.2 Add a "Purpose" section restating that the repository exists as
      an e2e-loop demonstration target for the `orca-companion` agent
      harness.
- [ ] 1.3 Add a "What this repo is _not_" section that lists the kinds of
      content the repository deliberately does not carry (production
      code, install instructions, multi-component configurations,
      secrets, real credentials).
- [ ] 1.4 Add a "Where follow-up work lives" section pointing at the
      GitHub issues / follow-up OpenSpec changes that drive future
      iterations of the demo.
- [ ] 1.5 Confirm `NOTES.md` renders as plain Markdown with no
      front-matter, no embedded HTML, and no fenced code blocks longer
      than the explanatory samples included in the file.

## 2. Validation

- [ ] 2.1 Run `openspec validate e2e-loop-scope-g1-notes-basics-02a5fb74
      --strict` (or equivalent manual checklist when OpenSpec is not
      initialised in the worktree) and confirm there are no findings.
- [ ] 2.2 Confirm the change's `## Impact` section references only
      `NOTES.md`, which is the single path declared in the Work Package
      Scope Envelope.
- [ ] 2.3 Confirm no file other than `NOTES.md` and the
      `openspec/changes/...` artefacts created by this change has been
      added or modified in the working tree.
