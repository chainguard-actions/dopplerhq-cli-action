<!-- markdownlint-disable -->

# Hardening Report: dopplerhq--cli-action/v4

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **dopplerhq--cli-action/v4** was hardened automatically. 1 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Three `uses:` references in workflow files are pinned to mutable tags or branch names instead of full 40-character commit SHAs, making the workflows vulnerable to supply-chain attacks if those tags or branches are moved or compromised:
- `actions/checkout@v6` (tag)
- `actions/setup-node@v6` (tag)
- `DopplerHQ/.github/.github/workflows/dependencies.yaml@main` (branch)

Locations:

- `.github/workflows/main.yml:34`
- `.github/workflows/main.yml:35`
- `.github/workflows/dependencies.yml:12`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all three mutable `uses:` references to full commit SHAs:
- `actions/checkout@v6` → `actions/checkout@d23441a48e516b6c34aea4fa41551a30e30af803 # v6` in `.github/workflows/main.yml`
- `actions/setup-node@v6` → `actions/setup-node@249970729cb0ef3589644e2896645e5dc5ba9c38 # v6` in `.github/workflows/main.yml`
- `DopplerHQ/.github/.github/workflows/dependencies.yaml@main` → `DopplerHQ/.github/.github/workflows/dependencies.yaml@6c1bb1d2991b68a3fa901ba964bc2c17d5f9753f # main` in `.github/workflows/dependencies.yml`

Original tags/branch names preserved as inline comments for readability.

