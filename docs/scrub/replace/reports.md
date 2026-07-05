# Results & Reports

After scanning or executing, the Replace module displays detailed results in a three-level hierarchy.

## Results Hierarchy

### Level 1 — Mapping Rows

Collapsible cards showing the old and new media filenames and directory paths, with a count badge (e.g., "5 ready", "3 ok, 1 failed").

### Level 2 — Sequence Groups

Inside each mapping row, instances are grouped by sequence. Each sequence group shows:

- A checkbox to include/exclude the entire sequence
- The sequence name
- Instance counts
- **Select All / Select None** links

### Level 3 — Instance Table

A detailed table for each sequence group with columns:

| Column | Description |
|--------|-------------|
| **Include** | Checkbox to include/exclude this instance |
| **Track** | Track label (e.g., "V1", "A3") |
| **Start TC** | Timeline start timecode (clickable to copy) |
| **End TC** | Timeline end timecode (clickable to copy) |
| **Status** | Checkmark (ok/would-change/ready) or X (failed) |
| **Notes** | Info button opening a modal with detailed notes |

Each instance row also has a **Show per-track breakdown** toggle. Expanding it lists the clip's individual **video** and **audio channel** sub-rows — useful for linked A/V clips, whose halves are swapped as separate instances.

## Status Icons

| Icon | Meaning |
|------|---------|
| :material-check: Green | Success (after execution) or would-change (after scan) |
| :material-close: Red | Failed — see notes for the error |
| Dimmed row | Excluded by user or skipped |

## Render Limit

To keep the results view responsive, the on-screen table is capped on two levels: at most **100 instances total**, and at most **50 instances per sequence**. The per-sequence cap stops a single large sequence from consuming the whole budget, so instances are distributed more evenly across sequences. When instances are hidden, a hint appears: *"Showing up to 100 instances total (max 50 per sequence). N hidden — export the TXT report for the full list."*

These caps affect the on-screen table only — the exported TXT report always contains every instance.

## Exporting a Report

Click the **Export** button in the results header to save a plain text (`.txt`) report via the file picker. The report includes:

- Build stamp, timestamp, scope, and execution mode (including a **Scan-only** mode when you've scanned but not executed)
- Each mapping with old/new paths and instance counts
- For **Offline/Online**, the **Relink path** and its **Path source** (where the new file was resolved from)
- Per-instance timecode, track, status (including **Ready** and **SKIPPED (unchecked)**), and notes, with **video** / **audio channel** labels per track
- Summary totals (ready, success, failed, skipped)

## Expand / Collapse

Use the **+** and **−** buttons in the results header to expand or collapse all mapping rows at once.
