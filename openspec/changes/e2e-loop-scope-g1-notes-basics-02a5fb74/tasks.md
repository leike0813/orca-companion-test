# Tasks

## 1. Author NOTES.md

- [ ] 1.1 Create `NOTES.md` at the repository root with the three baseline level-2 sections (`Project Status`, `Open Questions`, `Change Index`) in that exact order, and verify the file exists by running `test -f NOTES.md` which must exit 0.
- [ ] 1.2 Add at least one non-heading line of body content under each of the three baseline sections, and verify by running `awk 'BEGIN{c=0} /^## Project Status$/{p=1;next} /^## /{p=0} p && NF>0{c++} END{exit (c>=1)?0:1}' NOTES.md` and the analogous awk check for each of the other two sections, all of which must exit 0.

## 2. Verify acceptance

- [ ] 2.1 Confirm `NOTES.md` is the only repository file the change introduces, by running `git status --porcelain -- NOTES.md` together with `git ls-files --others --exclude-standard` and verifying the only relevant new entry is `NOTES.md`.
- [ ] 2.2 Confirm the three required level-2 headings appear in `NOTES.md` in the correct order, by running `grep -nE '^## (Project Status|Open Questions|Change Index)$' NOTES.md` and verifying the reported line numbers are strictly ascending and match `Project Status`, `Open Questions`, `Change Index` in that order.
- [ ] 2.3 Confirm NOTES.md contains no fenced executable override block by running `grep -nE '^\`\`(sh|bash|shell|yaml|yml)$' NOTES.md` (or no-op equivalent) and verifying either no match exists or, if a fenced block is present, it does not assert a behavior absent in `README.md` or `orca-companion.json` at the baseline commit.

