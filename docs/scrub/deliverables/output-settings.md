# Output Settings

## Output Folder

The main Deliverables view shows a read-only **Output Location** preview: the computed output path in monospace, a **✓** (write permission granted) or **⚠** (permission missing) badge, and an **Edit** button.

Click **Edit** (or the gear icon → **Output Location**) to set and build the path in [Settings](settings.md):

- **Browse** — pick the output base folder. Selecting a folder grants Scrub write permission and updates the badge to **✓**.
- **Folder structure builder** — add static and dated folder segments beneath the base path (see [Folder Structure](#folder-structure)).

!!! info "Why do I need to browse?"
    UXP requires explicit file system permission via a persistent token. The Browse action creates this token, granting Scrub write access to the folder across sessions.

If you haven't granted permission yet, the Edit button turns primary and the Export button shows a warning to set the output location in Settings.

## Folder Structure

In **Settings → Output Location**, build a nested folder tree beneath the base path. Two segment types:

| Segment | Button | Description |
|---------|--------|-------------|
| **Static folder** | **+ Add folder** | A fixed-name folder (e.g. `07_Color`, `Exports`). |
| **Dated folder** | **+ Add dated folder** | A folder auto-named from the current date, with a per-segment format dropdown. |

A live preview shows the full computed path as you build it, and the path preview on the main view updates to match. (There is no longer a single "Add date folder" checkbox — a date folder is just a dated segment.)

## Sub Folders

The **Sub Folders** dropdown (in [Settings](settings.md) → Export) controls where each export file is placed *under* the output path. It applies to **both** Selected (single-sequence) and Batch exports. Three modes:

| Mode | Result |
|------|--------|
| **Each Sequence as Sub Folders** *(default)* | Each sequence's exports go into a `‹SequenceName›/` sub-folder. |
| **Mirror Project Panel Bin Structure As Sub Folders** | Each sequence routes into a sub-folder matching its **bin (folder) hierarchy** in the Project panel. |
| **None** | All exports land directly under the output path, with no sub-folder. |

### Mirror Bin example

With output base `D:\Deliveries`, **Mirror Bin** mode, and this Project panel structure:

```
Project
├── 01_Promos
│    └── Spot_30  (sequence)
└── 02_Social
     └── Reel_A   (sequence)
```

the export writes:

```
D:\Deliveries\01_Promos\Spot_30_MASTER.mov
D:\Deliveries\02_Social\Reel_A_MASTER.mov
```

### Behavior notes

- **Root-level sequences** — in Mirror Bin mode, a sequence at the project root (no enclosing bin) exports to the base path with no stray folder.
- **Nested bins** — the full bin chain is mirrored, outermost folder first.
- **Illegal characters** — bin and sequence names are sanitized for the file system. Characters that are illegal on Windows or macOS (`<>:"/\|?*`) are stripped, so a bin named `A/B` or `My:Seq` produces a safe folder name and never escapes the output path.
- **Export-time accuracy** — bin paths are read at export time, so moving a sequence to a different bin after adding it to a batch uses its **current** location.
- **Duplicate names** — sequences that share a name but live in different bins land in different folders. Where two output files would still collide in one run (e.g. flat **None** mode with same-named sequences), Scrub auto-suffixes the filename (`_2`, `_3`, …) to avoid overwriting.
- **Date folders** — dated folder segments are applied first; sub-folders are created beneath them.

### Batch list breadcrumbs

In **Batch** scope with Mirror Bin mode, the batch sequence list shows a muted breadcrumb (e.g. `01_Promos /`) above each sequence name so you can see where each file will land.

!!! tip "Refresh after moving bins"
    Moving a sequence between bins in the Project panel does not automatically refresh the displayed breadcrumbs. Click the **↻ refresh** button next to the Selected/Batch toggle to re-read each sequence's current name and bin path. (The export itself always uses the current bin path regardless of the displayed breadcrumb.)

### Supported Date Formats

Dated folder segments and the `{date}` [suffix token](export-configs.md#suffix-tokens) share the same 13 formats:

| Format | Example |
|--------|---------|
| MMDD | 0310 |
| DDMM | 1003 |
| MMDDYY | 031026 |
| DDMMYY | 100326 |
| YYMMDD | 260310 |
| MMDDYYYY | 03102026 |
| DDMMYYYY | 10032026 |
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

!!! note "Collision protection"
    If two outputs in a single export run would resolve to the same filename in the same folder (case-insensitively) — for example same-named sequences batched with **Sub Folders** set to *None* — Scrub appends `_2`, `_3`, … before the extension so nothing is overwritten. The queued item is flagged as *renamed to avoid overwrite*.

## Folder Permission Modal

If you click **Export** without having browsed for a folder, a permission modal appears:

1. It explains that Scrub needs write permission.
2. If a project folder is detected, it's shown as a recommended location.
3. Click **Select Folder...** to open the file picker.
4. After selecting a folder, the export continues automatically.
