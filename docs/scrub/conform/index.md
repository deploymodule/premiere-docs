# Conform

The **Conform** module takes a Premiere Pro sequence — potentially containing nested sequences — flattens it into a single-track clip list, optionally builds a new simplified sequence, exports media clips through various engines, and generates FCP XML files for import into color grading applications like DaVinci Resolve.

## Workflow

The Conform module is a **four-step wizard**:

```mermaid
graph LR
    A[Step 1: Setup] --> B[Step 2: Preview]
    B --> C[Step 3: Running]
    C --> D[Step 4: Complete]
```

1. **[Setup](setup.md)** — Configure handles, merge gap, mode, and export settings. Scan the active sequence.
2. **Preview** — Review the flat clip list, check for offline clips and clip groups.
3. **Running** — Real-time progress through each pipeline phase.
4. **Complete** — Summary of results, warnings, and output file paths.

## Pipeline Modes

| Mode | Description |
|------|-------------|
| **Prep and Export** | Flatten the sequence, build a new conform sequence, and export. *(Default)* |
| **Export Current** | Read clips from the active timeline as-is and export. No flattening. |
| **Prep Current** | Flatten the sequence and build a conform sequence without exporting. |

## Export Engines

Three export engines can work together in a single pipeline. See [Export Engines](export-engines.md) for details.

| Engine | Purpose | Best For |
|--------|---------|----------|
| **REDLINE** | Debayer and export R3D clips | RED camera footage |
| **FFmpeg** | Trim clips with stream copy or re-encode | Quick extraction of ProRes, DNx, XAVC |
| **Adobe Media Encoder** | Render clips using AME presets | Any format AME supports |

## Key Concepts

**Handles**
:   Extra frames padded before and after each clip's used range. Gives the colorist room to adjust cuts. Default: 48 frames each.

**Clip Groups**
:   When clips have different frame rates or resolutions, they are automatically separated into groups. Each group gets its own sequence and XML file.

**Merge**
:   Adjacent clips from the same source file within a configurable frame gap are merged into a single clip, reducing the number of exports.

**FCP XML**
:   Final Cut Pro XML files generated for import into DaVinci Resolve or other color grading applications. See [FCP XML & Output](fcp-xml.md).

## Third-Party Requirements

The FFmpeg and REDLINE engines require external tools installed on your system:

!!! warning "Install before use"
    - **FFmpeg** must be installed to use the FFmpeg trim engine — [installation guide](prerequisites.md#ffmpeg)
    - **REDCINE-X PRO** must be installed to use the REDLINE engine — [installation guide](prerequisites.md#redcine-x-pro-redline)

    Adobe Media Encoder (AME) is built into your Adobe subscription and requires no additional installation.

## Sections

- [Prerequisites](prerequisites.md) — installing FFmpeg and REDCINE-X PRO
- [Setup & Scanning](setup.md) — configuration, settings modal, and the scan process
- [Export Engines](export-engines.md) — REDLINE, FFmpeg, and AME
- [FCP XML & Output](fcp-xml.md) — XML generation and output folder structure
