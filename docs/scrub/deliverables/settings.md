# Deliverables Settings

Open the Deliverables settings by clicking the **gear icon** (:material-cog:) in the bottom-right of the Deliverables module.

## Export Preferences

| Setting | Default | Description |
|---------|---------|-------------|
| **Open output folder when export completes** | Off | Opens the output folder in your file explorer after a successful batch export. |
| **Show notifications during export** | Off | Displays progress notifications during the export process. |
| **Search for track strings** | Off | Enables the track filter field in the Export Editor. When on, typing a string auto-selects tracks whose names contain it. See [Track Selection](track-selection.md). |

## Date Folder Format

Controls the date format used when **Add date folder** is enabled.

- **Format dropdown** — Choose from 9 date formats (see [Output Settings](output-settings.md#supported-date-formats) for the full list).
- **Live preview** — Shows today's date in the selected format.
- **Add date folder checkbox** — Toggles date subfolder creation on or off.

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
