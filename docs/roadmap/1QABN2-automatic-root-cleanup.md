---
id: 1QABN2
title: Opt in to guarded automatic root cleanup
status: needs-triage
type: roadmap
phase: Polish
---

# Opt in to guarded automatic root cleanup

## Why

The user requested optional automatic membership removal, while retaining offered cleanup
as the default. This can reduce housekeeping only if it does not silently discard work.
The phase marks an optional refinement, not low implementation risk.

## Scope to shape

- Add explicit opt-in using the same ownership, fresh-reference and preservation guards
  as [manual cleanup](6PXYA9-manual-root-cleanup.md).
- Unknown state or unknown terminal/debug association always defers removal.
- Preserve user exclusions and manual roots; pause must stop automatic mutation.
- Explain the limits of observing extension-private chats/sessions before enabling it.
- Remove workspace membership only, never on-disk checkouts or running processes.

Settle observability and failure behavior before promoting this card. It is not required
in the first release merely because it appears in the [product outcome](../../PRODUCT.md).

## Comments
