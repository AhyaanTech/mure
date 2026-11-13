---
id: 6PXYA9
title: Offer safe manual cleanup of inactive roots
status: needs-triage
type: roadmap
phase: Core Features
---

# Offer safe manual cleanup of inactive roots

## Why

A long-lived workbench accumulates roots, but closing a Herdr reference does not prove
that editor work is finished. Cleanup should be a deliberate offer, not an automatic
reaction that interrupts terminals, debugging or unsaved documents.

## Scope to shape

- Let the user select inactive, provably Mure-owned roots for membership removal.
- Revalidate live references and safety guards immediately before removal.
- Protect home, manual/ambiguous roots, dirty documents, active debug sessions and live
  terminals; unknown session association means defer, not assume safety.
- Retain roots on stale/incomplete/disconnected state and explain deferrals.
- Never delete files/worktrees, terminate processes or send terminal input.

This relies on ownership recorded by [attachment](H8MQ8V-live-checkout-attachment.md).
Third-party extension-private state is not universally observable; disclose that limit.
[Automatic cleanup](1QABN2-automatic-root-cleanup.md) requires separate opt-in scope.
See [the held safeguards](../issues/persistent-workbench/KFDQFD-spec.md#cleanup-and-failure-behavior).

## Comments
