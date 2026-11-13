---
id: 23MS17
title: Follow Herdr focus in the native Explorer
status: needs-triage
type: roadmap
phase: Core Features
---

# Follow Herdr focus in the native Explorer

## Why

Herdr is the user's working surface. VS Code should quietly select the corresponding
checkout root while retaining its loaded environment, rather than opening another window
or changing the current document.

## Scope to shape

- Read the selected server's focused pane, resolve its checkout, and select/reveal that
  root in the native Explorer without opening a file or stealing keyboard/OS focus.
- Keep home, root order, active editor/terminal and extension host unchanged.
- Handle rapid changes, same-pane cwd changes, unavailable targets and disconnect/reconnect
  without stale follow actions. Respect pause, trust and conflicting followers.

A first release could follow only already-loaded roots; that release boundary is not yet
accepted. [Automatic attachment](H8MQ8V-live-checkout-attachment.md) is separate intake.

## Evidence and remaining checks

The 2026-11-12 native `revealInExplorer` probe selected three roots with DOM confirmation,
stable order/host and an unfocused VS Code window. The user confirmed it worked well.
OS samples were partial. Existing editor/terminal preservation, integrated Herdr events
and third-party extension behavior still need checks; no need to repeat first-root swaps.
See [the evidence summary](../../PRODUCT.md#evidence-and-limits).

## Comments
