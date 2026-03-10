# Setup & Scanning

**Step 1** of the Conform wizard. Configure conform parameters, export settings, and scan the active sequence.

## Setup Parameters

These appear directly on the setup screen:

| Parameter | Range | Default | Description |
|-----------|-------|---------|-------------|
| **Max tracks to scan** | 1–99 | 99 | Number of video tracks to read from the sequence. |
| **Start handle frames** | 0–240 | 48 | Extra frames before each clip's source in-point. |
| **End handle frames** | 0–240 | 48 | Extra frames after each clip's source out-point. |
| **Merge gap (frames)** | 0–240 | 0 (disabled) | Adjacent clips from the same source within this gap are merged. |
| **Mode** | Dropdown | Prep and Export | Pipeline mode (see below). |

### Pipeline Modes

| Mode | What It Does |
|------|-------------|
| **Prep and Export** | Flatten → Build sequence → Export → Generate XML |
| **Export Current** | Read current timeline → Export → Generate XML |
| **Prep Current** | Flatten → Build sequence only (no export, no XML) |

## Settings Modal

Click the **gear icon** (:material-cog:) to open the full settings modal.

### Output Base Path

Click **Browse** to select the root output folder. A green badge shows "Folder set" when configured.

!!! info
    An output folder is required for export and XML generation. Without it, those pipeline steps are skipped.

### Output Folder Structure

Build a nested folder hierarchy for your output. Two types of segments:

| Type | Icon | Description |
|------|------|-------------|
| **Static folder** | :material-folder: | A fixed-name folder (e.g., "07_Color", "to Color") |
| **Dated folder** | :material-calendar: | A folder named from the current date in a chosen format |

**Default structure:** `07_Color / to Color / MMDDYY`

A live preview shows the computed path, e.g., `D:\Projects\07_Color\to Color\031026`.

Use **+ Add folder** and **+ Add dated folder** to build your structure. Click **×** on any segment to remove it (and everything below it).

### Sequence Name Suffix

Text appended to the source sequence name when creating the conform sequence.

| Source Sequence | Suffix | Conform Sequence |
|----------------|--------|------------------|
| A001 | `_CONFORM` | A001_CONFORM |
| EP01_Edit | `_CLR` | EP01_Edit_CLR |

### Clip Grouping

| Setting | Default | Description |
|---------|---------|-------------|
| **Group by frame rate** | On | Separate clips with different fps into distinct sequences/XML files |
| **Group by dimensions** | On | Separate clips with different resolutions into distinct sequences/XML files |

When multiple groups are detected, each gets its own conform sequence and FCP XML file.

### Export Options

Four checkboxes to enable/disable each export engine:

| Option | Default | Description |
|--------|---------|-------------|
| **R3D clips via REDLINE** | On | Export .R3D source clips through REDLINE |
| **Trim clips via FFmpeg** | Off | Trim non-R3D clips using FFmpeg |
| **Render clips in Adobe Media Encoder** | On | Export non-R3D clips through AME |
| **Generate FCP XML** | On | Generate Final Cut Pro XML files |

See [Export Engines](export-engines.md) for engine-specific settings.

## Scanning

Click **Scan Sequence** to read the active sequence.

**What happens during scan:**

1. The active sequence is read (including nested sequences for Prep and Export mode).
2. Clips are flattened into a single-track list.
3. Adjacent clips from the same source are merged (if merge gap > 0).
4. Clips are grouped by fps and/or dimensions (if enabled).
5. The preview is populated with the result.

After scanning, you advance to the **Preview** step showing the flat clip list with:

- Total clip count, R3D count, non-R3D count, offline count
- Approximate total duration
- A table with clip name, start TC, and end TC for each clip
- Banners for merged clips, multiple groups, or offline warnings
