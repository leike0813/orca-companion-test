# Tasks

## 1. Authoring the README banner

- [ ] 1.1 Insert an internal-use banner as the first content block in
      `README.md`, immediately after the existing `# orca-companion`
      title, and verify by re-reading `README.md` that the banner
      appears before the one-line project description.
- [ ] 1.2 Make the banner explicitly identify the repository as the
      `orca-companion` agent-harness e2e-loop demonstration target and
      verify by re-reading the banner text that the project name and
      the phrase "e2e-loop demonstration target" both appear.
- [ ] 1.3 Add an out-of-scope notice inside the banner stating that the
      repository is _not_ a real product, has no install path, and has
      no end-user surface, and verify by re-reading the banner text
      that the notice covers all three points.
- [ ] 1.4 Confirm the banner stays plain GitHub-flavored Markdown: no
      HTML, no image syntax, no YAML/TOML front-matter, and no fenced
      build-step directives, by visually scanning the file and running
      `head -n 5 README.md` to confirm there is no front-matter.
- [ ] 1.5 Re-word or re-order the existing one-line description and the
      italic "more sections" note so the banner reads first, and verify
      by re-reading the full `README.md` from top to bottom that the
      banner precedes every other prose block.

## 2. Validation

- [ ] 2.1 Run `openspec validate
      e2e-loop-scope-g1-readme-banner-c0e65d23 --strict` and confirm it
      reports the change as valid with no findings.
- [ ] 2.2 Run `openspec show e2e-loop-scope-g1-readme-banner-c0e65d23
      --json` and confirm the response lists exactly one capability
      (`project-readme`) under the `deltas` array.
- [ ] 2.3 Run `git status` in the worktree and confirm that the only
      file modified by this change is `README.md`, alongside the new
      `openspec/changes/e2e-loop-scope-g1-readme-banner-c0e65d23/`
      artefacts created by this task group.
- [ ] 2.4 Confirm the change's `## Impact` section references only
      `README.md`, which is the single path declared in the Work
      Package Scope Envelope.
