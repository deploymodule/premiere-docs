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
