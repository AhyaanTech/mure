# Mure

Mure is an MIT-licensed VS Code extension project coordinating a persistent multi-root
workbench with Herdr. The repository currently contains design/specification artifacts
and icon concepts, not an implemented extension or build/test toolchain.

## Read first

- [PRODUCT.md](PRODUCT.md): purpose, settled behavior, boundaries and evidence.
- [CONTEXT.md](CONTEXT.md): shared terminology.
- [DESIGN.md](DESIGN.md): proposed architecture and interfaces, not implemented APIs.
- `docs/roadmap/`: capability intake, promoted into bounded specs one at a time.
- The relevant Spec Tiki under `docs/issues/`: delivery scope only after human acceptance.
  The broad workbench draft is held as an outcome reference, not dispatch authorization.

## Repository constraints

- Keep the home first and root order stable during following. First-root changes restart
  VS Code extensions; do not use that mechanism for ordinary focus changes.
- Background following must not foreground VS Code, switch active documents/terminals,
  send shell input or modify Herdr topology. A native Explorer-only probe passed in an
  empty test host; existing editor/terminal preservation and integrated following still
  need verification.
- Keep Git worktrees distinct by checkout identity. Do not collapse them by remote URL or
  main repository path.
- Cleanup changes workspace membership only. Preserve home/manual roots; disconnected or
  incomplete state is not evidence that a checkout became inactive.
- The native `.code-workspace` is the folder manifest. Do not introduce a parallel YAML
  inventory, daemon or queue without a concrete new requirement.
- No hardcoded personal paths, socket credentials or session inventory in committed code
  or documentation. A configured home is not blanket permission to inspect personal notes.
- Foam is optional. Its first-root query configuration and multi-root limitations are
  consumer compatibility concerns, not authority to migrate users' notes.
- Keep README small; document product/design detail in the linked files. Icon assets are
  concepts, not approved branding. Initial distribution is a GitHub Release VSIX.
- Preserve unrelated changes. No commit, push, installation or release without authorization.

## Available verification

Run from the repository root:

```sh
git diff --check
tiki exec 'select id, title, type, status'
tiki exec 'select id, title, phase where has(phase)'
```

No product build, test or packaging command exists yet. Add verified commands when the
extension toolchain is implemented; do not describe planned checks as passing tests.

## Agent skills

### Issue tracker

Issues and specs use git-tracked Tiki Markdown under `docs/issues/<feature-slug>/`.
See [docs/agents/issue-tracker.md](docs/agents/issue-tracker.md) and the linked `ahy-tiki`
skill. Root `workflow.yaml` defines typed fields and `.tikiignore` bounds discovery.

### Domain docs

Single-context domain docs use root `CONTEXT.md` plus `docs/adr/` when decisions are
recorded. See [docs/agents/domain.md](docs/agents/domain.md). No framework-specific rule
family has been installed: the extension implementation stack is not scaffolded yet.
