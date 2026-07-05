# Setup & Scanning

**Step 1** of the Conform wizard. Configure conform parameters, export settings, and scan your chosen sequence.

## Choosing the Sequence

At the top of the setup screen, the **sequence picker** controls what Conform operates on. A **Selected / Batch** toggle switches between two modes:

=== "Selected (default)"

    Conform operates on the sequence **currently selected in the Project panel** — falling back to the active sequence if nothing is selected. The card shows the sequence name; click the **↻ refresh** button to re-read the current Project-panel selection.

=== "Batch"

    Conform processes **multiple sequences** in one run, one after another. The batch starts **empty**:

    1. Select one or more sequences in the Premiere Pro Project panel.
    2. Click the **+** button to add them to the batch (duplicates are skipped).
    3. Repeat to add more; click **×** on a row to remove one, or **Clear** to empty the batch.
    4. The **↻ refresh** button re-queries every sequence in the batch for its current name (e.g. after renaming them).

    Each sequence in the batch is flattened, built, and exported using the same settings. The **Complete** step then shows a per-sequence summary — a header like *"3 sequences · 2 succeeded · 1 partial · 0 failed"* and one row per sequence tagged **OK**, **Partial**, or **Failed**.

!!! note
    The setup parameters and settings below apply to **every** sequence in a batch run.

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

Use **+ Add folder** and **+ Add dated folder** to build your structure. Click **×** on any segment to remove just that segment — the remaining segments keep their order.

### Sub Folders

The **Sub Folders** dropdown controls where each conform's output lands *beneath* the folder-structure chain above. It has three modes:

| Mode | Result |
|------|--------|
| **Each Sequence as Sub Folders** *(default)* | Each conformed sequence gets its own `‹SequenceName›/` folder. In a batch, duplicate sequence names are auto-suffixed `_2`, `_3`, … so they never collide. |
| **Mirror Project Panel Bin Structure As Sub Folders** | Output is routed into a sub-folder matching the source sequence's **bin (folder) hierarchy** in the Project panel. |
| **None** | Output (and the engine's `R3D` / `MOV` / `XML` / `TRIMMED` sub-folders) lands directly under the folder-structure chain, with no per-sequence folder. |

!!! warning "Overwrite risk in batch runs"
    In **Mirror Bin** and **None** modes, several sequences in a batch can share one output folder. If those sequences reference the same source clip but trim it differently, the exports can **overwrite each other**. Use **Each Sequence as Sub Folders** (the default) when batching sequences that share media.

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
| **R3D clips via REDline** | On | Export .R3D source clips through REDline |
| **Trim clips via FFmpeg** | Off | Trim non-R3D clips using FFmpeg |
| **Render clips in Adobe Media Encoder** | On | Export non-R3D clips through AME |
| **Generate FCP XML** | On | Generate Final Cut Pro XML files |

See [Export Engines](export-engines.md) for engine-specific settings.

!!! info "Required settings are checked before the run starts"
    When you start the conform run, Scrub first validates that the settings each enabled step needs are present. If anything is missing it shows an inline message — for example *"Configure required settings: output folder, AME export preset."* — instead of failing partway through the pipeline. Open the settings modal to fill in the listed items. Required settings are: an **output folder**; a **REDLINE path** if R3D-via-REDLINE is on; an **AME export preset** if AME rendering is on; and an **FFmpeg binary path** if FFmpeg trimming is on.

## Scanning

Click **Scan Sequence** to read your chosen sequence (the one selected in the Project panel, or in **Batch** mode a preview of the first sequence in the batch).

**What happens during scan:**

1. The selected sequence is read (including nested sequences for Prep and Export mode).
2. Clips are flattened into a single-track list.
3. Adjacent clips from the same source are merged (if merge gap > 0).
4. Clips are grouped by fps and/or dimensions (if enabled).
5. The preview is populated with the result.

After scanning, you advance to the **Preview** step showing the flat clip list with:

- Total clip count, R3D count, non-R3D count, offline count
- Approximate total duration
- A table with clip name, start TC, and end TC for each clip
- Banners for merged clips, multiple groups, or offline warnings
