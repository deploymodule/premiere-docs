# Track Selection

Each [export configuration](export-configs.md) can target **all tracks** or **specific tracks** for both video and audio independently. This lets you create stem exports, dialog-only deliverables, or graphics-free versions from a single sequence.

## Selection Modes

### All Tracks

The default. Every video or audio track in the sequence is included in the export.

### Selected Tracks

Check individual tracks to include. Unchecked tracks are temporarily muted during this export, then restored afterward.

When you switch to Selected Tracks, a list of all tracks appears with checkboxes. Each track shows:

- **Track label** (e.g., "V1 - GFX", "A3 - SFX")
- **"empty" badge** — if the track has no clips
- **"muted" badge** — if the track is currently muted in the timeline (audio only)

Use the **Select All** / **Deselect All** buttons to quickly toggle all tracks.

## Track Filter (Auto-Matching)

When the **Search for track strings** setting is enabled (in [Settings](settings.md)), a text filter field appears in Selected Tracks mode.

Type a string to auto-select tracks whose names contain that string (case-insensitive, 300ms debounce).

| Filter String | Matches |
|---------------|---------|
| `Dialog` | A1 - Dialog, A4 - Dialog BG |
| `SFX` | A3 - SFX |
| `GFX` | V3 - GFX, V4 - GFX Lower |

This is especially powerful for standardized track naming across projects — define the filter once in the export config and it auto-selects the right tracks in every sequence.

!!! tip "Workflow Example"
    Create an export called "Dialog Only" with audio filter set to `Dialog`. Open any sequence with dialog tracks named consistently, and the right tracks are selected automatically.

## How Track Selection Works Internally

Scrub uses a **mute/unmute strategy** for track selection:

1. Before each export, Scrub saves the current mute state of all tracks.
2. Tracks not included in the export are temporarily muted.
3. The export is queued to Adobe Media Encoder.
4. Original mute states are restored — even if the export fails.

This means your timeline is never permanently altered by the export process.

## Audio Modes

When audio tracks are set to **Selected Tracks**, the audio mode is automatically set to **Solo** — meaning only the selected audio tracks are included. When set to **All Tracks**, audio mode is **Mix** (all tracks mixed together).
