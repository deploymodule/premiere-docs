# Installation

## Step 1 — Download the Plugin

Download the latest Scrub release and extract the `dist/` folder to a location on your computer.

## Step 2 — Open UXP Developer Tools

1. Launch **UXP Developer Tools** (UDT v2.2+).
2. Click **Add Plugin**.
3. Navigate to the extracted `dist/` folder and select `manifest.json`.
4. Click **Load** (or **Load & Watch** for development).

!!! tip "Run UDT as Administrator"
    On Windows, running UDT with admin privileges avoids permission issues when loading plugins.

## Step 3 — Open the Panel in Premiere Pro

1. Open **Adobe Premiere Pro** (v25.6 or later).
2. Go to **Window → Extensions → Scrub**.
3. The Scrub panel opens — you're ready to go.

## Platform Notes

=== "Windows"

    - No additional dependencies required.
    - Preset folders are auto-detected from standard Adobe locations.
    - REDLINE and FFmpeg paths are auto-detected if installed in default locations.

=== "macOS"

    - UXP persistent tokens from Windows do not transfer — you'll need to re-browse for preset folders.
    - If using the Conform module's REDLINE feature, the `RedlineLauncher.scpt` file must be compiled once:
      ```bash
      osacompile -o RedlineLauncher.scpt RedlineLauncher.scpt
      ```
    - FFmpeg can be installed via Homebrew: `brew install ffmpeg`.

## Updating

To update Scrub:

1. Replace the `dist/` folder contents with the new version.
2. In UDT, click **Reload** on the Scrub entry.
3. The updated panel loads immediately — no restart required.
