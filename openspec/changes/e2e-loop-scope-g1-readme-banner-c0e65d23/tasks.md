# Tasks

## 1. Add the banner block to README.md

- [ ] 1.1 Replace the top of `README.md` with a blockquote-framed banner block
      that starts with `# orca-companion`, includes the one-sentence tagline and
      fact strip, and ends with a `---` horizontal rule, and verify the banner
      is the first content in the file by checking that the first non-blank
      line begins with `>` (`head -1 README.md` shows `> # orca-companion`).

- [ ] 1.2 Keep the existing introductory paragraph and italic placeholder
      directly under the banner's horizontal rule and verify the body content
      remains after the separator (`grep -A 1 '^---$' README.md` shows the
      introductory paragraph immediately below the rule).

## 2. Verify the change satisfies the readme-banner spec

- [ ] 2.1 Run `openspec validate e2e-loop-scope-g1-readme-banner-c0e65d23` and
      verify the change passes validation with no errors.

- [ ] 2.2 Run `openspec show e2e-loop-scope-g1-readme-banner-c0e65d23 --type change`
      and verify the rendered change lists the `readme-banner` capability under
      `Capabilities → New Capabilities`.

- [ ] 2.3 Confirm the only path referenced in `proposal.md → Impact` is
      `README.md` and verify it by grepping for backtick-wrapped paths in that
      section (`grep -F '`' openspec/changes/e2e-loop-scope-g1-readme-banner-c0e65d23/proposal.md`
      shows only `README.md` between the `## Impact` heading and the next `##`
      heading).
