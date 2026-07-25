<!-- markdownlint-disable -->

# Hardening Report: DopplerHQ--cli-action/v4.0.1

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **DopplerHQ--cli-action/v4.0.1** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

Workflow uses action references pinned to mutable tags/branches rather than immutable full-length commit SHAs. This exposes the workflow to supply-chain attacks if the referenced tag or branch is moved or compromised. Failing references:
- `uses: actions/checkout@v6` (line 34) — tag ref, not a SHA
- `uses: actions/setup-node@v6` (line 35) — tag ref, not a SHA

Each should be pinned to a full 40-character hex commit SHA, e.g. `uses: actions/checkout@<sha> # v6`.

Locations:

- `.github/workflows/main.yml:34`
- `.github/workflows/main.yml:35`

### unpinned-uses (severity: high)

Workflow uses a reusable workflow reference pinned to a mutable branch (`@main`) rather than an immutable full-length commit SHA. This exposes the workflow to supply-chain attacks if the `main` branch of the referenced repository is compromised. Failing reference:
- `uses: DopplerHQ/.github/.github/workflows/dependencies.yaml@main` (line 11) — branch ref, not a SHA

This should be pinned to a full 40-character hex commit SHA, e.g. `uses: DopplerHQ/.github/.github/workflows/dependencies.yaml@<sha> # main`.

Locations:

- `.github/workflows/dependencies.yml:11`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses

**Notes:**

Pinned all mutable action/workflow references to full commit SHAs:
- `.github/workflows/main.yml` line 34: `actions/checkout@v6` → `actions/checkout@d23441a48e516b6c34aea4fa41551a30e30af803 # v6`
- `.github/workflows/main.yml` line 35: `actions/setup-node@v6` → `actions/setup-node@249970729cb0ef3589644e2896645e5dc5ba9c38 # v6`
- `.github/workflows/dependencies.yml` line 11: `DopplerHQ/.github/.github/workflows/dependencies.yaml@main` → `DopplerHQ/.github/.github/workflows/dependencies.yaml@6c1bb1d2991b68a3fa901ba964bc2c17d5f9753f # main`

All SHAs were resolved using lookup_action_sha. Original tags/branches preserved as inline comments.

