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
| **Status** | Checkmark (ok/would-change) or X (failed) |
| **Notes** | Info button opening a modal with detailed notes |

## Status Icons

| Icon | Meaning |
|------|---------|
| :material-check: Green | Success (after execution) or would-change (after scan) |
| :material-close: Red | Failed — see notes for the error |
| Dimmed row | Excluded by user or skipped |

## Render Limit

If more than **100 instances** are found, only the first 100 are displayed. A hint appears: *"Showing first 100 instances. Export the TXT report for the full report."*

## Exporting a Report

Click the **Export** button in the results header to save a plain text (`.txt`) report via the file picker. The report includes:

- Build stamp, timestamp, scope, and execution mode
- Each mapping with old/new paths and instance counts
- Per-instance timecode, track, status, and notes
- Summary totals (success, failed, skipped)

## Expand / Collapse

Use the **+** and **−** buttons in the results header to expand or collapse all mapping rows at once.
