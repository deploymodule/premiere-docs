# Global Settings

Access global settings by clicking the **gear icon** (:material-cog:) in the top-right of the main Scrub menu.

## Settings Transfer

Share your Scrub configuration between machines or team members.

### Exporting Settings

1. Click **Export Settings**.
2. Select a folder in the file picker.
3. Scrub writes `scrub-settings.json` to the chosen folder.

### What's Included in the Export

| Category | Details |
|----------|---------|
| **Delivery Presets** | All presets with their export configurations |
| **App Preferences** | Date format, notifications, folder-on-complete, date folder toggle, track string search, built-in presets toggle |
| **Naming Choice Options** | Custom choice options from the Template module's naming system |

### What's Excluded

Machine-specific data that wouldn't work on another computer:

- UXP persistent tokens (file system permissions)
- File system paths (output folders, preset folder locations)
- Preset location settings

### Importing Settings

1. Click **Import Settings**.
2. Select a `scrub-settings.json` file.
3. A **confirmation dialog** shows what will happen:
    - :material-plus: **Added** — new presets and choice options
    - :material-update: **Updated** — app preferences
    - :material-approximately-equal: **Skipped** — duplicates already in your configuration
4. Review the summary and click **Import** to apply, or **Cancel**.

### Merge Strategy

Imports are **additive** — your existing data is never deleted.

| Data | Strategy | Duplicate Detection |
|------|----------|---------------------|
| **Delivery Presets** | New presets are appended. Existing presets are never modified or removed. | By preset name (exact match) |
| **App Preferences** | All portable fields are overwritten with imported values. | N/A — always applied |
| **Choice Options** | New options are added. Existing options are skipped. | By label (case-insensitive) |

!!! info "Fresh IDs"
    Imported presets and choice options receive new unique IDs to avoid conflicts with existing data.

## About

The global settings modal also displays:

- **Plugin version** (e.g., Scrub UXP v1.0.0)
- **Build ID** (for development builds)
- **Target platform** (Premiere Pro 25.6+)
