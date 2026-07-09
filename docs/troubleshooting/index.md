# Troubleshooting

Common issues and their solutions when using Scrub.

## Installation & Loading

### Scrub doesn't appear under Window → UXP Plugins

- Verify you're running **Premiere Pro 25.6** or later (UXP support is required).
- Fully quit and reopen Premiere Pro after installing the `.ccx`.
- Confirm the install finished: Scrub should be listed in the **Plugins** section of the Creative Cloud Desktop app.
- If double-clicking the `.ccx` didn't launch Creative Cloud, install it manually with Adobe's Unified Plugin Installer Agent (UPIA) — see [Installation](../getting-started/installation.md).
- If it still doesn't appear, enable **Developer Mode** under Premiere Pro's **Settings → Plugins** preferences, then restart Premiere.

### Panel appears but shows blank/white

- Fully quit and relaunch Premiere Pro.
- Reinstall the latest `.ccx` from your [Gumroad](https://zachanot.gumroad.com/l/scrub) library in case the download was incomplete.
- Confirm you're on **Premiere Pro 25.6** or later.

### Still having trouble?

- Reinstall the newest version from Gumroad — it replaces the existing install in place.
- If the problem persists, [contact support](../scrub/support.md) with your Premiere Pro version and OS.

---

## Deliverables Module

### "No presets available" in export dropdown

Your AME preset folders aren't configured. Go to **Settings → Export Preset Folders** and add the folder containing your `.epr` files.

Typical locations:

=== "Windows"

    ```
    C:\Users\<you>\Documents\Adobe\Adobe Media Encoder\<version>\Presets\
    ```

=== "macOS"

    ```
    ~/Library/Application Support/Adobe/Adobe Media Encoder/<version>/Presets/
    ```

### Export button is disabled

Check these conditions:

| Issue | Solution |
|-------|----------|
| No sequence loaded | Click **Refresh** in the sequence header |
| No output folder permission | Click **Browse** in Output Location |
| No enabled exports | Enable at least one export checkbox |
| Preset validation error | Ensure each export's preset resolves to a valid `.epr` file |

### Export queues but AME doesn't process

- Make sure Adobe Media Encoder is installed and up to date.
- Try opening AME manually before exporting.
- Check that the `.epr` preset file exists at the resolved path.

---

## Replace Module

### "No selection detected"

- Make sure you've selected items in the correct source (Project Panel or Timeline).
- The panel may lose focus when switching — try selecting items, then clicking **+** quickly.

### Scan finds 0 instances

- Verify the old media in your map actually exists in the scoped sequences.
- Check that sequence scope is correct (All Sequences vs. Selected Sequences).
- Ensure clips haven't been offlined or replaced already.

### Replace mode fails with "SequenceEditor unavailable"

- This can occur if the sequence was closed during execution.
- Keep the target sequence open in the timeline during replacement.

---

## Prep Module

### Naming preview shows "(preview unavailable)"

- Make sure a naming preset is selected.
- Fill in required text token fields.
- Click the refresh button next to Format Preview.

### "Duplicate Names Detected" dialog

This appears when a batch rename would produce identical names for multiple items. You can:

- Click **Rename Anyway** to proceed (items will have the same name).
- Click **Cancel** and adjust token values to create unique names.

### Sequence presets not loading

- Go to the **Sequence Preset Sources** modal (gear icon in the Sequence section).
- Add folders containing `.sqpreset` files.
- Click **Refresh Presets** in the Sequence Group editor.

---

## Conform Module

### "No active sequence" error

Open a sequence in Premiere Pro before clicking Scan Sequence.

### REDLINE not found

1. Install REDCINE-X PRO from [RED's website](https://www.red.com/downloads).
2. Click **Auto** to re-detect, or **Browse** to locate manually.

### FFmpeg not found

=== "Windows"

    Download FFmpeg from [ffmpeg.org](https://ffmpeg.org/download.html) and extract to `C:\ffmpeg\`. The binary should be at `C:\ffmpeg\bin\ffmpeg.exe`.

=== "macOS"

    Install via Homebrew:
    ```bash
    brew install ffmpeg
    ```

### FFmpeg stream copy produces extra frames

Stream copy mode cuts on keyframes, which may include a few extra frames. Switch to **Re-encode mode** for frame-accurate trims. This is expected behavior for long-GOP codecs (H.264, HEVC).

### XML import in Resolve shows wrong timecodes

- Make sure **Group by frame rate** is enabled in Settings to avoid mixed-fps sequences.
- Verify the conform sequence's frame rate matches your Resolve project.

---

## General

### Settings lost after updating

Settings are stored in `localStorage`, which persists across plugin reloads. However, if the plugin ID changes between versions, settings may reset. Use [Settings Transfer](../scrub/global-settings.md) to export and reimport your configuration.

### File picker doesn't open

- This is a UXP permission issue. Fully quit and reopen Premiere Pro.
- On Windows, try launching Premiere Pro as Administrator.
- On macOS, check that Premiere Pro has Full Disk Access in System Preferences → Privacy & Security.

### Cross-platform issues (Windows ↔ macOS)

- UXP persistent tokens (file permissions) do **not** transfer between platforms. You'll need to re-browse for preset folders and output directories.
- Export preset folder paths differ between platforms — reconfigure in Settings.
- REDLINE and FFmpeg paths are platform-specific — use the **Auto** button to detect the correct path on each OS.
