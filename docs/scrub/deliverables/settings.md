# Deliverables Settings

Open the Deliverables settings by clicking the **gear icon** (:material-cog:) in the bottom-right of the Deliverables module. The settings modal has three sections: **Output Location**, **Export**, and **Export Presets**.

## Output Location

Set and build your output path here. This section is the single place to grant folder permission and shape the folder tree; the main Deliverables view only shows a read-only preview of the result.

- **Browse** — pick the output base folder. A UXP file picker opens; selecting a folder grants Scrub write permission (a persistent token) and shows a green checkmark.
- **Folder structure builder** — beneath the base path, add nested folder segments:
    - **+ Add folder** — a fixed-name **static** folder (e.g. `07_Color`, `Exports`).
    - **+ Add dated folder** — a folder auto-named from the current date, with a per-segment format dropdown (see [Supported Date Formats](output-settings.md#supported-date-formats)).
- **Live preview** — a monospace line shows the full computed path as you build it.

See [Output Settings](output-settings.md) for the full walkthrough and examples.

## Export

| Setting | Default | Description |
|---------|---------|-------------|
| **Show notifications during export** | Off | Displays progress notifications during the export process. |
| **Search for track strings** | Off | Enables the track filter field in the Export Editor. When on, typing a string auto-selects tracks whose names contain it. See [Track Selection](track-selection.md). |
| **Sub Folders** | Each Sequence as Sub Folders | A dropdown controlling where each export file is placed under the output path. Applies to **both** Selected and Batch scope. See [Sub Folders](output-settings.md#sub-folders). |

### Sub Folders modes

| Mode | Result |
|------|--------|
| **Each Sequence as Sub Folders** *(default)* | Each sequence's exports go into a `‹SequenceName›/` sub-folder. |
| **Mirror Project Panel Bin Structure As Sub Folders** | Each sequence routes into a sub-folder matching its bin (folder) hierarchy in the Project panel. |
| **None** | All exports land directly under the output path with no sub-folder. |

!!! info "Default date format"
    New dated folder segments and the `{date}` suffix token both use Scrub's default date format. There is no separate "Add date folder" checkbox — date folders are just dated segments you add in the folder builder above.

## Export Preset Folders

Manages the folders where Scrub scans for Adobe Media Encoder `.epr` preset files.

### Adding a Preset Folder

1. Click the **+** button.
2. Select a folder containing `.epr` files in the file picker.
3. Scrub validates the folder (checks it exists and contains `.epr` files).
4. If valid, the folder is added to the list and presets are rescanned.

### Removing a Preset Folder

Click the red **×** button next to a folder path to remove it.

### Rescanning

Click **Rescan Presets** to re-read all configured folders for preset files. Use this after adding new `.epr` files to a folder.

### Auto-Detection

On first run, Scrub automatically discovers default Adobe Media Encoder preset folders. If none are found, you're prompted to select a folder manually.

### Built-In Presets

Enable **Include built-in preset names** as a fallback when no `.epr` files are found. This provides a list of common preset names, though they cannot be resolved to file paths for actual export.

!!! tip "Where are my .epr files?"
    Adobe Media Encoder presets are typically located in:

    - **Windows**: `C:\Users\<you>\Documents\Adobe\Adobe Media Encoder\<version>\Presets\`
    - **macOS**: `~/Library/Application Support/Adobe/Adobe Media Encoder/<version>/Presets/`

    You can also export custom presets from AME to any folder and point Scrub there.
