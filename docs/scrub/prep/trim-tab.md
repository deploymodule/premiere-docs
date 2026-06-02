# Trim Tab

The **Trim** tab provides two timeline-cleanup tools that operate directly on the current project — they don't use templates or naming presets. Each tool has its own collapsible section.

| Tool | What it does |
|------|--------------|
| [**Source Trim**](#source-trim) | Sets source **In/Out** marks on the clips selected in the Project panel, so they drop onto the timeline with handles already removed |
| [**Remove Disabled**](#remove-disabled) | Deletes disabled (muted) track items from the focused timeline |

When an operation finishes, a results bar reports how many clips were **affected** and how many were **skipped**, along with any warnings. Successful runs clear after a few seconds; errors stay up longer. A **Cancel** button appears while an operation is running.

---

## Source Trim

Sets the source in- and out-points on the items currently selected in the **Project panel**. After trimming, when you drag those clips to a timeline they arrive with the head and tail handles already shaved off — useful for stripping pre-roll/post-roll handles before assembling a cut.

### Settings

| Field | Description | Default |
|-------|-------------|---------|
| **Head frames** | Number of frames to remove from the start (in-point moves later) | 0 |
| **Tail frames** | Number of frames to remove from the end (out-point moves earlier) | 0 |

### How to use it

1. Select one or more clips in the Project panel.
2. Set **Head frames** and **Tail frames**.
3. Click **Set Source In/Out**.

Scrub updates each selected clip's source in/out marks. The clip's media is not modified — only its in/out points — so the change is non-destructive and can be re-applied or reset at any time.

---

## Remove Disabled

Removes all **disabled (muted)** track items from the focused timeline in a single pass. Use it to clean up a sequence where alternate takes or scratch layers have been muted rather than deleted.

### Settings

| Field | Options | Description |
|-------|---------|-------------|
| **Range** | **Whole timeline** · **Between In/Out** | Limit removal to the whole sequence or only the section between the sequence's In and Out points |
| **Tracks** | **All tracks** · **Video only** · **Audio only** | Limit removal to a track type |

### How to use it

1. Choose a **Range** and **Tracks** scope.
2. Click **Remove**.

Disabled track items within the chosen range and track scope are deleted. Enabled clips are never touched.

!!! warning
    Removal deletes the disabled track items from the timeline. Use Premiere Pro's **Undo** (Ctrl/Cmd+Z) if you need to reverse it.
