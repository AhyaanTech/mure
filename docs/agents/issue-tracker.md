# Issue tracker: repository Tiki

Tiki is the local, git-tracked authority for Markdown under `docs/issues/` and
`docs/roadmap/`. Frontmatter `status`, `type`, `dependsOn`, `risk`, and roadmap `phase`
are operational state. Patch Markdown bodies as files; never assign `description`.

Use the current AhyaanSkills workflow (ADR 0022 as amended by ADR 0023) via linked global instructions; do not
copy model routing or review ladders into project instructions.

## Artifact conventions

- Specs live in `docs/issues/<feature-slug>/`; tickets in its `issues/` directory;
  roadmap cards in `docs/roadmap/`.
- IDs are Tiki-minted and independent of filenames. Only `done` satisfies `dependsOn`.
- Delivery bodies begin `Spec: [[../<SPEC_ID>-spec|<SPEC_ID>]]`, using the actual
  relative filename and readable label; never put that spec ID in `dependsOn`.
- Bodies are compact active handoffs above immutable `## Comments`; workers never mutate
  Tiki, Comments, commits, or pushes.
- One spec maps to one branch/PR and one integration ticket blocked by implementation leaves.

## Lifecycle

`ready-for-agent` -> `in-progress` -> leaf `done`; the integration ticket becomes
`review-pending` for the integrated review, then `done` on approval/advisory or
`ready-for-human` after a second blocker. The control plane records current verification
results and updates the spec Resume/Progress section. Terminal `done`/`wontfix` artifacts
are never reopened; a material scope change requires human choice before a linked new
ticket may be created.

## Roadmap cards

Use `ahy-roadmap` for capability intake. Cards are ideas, not dispatchable implementation
work. Deduplicate against existing cards before creating one with root-scoped
`tiki-helper create --dir docs/roadmap`, `--type roadmap`, `--status needs-triage`, and
an explicit title, slug and phase. IDs must be helper-minted; never invent them.

Use phases `Foundation`, `Core Features`, `Polish`, and `Future Ideas`. Preserve the
reasoning under `## Why` and append history under immutable `## Comments`. An accepted
bounded spec promotes the card: add a `Spec:` wikilink to its actual relative filename,
preserve the rationale/history, and use Tiki to set the card to `done`. Do not delete it.
A held outcome draft is not an accepted promotion target.

Find the next roadmap ideas from the repository root:

```sh
tiki exec 'select id, title, phase where has(phase) and status != "done" and status != "wontfix" order by phase'
```

## Frontier

Run the dispatchable delivery query from the repository root, separately from the roadmap:

```sh
tiki exec 'select id, title, type, status where type in ["ticket", "integration"] and status = "ready-for-agent" and not (dependsOn any status != "done") order by updatedAt'
```

Root `workflow.yaml` defines the other queues; use `ahy-tiki` for typed mutations and
creation/recovery rules. Preserve IDs, frontmatter, filenames, links, and Comments when
migrating legacy active work; rewrite only a pre-dispatch active body.

## Receipts and ownership

The control plane alone records dispatch, return, block, resume, review and human handoff
events under Comments. Use actual UTC ISO 8601 time, actor/model/effort when known,
attempt number, concise result and command evidence; identify the reviewed revision or
working-tree snapshot. A resume explains what changed. Record unknown historical times
as unknown; preserve old Comments. `createdAt`/`updatedAt` and git commits are not event
timers. Elapsed intervals are not active model time or token cost.

Tickets name documentation impact and its owner. Update enduring docs alongside the code;
keep shared docs with one owner. Tiki is not a file/resource lock: verify file, interface,
generated-output and runtime/test-resource compatibility before parallel dispatch.
