# Installation

[Get Scrub :material-cart:](https://zachanot.gumroad.com/l/scrub){ .md-button .md-button--primary }

## Step 1 — Download the Plugin

Purchase Scrub from [Gumroad](https://zachanot.gumroad.com/l/scrub). Your download is a single **`.ccx`** file — the Scrub plugin installer. Save it somewhere you can find it (e.g. your Downloads folder). No unzipping needed.

## Step 2 — Install the Plugin

1. **Double-click the `Scrub.ccx` file.** The **Creative Cloud Desktop** app launches (make sure it's installed and you're signed in).
2. A dialog warns that the plugin isn't from the Adobe Marketplace — click **Install** to continue.
3. Because Scrub uses local file access, you may be asked to grant permission — approve it to finish installing.

!!! info "This is normal"
    The "not from the Marketplace" warning appears for every self-distributed plugin. It just means Scrub is delivered directly rather than through Adobe Exchange.

## Step 3 — Open the Panel in Premiere Pro

1. Open **Adobe Premiere Pro** (v25.6 or later).
2. Go to **Window → UXP Plugins → Scrub**.
3. The Scrub panel opens — you're ready to go.

!!! tip "Don't see it under UXP Plugins?"
    - Fully quit and reopen Premiere Pro after installing.
    - If the `.ccx` double-click didn't launch Creative Cloud, install manually with Adobe's Unified Plugin Installer Agent (UPIA):
      - **Windows:** `UnifiedPluginInstallerAgent.exe /install "C:\path\to\Scrub.ccx"`
      - **macOS:** `./UnifiedPluginInstallerAgent --install /path/to/Scrub.ccx`
    - If it still doesn't appear, enable **Developer Mode** under Premiere Pro's **Settings → Plugins** preferences, then restart Premiere.

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

1. Download the latest `.ccx` from your [Gumroad](https://zachanot.gumroad.com/l/scrub) library (buyers get access to updates).
2. Double-click it and click **Install** — it replaces the existing version in place.
3. Restart Premiere Pro to load the updated panel.
