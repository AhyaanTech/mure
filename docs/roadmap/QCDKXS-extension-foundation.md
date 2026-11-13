---
id: QCDKXS
title: Maintainable extension architecture and contributor setup
status: done
type: roadmap
phase: Foundation
---
# Maintainable extension architecture and contributor setup

Spec: [[../issues/extension-foundation/B2FBK0-spec|Loadable extension foundation]]

## Why

Mure is a public MIT project, not a disposable personal script. Contributors should be
able to understand, build and test it without reconstructing the original conversation.
The user wants deliberate architecture and incremental delivery, not one-shot generation
of the full extension.

## Scope to shape

- Choose the implementation stack and a small, explicit module structure.
- Separate Herdr transport, checkout resolution, policy, and VS Code side effects so
  behavior can be tested without a live desktop for every case.
- Establish reproducible development/build/test commands and concise contributor guidance.
- Record consequential decisions; avoid a monorepo, reusable framework or separate
  packages without a demonstrated need.

The user accepted a loadable foundation before choosing the first runtime feature:
one strict-TypeScript extension package with npm, compiler-based build,
native VS Code tests, local VSIX packaging and minimal diagnostics. Do not implement future
policy or interfaces merely because they appear in the [design direction](../../DESIGN.md).
The separate [distribution card](X6LZJP-github-vsix-distribution.md) covers public release.

## Promotion

Promoted into the accepted foundation spec. This card's `done` state records promotion,
not completed implementation. The Herdr client contract and first runtime feature remain
later decisions; the scaffold must not prejudge them with placeholder code.

## Comments

### 2026-11-13T03:55:34Z | control-plane-draft | attempt 1

- User chose stepwise foundation planning before runtime behavior. Created a bounded draft
  and moved this card into clarification; not promoted until explicit spec acceptance.

### 2026-11-13T04:04:35Z | human-acceptance-and-promotion | attempt 1

- Human accepted the reviewed foundation spec. Added its canonical pointer and promoted
  this card; runtime capabilities and public release remain separate roadmap work.
