# Execution Modes

**Step 3** of the Replace wizard. After scanning for matching clip instances, choose an execution mode and run the replacement.

## Scanning

Click the **magnifying glass** button to scan. Scrub iterates through all sequences in scope, enumerates track items, and matches them against your replacement map using:

- Canonical media keys (name + path + type)
- Stable item IDs (node/GUID)
- Normalized file paths

The scan results show how many instances were found across how many sequences.

!!! note "Linked A/V warnings"
    If any linked clips can't be handled cleanly, the scan reports *"N linked-audio warning(s) — expand the panel below for details"* and shows a collapsible **Linked A/V warnings** panel. Locked tracks are skipped and noted. See [Linked A/V Clips](#linked-av-clips) below.

## The Three Modes

After scanning, three mode buttons appear. Select one before clicking **Execute**.

---

### Offline/Online

**What it does**: Changes the file path of the old project item to point to the new file. All instances across the project update immediately because they reference the same project item.

**Process**:

1. Resolves the new media file path (from the project, cache, or a file picker prompt).
2. Sets the old project item offline.
3. Changes its media path to the new file.
4. Renames the project item to match the new filename.
5. Refreshes and verifies the relink.

**Best for**: Simple version swaps where you want every instance of the old file to update everywhere.

!!! note
    If the new media path can't be resolved automatically, you'll be prompted with a file picker. The path is cached per row to avoid repeated prompts.

---

### Neighbor

**What it does**: Creates new tracks alongside the originals and places replacement clips there. Original clips are left untouched.

**Process**:

1. Extracts preservation snapshots from each original clip.
2. Creates new video/audio tracks as needed (one per original track that has matches).
3. Inserts each replacement clip on the neighbor track at the same timeline position.
4. Reapplies the preserved effects, keyframes, and markers to the placed clips.

**Best for**: A/B comparison workflows where you want old and new side by side. Non-destructive — the originals stay in place, and the preserved data is reapplied to the neighbor clips automatically (no manual copying needed).

---

### Replace

**What it does**: Deletes the original clips and inserts replacement clips in their place, preserving effects, keyframes, markers, transitions, and timing.

**Process**:

1. Extracts preservation snapshots from each original clip.
2. Batch-deletes the originals.
3. Inserts new clips at the correct timeline positions.
4. Applies preservation snapshots to restore all clip data.

**Preserved data includes**:

- Effects chain (display name, match name, all parameters)
- Keyframes (tick times, values, interpolation mode)
- Markers (name, comment, time offset, type, color, duration)
- Transitions (head/tail, type, match name, duration, alignment)
- Label colors
- Source in/out points and timeline positions

!!! warning "Destructive Operation"
    Replace mode permanently removes original clips. Make sure you've verified the scan results before executing.

!!! danger "Per-clip delete and place are not one atomic step"
    Each clip is deleted and re-placed as **separate transactions with no rollback**. Clips are independent of one another — a failure on one clip never affects the others. But *within* a single clip, if placement fails **after** its original was already deleted, that leaves a **gap** on the timeline where the clip used to be. It's reported as **failed** in the results (check the notes), and is not automatically restored. Keep Premiere's own **Undo** available as a fallback.

---

### Linked A/V Clips

Linked A/V clips are **split into separate video and audio instances**, each scanned and swapped independently. In the results, a linked clip therefore appears as its video half and its audio half as distinct rows, and the [What to replace](sequence-selection.md#what-to-replace) setting decides which halves are included.

!!! warning "Multi-audio limitation"
    Linked clips with **multiple audio channels on non-consecutive tracks** (or an inconsistent channel layout) are **skipped with an explanatory note** rather than replaced — this avoids corrupting complex layouts. Re-arrange the audio onto consecutive tracks, or use a single-channel source, if you need those clips swapped. The skip reason appears in the instance notes and the exported report.

## Include/Exclude Controls

Before executing, you can fine-tune which instances to process:

- **Per-sequence checkboxes** — include or exclude an entire sequence.
- **Per-instance checkboxes** — include or exclude individual clip instances.
- **Select All / Select None** links for batch toggling within a sequence.

Excluded instances are dimmed in the results and skipped during execution.
