# Proposal

## Why

The repository currently ships a placeholder README that announces the project name and description in free-form prose, then trails off with an italic note promising future sections. Without a defined banner block at the top of the README, every reader has to guess which lines are part of the project's identity, which lines are placeholder copy, and which lines signal the project's status. Subsequent changes that extend the README will have no stable contract for the introductory block, so they will each invent their own banner ad hoc. This change introduces a single `readme-banner` capability so the project identity, tagline, and forward-looking status are described once and can be relied on by every later change.

## What Changes

- Replace the unstructured introduction in `README.md` with a defined banner block at the top of the file.
- The banner MUST present, in order, the project title, a one-sentence tagline, and a status banner line that names the project as an end-to-end loop demonstration under active development.
- Remove the legacy italic placeholder copy ("_More sections (Installation, Usage, etc.) will be added in later changes._") and re-express the same forward-looking intent as a status banner line owned by the new `readme-banner` capability.
- Document the banner under the OpenSpec capability `readme-banner` so later changes can add adjacent sections without re-litigating the banner contract.

## Capabilities

### New Capabilities
- `readme-banner`: Defines the structure and baseline content of the introductory banner block at the top of `README.md` so the project's identity and status are described consistently.

### Modified Capabilities
- None.

## Impact

- `README.md` (existing top-level file; the banner at the top of the file is rewritten under the new `readme-banner` capability contract).
