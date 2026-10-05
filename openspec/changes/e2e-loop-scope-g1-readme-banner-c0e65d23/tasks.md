# Tasks

Acceptance command for this work package (run from the repository root; it covers `README.md`
and exits non-zero on any regression):

```sh
sh -c 'f=README.md; [ "$(head -1 "$f" | grep -c ip05-cc-06)" -eq 1 ] && [ "$(grep -c "^\*\*Status:\*\*" "$f")" -eq 1 ] && grep -qx "# ip05-cc-06" "$f" && [ "$(awk "NF && !/^# /{n++} /^# /{print n+0; exit}" "$f")" -le 10 ]'
```

The four checks map to the spec in order: the banner's opening line is the first line of the
file and names the project; exactly one `**Status:**` line exists; the original `# ip05-cc-06`
title survives below the banner; the banner stays within ten non-blank lines.

## 1. Banner Content

- [ ] 1.1 Insert the banner at the top of `README.md` as a bolded opening line naming the
  project followed by a one-line plain-text purpose statement; verify the first line of the
  file is that opening line by running `head -1 README.md`
- [ ] 1.2 Add exactly one lifecycle status line using the literal `**Status:**` label prefix
  with a value from the declared set; verify with
  `grep -c '^\*\*Status:\*\*' README.md` returning `1`
- [ ] 1.3 Separate the banner from the existing `# ip05-cc-06` title with one blank line and
  leave the rest of the file untouched; verify with `grep -qx '# ip05-cc-06' README.md`

## 2. Acceptance Verification

- [ ] 2.1 Run the acceptance command above from the repository root and confirm it exits `0`
  against the edited `README.md`
- [ ] 2.2 Confirm the acceptance command is a real check by running it against a copy of the
  pre-change `README.md` (title only, no banner) and confirming it exits non-zero
- [ ] 2.3 Confirm `git diff --stat` reports `README.md` as the only modified tracked file, so
  the Work Package Scope Envelope is respected

