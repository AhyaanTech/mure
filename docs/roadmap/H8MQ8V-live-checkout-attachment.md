---
id: H8MQ8V
title: Attach live Herdr checkouts without disrupting the workbench
status: needs-triage
type: roadmap
phase: Core Features
---

# Attach live Herdr checkouts without disrupting the workbench

## Why

Opening a project in Herdr should make its actual checkout available in the persistent
workbench. Saved projects and zoxide are opening mechanisms, not reliable inventories;
a pane may enter a checkout different from its workspace's original repository.

## Scope to shape

- Derive references from all live panes plus appropriate workspace metadata; prefer the
  focused pane's actual checkout for focus resolution.
- Validate local absolute paths and canonicalize checkout identity. Dedupe subdirectories
  and symlink aliases while retaining distinct Git worktrees.
- Append eligible missing Git checkouts after home without reordering existing roots.
- Obtain binding consent, respect trust, and record ownership/exclusions from the first
  adding release. Manual roots remain user-owned; manual removal suppresses re-add.
- Retain loaded roots under disconnect, incomplete snapshots or unresolved paths.

This card does not authorize removal. Ownership must not be retroactively guessed when
[manual cleanup](6PXYA9-manual-root-cleanup.md) arrives. Membership and
[Explorer following](23MS17-explorer-focus-following.md) are separate responsibilities,
not necessarily separate release dates. See [product direction](../../PRODUCT.md).

## Comments
