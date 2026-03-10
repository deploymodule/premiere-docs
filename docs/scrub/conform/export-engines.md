# Export Engines

The Conform module supports three export engines that can work independently or together in a single pipeline.

## REDLINE

**Purpose:** Debayer and export R3D (RED camera RAW) clips.

### Configuration

| Setting | Description |
|---------|-------------|
| **REDLINE binary path** | Path to the REDLINE command-line tool |

### Auto-Detection

Click **Auto** to search for REDLINE in standard locations:

=== "Windows"

    - `C:\Program Files\REDCINE-X PRO 64-bit\Redline.exe`
    - `C:\Program Files\REDCINE-X PRO\Redline.exe`
    - `C:\Program Files (x86)\REDCINE-X PRO\Redline.exe`

=== "macOS"

    - `/Applications/REDCINE-X Professional/REDCINE-X PRO.app/Contents/MacOS/REDline`
    - `/Applications/REDCINE-X PRO.app/Contents/MacOS/REDline`

If auto-detection fails, click **Browse** to locate the executable manually.

### How It Works

1. Scrub generates a batch script with REDLINE commands for each R3D clip.
2. The script is launched as an external process.
3. Scrub waits for completion (10-minute timeout).
4. Rendered clips are verified and their info is recorded.

---

## FFmpeg

**Purpose:** Trim clips by extracting the used portion with handles. Supports two modes.

### Configuration

| Setting | Description |
|---------|-------------|
| **FFmpeg binary path** | Path to the FFmpeg executable |
| **Trim Mode** | Stream Copy (fast) or Re-encode (frame-accurate) |
| **Output Codec** | Only when re-encoding: ProRes 422 HQ (.mov) or DNxHR HQ (.mxf) |

### Auto-Detection

Click **Auto** to search for FFmpeg:

=== "Windows"

    - `C:\ffmpeg\bin\ffmpeg.exe`

=== "macOS"

    - `/usr/local/bin/ffmpeg`

### Trim Modes

=== "Stream Copy (fast)"

    Cuts on keyframes without re-encoding. May include a few extra frames at cut points.

    **Best for I-frame codecs:**

    - Apple ProRes (.mov)
    - Avid DNxHR / DNxHD (.mxf)
    - XAVC (.mxf)
    - AVC-Intra

=== "Re-encode (frame-accurate)"

    Decodes and re-encodes for precise frame cuts. Slower but guaranteed accurate.

    **Required for long-GOP codecs:**

    - H.264 (.mp4)
    - HEVC / H.265 (.mp4)
    - XAVC-L

### FFmpeg + AME Fallback

When both FFmpeg and AME are enabled, AME acts as a **fallback** for any clips that FFmpeg fails to process. This gives you the speed of FFmpeg for most clips with AME as a safety net.

---

## Adobe Media Encoder (AME)

**Purpose:** Render clips using AME encoder presets. The most versatile engine but slower than FFmpeg stream copy.

### Configuration

| Setting | Description |
|---------|-------------|
| **AME Export Preset** | An `.epr` preset file from Adobe Media Encoder |

### Selecting a Preset

The preset dropdown shows all `.epr` files discovered from the system. Use **Browse** to manually select a preset file, or **Refresh** to rescan.

### How It Works

1. For each eligible clip, Scrub queues an export to Adobe Media Encoder.
2. AME renders the clip using the selected preset.
3. Output files are saved to the conform output folder.

---

## Engine Priority

When multiple engines are enabled, they process clips in this order:

1. **REDLINE** — processes R3D clips only
2. **FFmpeg** — processes non-R3D clips (or all clips if REDLINE is off)
3. **AME** — processes remaining clips, or acts as fallback for FFmpeg failures

Clips are never processed by multiple engines — each clip is handled by exactly one engine.
