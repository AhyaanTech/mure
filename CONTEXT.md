# Mure context

Mure coordinates a persistent editor workbench with terminal work in Herdr.
Its language distinguishes project membership from the user's current focus.

## Language

**Workbench**:
The user's persistent editor environment containing a personal home and attached project
checkouts. It is not a Herdr workspace.
_Avoid_: workspace, when the owning application would be ambiguous.

**Home**:
The user-selected directory for personal notes and shared navigation or dashboards.
It is independent of the project currently receiving attention.
_Avoid_: active project, primary repository.

**Attached checkout**:
A specific local Git checkout present in the workbench. Different worktrees of one
repository are different attached checkouts.
_Avoid_: repository, when checkout identity matters.

**Herdr workspace**:
A terminal grouping containing tabs and panes. Its saved project definition and the
current directories of its panes are distinct sources of information.

**Focused checkout**:
The checkout corresponding to the currently focused Herdr pane's directory.
It does not imply that the editor's active document or terminal belongs to that checkout.

**Mure-owned root**:
An attached checkout whose addition Mure recorded for this workbench. Existing or
manually added roots are not Mure-owned merely because Herdr also references them.

**Inactive root**:
A Mure-owned root with no remaining live Herdr reference according to a current, complete
view of the connected server. Disconnection alone cannot establish inactivity.

**Cleanup**:
Removing eligible Mure-owned roots from workbench membership, manually or through an
opt-in policy. It never means deleting checkout files, Git worktrees or terminal processes.
