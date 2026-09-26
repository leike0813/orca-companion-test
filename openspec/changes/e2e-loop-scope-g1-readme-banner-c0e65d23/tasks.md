# Tasks — `e2e-loop-scope-g1-readme-banner-c0e65d23`

> Scope Envelope (this Work Package): `["README.md"]`.
> Anything outside this list is out of scope. If a future refinement
> proves necessary, open a new Work Package rather than widening this
> one.

## 1. Author the banner content

- [x] 1.1 Draft the banner as a single Markdown blockquote line that
  begins with `> ` and an emoji codepoint, contains the substrings
  `orca-companion` and `Orca e2e-loop`, and identifies the project
  as an Orca e2e-loop demonstration target.
- [x] 1.2 Confirm the banner wording does not contradict its declared
  role (no "production library", no "CLI tool", no other agent
  harness, etc.).

## 2. Insert the banner into `README.md`

- [x] 2.1 Confirm the baseline `README.md` (commit `e951e88`) starts
  with the H1 title `# orca-companion` on line 1, followed by a blank
  line, the description line `An e2e-loop demonstration project for
  the orca-companion agent harness.`, a blank line, and the italic
  deferral note `_More sections (Installation, Usage, etc.) will be
  added in later changes._`.
- [x] 2.2 Insert the banner as a new line directly after the H1 title
  and its trailing blank line, so the post-change file order is: H1
  title, blank line, banner line, blank line, description line, blank
  line, italic deferral note.
- [x] 2.3 Verify the H1 title, the description line, and the italic
  deferral note are unchanged in wording and in their relative order
  after the banner is inserted.

## 3. Format and structure verification

- [x] 3.1 Confirm `README.md` parses as valid CommonMark.
- [x] 3.2 Confirm the banner line begins with `>` followed by a single
  space and a single emoji codepoint.
- [x] 3.3 Confirm the banner line is the only `> `-prefixed blockquote
  in `README.md` (no other blockquotes introduced).

## 4. Spec–artifact alignment check

- [x] 4.1 Confirm both required substrings (`orca-companion` and
  `Orca e2e-loop`) appear inside the banner lines of `README.md`
  (case-insensitive `grep`).
- [x] 4.2 Confirm the banner is the first body element after the H1
  title: line 1 is `# orca-companion`, line 2 is blank, and the
  banner begins on line 3.
- [x] 4.3 Confirm the baseline description line and the italic
  deferral note both still appear, in that order, after the banner.

## 5. Final conformance

- [x] 5.1 Run `openspec change validate
  e2e-loop-scope-g1-readme-banner-c0e65d23 --strict` and confirm the
  change validates cleanly.
- [x] 5.2 Confirm no file outside the Work Package Scope Envelope
  (`README.md`) has been created, modified, or deleted (compare
  `git status` against the baseline `e951e88`).
- [x] 5.3 Confirm `openspec/specs/readme-banner/spec.md` is **not**
  committed to `openspec/specs/` — it remains inside
  `openspec/changes/e2e-loop-scope-g1-readme-banner-c0e65d23/specs/`
  until archive.

