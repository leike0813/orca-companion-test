# Tasks

## 1. Author README banner

- [ ] 1.1 Ensure line 1 of `README.md` is exactly `# orca-companion` (no
      leading or trailing whitespace, single LF line ending), and verify with
      `awk 'NR==1 && $0!="# orca-companion"{exit 1} {next}' README.md` exiting
      with code 0.

- [ ] 1.2 Ensure line 2 of `README.md` is a single blank Markdown separator
      (an empty string), and verify with
      `awk 'NR==2 && $0!=""{exit 1} {next}' README.md` exiting with code 0.

- [ ] 1.3 Ensure line 3 of `README.md` is the pinned banner blockquote that
      begins with the literal leading sentence, and verify with
      `awk 'NR==3 && $0!="> **Note:** this repository is an end-to-end loop demonstration project for the orca-companion agent harness."{exit 1} {next}' README.md`
      exiting with code 0.

- [ ] 1.4 Ensure the banner blockquote is the only content between the H1 and
      the banner line, and verify with
      `awk 'NR==2 && $0!=""{exit 1} NR==3 && $0!~/^> \*\*Note:\*\* this repository is an end-to-end loop demonstration project for the orca-companion agent harness\.$/{exit 1} {next}' README.md`
      exiting with code 0.

- [ ] 1.5 Ensure no second H1 appears on lines 1-3, and verify with
      `awk 'NR<=3 && /^# / && NR!=1{exit 1}' README.md` exiting with code 0.

- [ ] 1.6 Ensure the file uses single LF line endings so byte-exact positions
      are stable, and verify with
      `grep -c $'\r$' README.md | awk '{exit ($1==0)?0:1}'` exiting with code 0.

## 2. Verify acceptance

- [ ] 2.1 Confirm `README.md` is the only repository file this change
      introduces or modifies, by running `git status --porcelain` and
      verifying that the only entry reported is `README.md`.

- [ ] 2.2 Confirm the pinned leading sentence appears exactly once and on
      line 3, by running
      `grep -cF '> **Note:** this repository is an end-to-end loop demonstration project for the orca-companion agent harness.' README.md`
      and verifying the count is exactly `1`, and by running
      `grep -nF '> **Note:** this repository is an end-to-end loop demonstration project for the orca-companion agent harness.' README.md`
      and verifying the reported line number is exactly `3`.

- [ ] 2.3 Confirm the H1 is the only level-1 heading in the file, by running
      `grep -cE '^# [^#]' README.md` and verifying the count is exactly `1`.

- [ ] 2.4 Confirm the file is at least 3 lines long and the trailing italic
      line, if present, is not pinned by the spec, by running
      `awk 'END{exit (NR>=3)?0:1}' README.md` exiting with code 0.

## 3. Verify documentation-only surface

- [ ] 3.1 Confirm line 3 of `README.md` contains no fenced code fence or
      inline HTML marker, by running
      `awk 'NR==3 && (/```/ || /</){exit 1}' README.md` and verifying it exits
      with code 0.

- [ ] 3.2 Confirm line 3 of `README.md` declares no semantic-version pin,
      no machine identifier, and no imperative command, by running
      `awk 'NR==3 && (/[0-9]+\.[0-9]+\.[0-9]+/ || /`/ || /\\$[A-Z_]+/){exit 1}' README.md`
      and verifying it exits with code 0.

- [ ] 3.3 Confirm line 3 of `README.md` is plain prose (no fenced language tag,
      no task-list marker, no table syntax), by running
      `awk 'NR==3 && (/^- / || /^\| / || /```[a-z]+$/){exit 1}' README.md` and
      verifying it exits with code 0.
