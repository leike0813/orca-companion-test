# Tasks

## 1. Banner skeleton

- [x] 1.1 Confirm `README.md` still consists of the single project title line, and record its current first line as the value that must survive this change. Verify with `head -n 1 README.md` and confirm the output is the top-level project heading.
- [x] 1.2 Insert a blockquote banner block directly beneath the title line in `README.md`, leaving the title as the file's first line and unaltered. Verify with `head -n 5 README.md` that line 1 is the heading and that the blockquote lines follow it with no intervening heading.

## 2. Banner content

- [x] 2.1 State the recovery status in the banner: the project is a recovered Orca worktree and recovery is still in progress. Verify by re-reading the banner and confirming the claim is present in greppable prose rather than implied.
- [x] 2.2 State in the banner that the repository contains no product code yet, and frame that as the current state of a recovery rather than as content that went missing. Verify by re-reading the banner and confirming the claim covers both the absence and its cause.
- [x] 2.3 State in the banner that the outstanding recovery work is specified as OpenSpec changes, and name `openspec/changes/` as the directory that tracks them. Verify with `grep -n 'openspec/changes/' README.md` returning a match inside the banner block.
- [x] 2.4 Point at `NOTES.md` as the single place recording the project basics, the companion configuration, the working agreements, and the open recovery items, without restating any of them. Verify by re-reading the banner and confirming each of those four subjects is referenced, not described.

## 3. Drift guards

- [x] 3.1 Confirm the banner is at most five substantive lines. Verify by counting the banner's lines (a `grep -c '^>' README.md` against the block's body) and confirming the result is five or fewer.
- [x] 3.2 Confirm the banner duplicates neither `NOTES.md` nor the Orca companion configuration: verify with `grep -n '"' README.md` returning no JSON structure, and by reading the banner against `NOTES.md` to confirm the two share only the project name and the pointer target.
- [x] 3.3 Confirm the banner introduces no section headings of its own. Verify with `grep -n '^## ' README.md` returning no match, so the file remains a title plus a banner.

## 4. Acceptance check

- [x] 4.1 Run the read-only acceptance command `test -f README.md && head -n 1 README.md | grep -q '^# ' && grep -q 'NOTES.md' README.md` in the worktree and confirm exit status zero; then run each assertion separately against a non-existent path or an emptied file to confirm the negative case exits non-zero.
- [x] 4.2 Run `openspec validate ip05-ip05-recovery-20261004o-scope-g1-readme-banner-7c31ab18 --strict` and confirm the change reports valid.
- [x] 4.3 Confirm the change touches no product file other than `README.md`: verify with `git status --porcelain` that the only added or modified tracked path outside the specification directory is `README.md`.
