<!-- markdownlint-disable -->

# Hardening Report: DopplerHQ--cli-action/v2

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **DopplerHQ--cli-action/v2** was hardened automatically. 2 finding(s) were identified and resolved across 1 iteration(s).

## Findings Fixed

### unpinned-uses (severity: high)

The workflow uses actions/checkout@v2, which is pinned to a mutable tag rather than an immutable 40-character commit SHA. A tag can be moved to point to a different (potentially malicious) commit, enabling supply-chain attacks. It should be replaced with a full SHA pin, e.g. actions/checkout@11bd71901bbe5b1630ceea73d27597364c9af683 # v2.

Locations:

- `.github/workflows/main.yml:11`

### missing-permissions (severity: medium)

The workflow file .github/workflows/main.yml has no top-level permissions: key and the single job (test_action) also has no job-level permissions: key. Without explicit permissions, the workflow inherits the repository's default token permissions, which may be overly broad (write access to contents, packages, etc.). A minimal permissions block (e.g. permissions: contents: read) should be added.

Locations:

- `.github/workflows/main.yml:1`

## Iteration Notes

### Iteration 1

**Fixes applied:** unpinned-uses, missing-permissions

**Notes:**

Fixed .github/workflows/main.yml: (1) Pinned actions/checkout@v2 to the full commit SHA actions/checkout@0717577d45739eb3c851188b29f50ed6c0b2194e # v2 to prevent supply-chain attacks via mutable tags. (2) Added a top-level `permissions: contents: read` block to restrict the GITHUB_TOKEN to the minimum permissions needed for a checkout-and-test workflow.

