# Tasks

## 1. Replace the placeholder with the banner

- [ ] 1.1 Remove the `_More sections (Installation, Usage, etc.) will be added
  in later changes._` line from `README.md`; verify with
  `! grep -q 'will be added in later changes' README.md`.
- [ ] 1.2 Add a banner block directly beneath the `#` title, every line starting
  with `> `; verify with
  `awk '/^# /{n=1;next} n&&/^$/{f=1;next} f{print;exit}' README.md` printing a
  line that starts with `>`.
- [ ] 1.3 State the development stage and what the project is in the banner;
  verify the banner body is non-empty with
  `awk '/^# /{n=1;next} n&&/^$/{f=1;next} f&&/^>/{s=1} f&&!/^>/{exit} s' README.md | grep -q '[^[:space:]]'`.
- [ ] 1.4 Point the banner at the existing tracked-work and reference documents;
  verify each path the banner names resolves by extracting its backticked paths
  and testing each with `test -e` against the repository root, so that a path
  is only named if it exists in the tree the banner is written against.

## 2. Verify the document against the specs

- [ ] 2.1 Confirm the document still has exactly one top-level title with
  `test "$(grep -c '^# ' README.md)" -eq 1`.
- [ ] 2.2 Confirm the banner introduced no headings by listing them with
  `grep -n '^#' README.md` and verifying the only match is the project title
  line.
- [ ] 2.3 Confirm no equivalent deferral was introduced by reading `README.md`
  end to end; verify there is no line promising forthcoming sections.
- [ ] 2.4 Confirm every claim in the banner matches the tree by comparing the
  banner against `ls -a` and the repository contents; verify no statement
  describes a file, command, or feature the repository lacks.
- [ ] 2.5 Confirm the change stayed in scope by running `git status --porcelain`
  and verifying `README.md` is the only path outside
  `openspec/changes/e2e-loop-scope-g1-readme-banner-c0e65d23/` that is
  modified.
