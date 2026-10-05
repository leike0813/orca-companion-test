# Tasks

All commands below are run from the repository root and assume `NOTES.md` sits there.

## 1. Notes Document

- [ ] 1.1 Create `NOTES.md` at the repository root with one level-one title followed by the level-two sections `Purpose`, `Project Layout`, `Conventions`, and `Workflow`, in that order, and verify with `test -s NOTES.md` plus `test "$(grep -c '^# ' NOTES.md)" -eq 1 && test "$(grep '^## ' NOTES.md | tr '\n' ' ')" = "## Purpose ## Project Layout ## Conventions ## Workflow "`
- [ ] 1.2 Give every one of the four sections at least one line of non-heading body text, and verify with `awk '/^## /{if(h!=""&&b==0)exit 1; h=$0;b=0;next} /^[ \t]*#/||/^[ \t]*$/{next} {b=1} END{if(h!=""&&b==0)exit 1}' NOTES.md` (exit status 0 means no section is empty)
- [ ] 1.3 Fill the `Project Layout` section with backticked repository-relative paths that exist today, and verify with `test -z "$(grep -o '`[^`]*`' NOTES.md | tr -d '`' | awk 'index($0,"/")>0 || /\.md$/' | while read -r p; do [ -e "$p" ] || echo "$p"; done)"`
- [ ] 1.4 Write the `Conventions` and `Workflow` sections so they describe this repository's real practice rather than placeholders, keeping every shell command they show in backticks free of a `/` so it is not mistaken for a path, and re-run the 1.3 check to confirm it still passes

## 2. Acceptance Verification

- [ ] 2.1 Run the acceptance command for this change and confirm it prints nothing and exits 0: `test -s NOTES.md && test "$(grep -c '^# ' NOTES.md)" -eq 1 && test "$(grep '^## ' NOTES.md | tr '\n' ' ')" = "## Purpose ## Project Layout ## Conventions ## Workflow " && awk '/^## /{if(h!=""&&b==0)exit 1; h=$0;b=0;next} /^[ \t]*#/||/^[ \t]*$/{next} {b=1} END{if(h!=""&&b==0)exit 1}' NOTES.md && test -z "$(grep -o '`[^`]*`' NOTES.md | tr -d '`' | awk 'index($0,"/")>0 || /\.md$/' | while read -r p; do [ -e "$p" ] || echo "$p"; done)" && test "$(grep -o '`[^`]*`' NOTES.md | tr -d '`' | awk 'index($0,"/")>0 || /\.md$/' | wc -l)" -ge 1`
- [ ] 2.2 Confirm the change touched nothing but the notes file, and verify with `git status --porcelain` showing `NOTES.md` as the only modified or untracked path outside this change's own specification unit
