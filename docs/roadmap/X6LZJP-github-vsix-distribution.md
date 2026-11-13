---
id: X6LZJP
title: Distribute reproducible VSIX builds through GitHub Releases
status: needs-triage
type: roadmap
phase: Foundation
---

# Distribute reproducible VSIX builds through GitHub Releases

## Why

Mure is intended as a public MIT extension with GitHub Releases as its initial
installation channel. A successful development-host experiment is not an installable,
repeatable release that another contributor or user can verify.

## Scope to shape

- Package the accepted increment as a VSIX using the selected toolchain.
- Document build, install, supported versions/platform evidence and known limitations.
- Reuse the foundation's automated build/test/package checks and packaged-extension
  smoke test as release prerequisites; extend only for release-specific verification.
- Choose a versioning and human-authorized release process; no publication is authorized
  by this card, and Marketplace distribution remains out of scope.

[The accepted foundation spec](../issues/extension-foundation/B2FBK0-spec.md) defines the
local packaging and CI prerequisites; they are not implemented yet. This card owns subsequent public
distribution, not a duplicate build-system implementation. Packaging should accompany
each usable slice, not wait until the entire product outcome is implemented. Exact
release automation and support claims remain decisions, not commitments. See [product distribution](../../PRODUCT.md#distribution-and-documentation).

## Comments
