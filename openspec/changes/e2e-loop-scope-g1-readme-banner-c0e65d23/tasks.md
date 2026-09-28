# Tasks

## 1. Verify README.md banner content against the readme-banner spec

- [ ] 1.1 Confirm `README.md` exists at the repository root and is a
  regular file (run `test -f README.md` and confirm exit code 0).
- [ ] 1.2 Confirm `README.md` has no UTF-8 BOM and parses as Markdown
  (run `head -c 3 README.md | od -An -tx1` and verify the first bytes
  are not `ef bb bf`, then run a Markdown parse to confirm no errors).
- [ ] 1.3 Confirm the first non-empty line of `README.md` is exactly
  `# orca-companion` (run `head -n 1 README.md` and compare to the
  expected heading).
- [ ] 1.4 Confirm the tagline paragraph immediately after the title
  contains the literal phrases `end-to-end demonstration project` and
  `orca-companion agent harness` (run `grep -F` for each phrase and
  confirm both succeed).
- [ ] 1.5 Confirm the italic forward-pointer note after the tagline is
  delimited by single asterisks (`*…*`) and explicitly names at least
  one deferred section such as `Installation` or `Usage` (run
  `grep -F '*More sections' README.md` and confirm it matches).
- [ ] 1.6 Confirm no level-1 or level-2 heading appears above the
  forward-pointer note (run `grep -nE '^#{1,2} ' README.md` and confirm
  the only early match is the `# orca-companion` title on line 1).
- [ ] 1.7 Confirm `README.md` ends with exactly one trailing newline
  (run `tail -c 1 README.md | od -An -tx1` and verify the final byte is
  `0a`, then run `tail -c 2 README.md | od -An -tx1` and verify the
  second-to-last byte is not `0a`).

## 2. Reconcile README.md if any verification check fails

- [ ] 2.1 If any check from task 1 fails, edit `README.md` so it
  satisfies the `readme-banner` spec while preserving UTF-8 encoding,
  no BOM, and exactly one trailing newline.
- [ ] 2.2 Re-run every check from task 1 against the updated
  `README.md` and confirm each one passes.

## 3. Stage and hand off the change

- [ ] 3.1 Confirm
  `openspec/changes/e2e-loop-scope-g1-readme-banner-c0e65d23/` contains
  `.openspec.yaml`, `proposal.md`, `tasks.md`, and
  `specs/readme-banner/spec.md`.
- [ ] 3.2 Run `openspec validate
  e2e-loop-scope-g1-readme-banner-c0e65d23 --strict` and resolve every
  reported finding before handoff.
- [ ] 3.3 Confirm `git status` reports only `README.md` (modified) and
  the new `openspec/changes/e2e-loop-scope-g1-readme-banner-c0e65d23/`
  tree (untracked) relative to the baseline head
  `b0200dfcc5bdd52450c7f941691a6ac3c7e35364`.
- [ ] 3.4 Leave the change unarchived and in
  `openspec/changes/e2e-loop-scope-g1-readme-banner-c0e65d23/` for the
  validator and finalizer; do not run `openspec archive`.
