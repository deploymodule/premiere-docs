# Output Settings

## Output Folder

Click **Browse** to select an output folder. A UXP file picker opens — select any folder on your system. Once selected:

- A **green checkmark** confirms write permission.
- The **path preview** shows the full output path in monospace text.

!!! info "Why do I need to browse?"
    UXP requires explicit file system permission via a persistent token. The Browse action creates this token, granting Scrub write access to the folder across sessions.

If you haven't browsed yet, the Export button shows a warning: *"Click Browse in Output Location to grant write permission."*

## Date Folders

When **Add date folder** is enabled (in [Settings](settings.md)), Scrub creates a date-stamped subfolder inside the output directory.

| Date Format | Example Folder |
|-------------|----------------|
| `MMDDYY` | `031026/` |
| `YYYYMMDD` | `20260310/` |
| `YYYY-MM-DD` | `2026-03-10/` |
| `MMM DD YYYY` | `Mar 10 2026/` |

The path preview updates in real time to show the full path including the date subfolder.

## Bin Structure Subfolders

When **Batch: mirror Project Panel bin structure as sub-folders** is enabled (in [Settings](settings.md)), a **batch** export routes each sequence into a sub-folder that matches its **bin (folder) hierarchy in the Project Panel**, created beneath the output folder.

This only applies to **batch** exports (multiple sequences). Single-sequence exports are unaffected.

### Example

With output base `D:\Deliveries` and this Project Panel structure:

```
Project
├── 01_Promos
│    └── Spot_30  (sequence)
└── 02_Social
     └── Reel_A   (sequence)
```

A batch export with the toggle **on** writes:

```
D:\Deliveries\01_Promos\Spot_30_MASTER.mov
D:\Deliveries\02_Social\Reel_A_MASTER.mov
```

With the toggle **off** (the default), both files land directly in `D:\Deliveries\`.

### Behavior notes

- **Root-level sequences** — a sequence that sits at the project root (no enclosing bin) always exports to the base path, whether the toggle is on or off. No stray folder is created for it.
- **Nested bins** — the full bin chain is mirrored, outermost folder first. Deeply nested sequences get the complete folder path.
- **Illegal characters** — bin names are sanitized for the file system. Characters that are illegal on Windows or macOS (`<>:"/\|?*`) are stripped, so a bin named `A/B` or `My:Seq` produces a safe folder name and never escapes the output path.
- **Export-time accuracy** — the bin path is read at export time, so if you move a sequence to a different bin after adding it to the batch, the export uses its **current** location.
- **Duplicate names** — sequences that share a name but live in different bins are naturally separated into different folders, avoiding the file collision they would have in a flat batch.
- **Date folders** — if **Add date folder** is also enabled, the date folder is applied first and bin subfolders are created beneath it.

### Batch list breadcrumbs

When the toggle is on, the batch sequence list shows a muted breadcrumb (e.g. `01_Promos /`) above each sequence name so you can see where each file will land. With the toggle off, the list looks unchanged.

!!! tip "Refresh after moving bins"
    Moving a sequence between bins in the Project Panel does not automatically refresh the batch list breadcrumbs. Click the **↻ refresh** button next to the Batch/Active toggle to re-read the current name and bin path for every sequence in the batch. (The export itself always uses the current bin path regardless of the displayed breadcrumb.)

### Supported Date Formats

| Format | Example |
|--------|---------|
| MMDDYY | 031026 |
| DDMMYY | 100326 |
| YYMMDD | 260310 |
| YYYYMMDD | 20260310 |
| YYYY-MM-DD | 2026-03-10 |
| MM-DD-YYYY | 03-10-2026 |
| DD-MM-YYYY | 10-03-2026 |
| MMM DD YYYY | Mar 10 2026 |
| DD MMM YYYY | 10 Mar 2026 |

## Output Filename

Each export produces a file named:

```
{SequenceName}{Suffix}.{Extension}
```

| Component | Source |
|-----------|--------|
| Sequence Name | The active Premiere Pro sequence name |
| Suffix | From the export configuration (e.g., `_FULL`, `_VO`) |
| Extension | Determined by the AME encoder preset |

### Example

With sequence "EP01_FinalCut", suffix "_DLG", and an H.264 preset:

```
EP01_FinalCut_DLG.mp4
```

## Folder Permission Modal

If you click **Export** without having browsed for a folder, a permission modal appears:

1. It explains that Scrub needs write permission.
2. If a project folder is detected, it's shown as a recommended location.
3. Click **Select Folder...** to open the file picker.
4. After selecting a folder, the export continues automatically.
