<!-- markdownlint-disable -->

# Hardening Report: DopplerHQ--cli-action/v1

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **DopplerHQ--cli-action/v1** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The workflow uses `actions/checkout@v2`, which is pinned to a mutable tag rather than an immutable 40-character commit SHA. This means the action could be silently updated or replaced with a malicious version without any change to the workflow file. It should be pinned to a full SHA, e.g. `actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v2`.

Locations:

- `.github/workflows/main.yml:11`

### missing-permissions (severity: medium)

The workflow file `.github/workflows/main.yml` has no top-level `permissions:` block and the single job `test_action` also has no job-level `permissions:` block. Without explicit permissions, the GITHUB_TOKEN is granted its default (potentially broad) permissions. A minimal permissions block (e.g. `permissions: read-all` or specific scopes) should be added.

Locations:

- `.github/workflows/main.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

1. Pinned `actions/checkout@v2` to its full commit SHA `0717577d45739eb3c851188b29f50ed6c0b2194e` with `# v2` comment for readability. 2. Added `permissions: {}` at the top level of the workflow to explicitly deny all GITHUB_TOKEN permissions, following the principle of least privilege.

