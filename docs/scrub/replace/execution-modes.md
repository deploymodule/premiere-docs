# Execution Modes

**Step 3** of the Replace wizard. After scanning for matching clip instances, choose an execution mode and run the replacement.

## Scanning

Click the **magnifying glass** button to scan. Scrub iterates through all sequences in scope, enumerates track items, and matches them against your replacement map using:

- Canonical media keys (name + path + type)
- Stable item IDs (node/GUID)
- Normalized file paths

The scan results show how many instances were found across how many sequences.

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

**What it does**: Creates new tracks alongside the originals and places replacement clips there. Original clips are untouched.

**Process**:

1. Creates new video/audio tracks as needed (one per original track that has matches).
2. Inserts each replacement clip on the neighbor track at the same timeline position.

**Best for**: A/B comparison workflows where you want to see old and new side by side. Non-destructive — you can manually compare and copy properties.

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

## Include/Exclude Controls

Before executing, you can fine-tune which instances to process:

- **Per-sequence checkboxes** — include or exclude an entire sequence.
- **Per-instance checkboxes** — include or exclude individual clip instances.
- **Select All / Select None** links for batch toggling within a sequence.

Excluded instances are dimmed in the results and skipped during execution.
