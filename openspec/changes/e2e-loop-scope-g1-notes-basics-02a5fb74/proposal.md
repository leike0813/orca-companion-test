# Proposal

## Why

The repository currently gives a new contributor almost no orientation material: the
only existing prose is a one-line README, so anyone joining the project has to infer the
project layout and the local workflow from the working tree itself. Adding a single
`NOTES.md` at the repository root gives people one obvious place to read the basics
before they start making changes.

## What Changes

- Add a `NOTES.md` file at the repository root.
- Define the structure that `NOTES.md` must follow: a title, a short purpose statement,
  and a fixed set of sections covering the repository layout, the local development
  workflow, and the conventions contributors are expected to follow.
- Require `NOTES.md` to state only facts that are verifiable from the repository itself,
  so the file cannot drift into aspirational or outdated guidance.

## Capabilities

### New Capabilities

- `repo-notes`: The repository ships a root-level `NOTES.md` that orients contributors by
  describing the repository layout, the local development workflow, and the conventions
  contributors follow.

### Modified Capabilities

<!-- None. No existing capability changes its requirements in this change. -->

## Impact

- Adds `NOTES.md` at the repository root. No existing file is modified or removed.
