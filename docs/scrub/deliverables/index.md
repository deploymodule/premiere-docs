# Deliverables

The **Deliverables** module is a batch export system for Adobe Premiere Pro. Define multiple export configurations — each with its own encoder preset, track selection, and file suffix — group them into reusable **Delivery Presets**, and export them all in a single operation.

## How It Works

```mermaid
graph LR
    A[Open Sequence] --> B[Set Output Folder]
    B --> C[Select Delivery Preset]
    C --> D[Configure Exports]
    D --> E[Click Export]
    E --> F[Files Queued to AME]
```

1. **Load your sequence** — click Refresh to detect the active sequence.
2. **Set an output folder** — click Browse to grant file write permission.
3. **Select a Delivery Preset** — or create a new one with the **+** button.
4. **Configure exports** — add one or more export configurations, each with its own preset, suffix, and track selection.
5. **Export** — Scrub queues each enabled export to Adobe Media Encoder.

## Key Concepts

**Delivery Preset**
:   A named group of export configurations. Example: a "Client Delivery" preset might contain three exports — Full Mix, Dialog Only, and Music & Effects.

**Export Configuration**
:   A single output file definition within a delivery preset. Each has a name, file suffix, AME encoder preset, and track selection.

**Track Selection**
:   Each export can target all tracks or specific video/audio tracks. Scrub temporarily mutes/unmutes tracks during export, then restores your original state.

**Preset Resolution**
:   Export configs store preset names (not file paths). At export time, names are resolved to `.epr` files from your configured preset folders. This keeps presets portable across machines.

## Sections

- [Delivery Presets](delivery-presets.md) — creating, editing, and managing presets
- [Export Configurations](export-configs.md) — configuring individual exports
- [Track Selection](track-selection.md) — per-export track filtering
- [Output Settings](output-settings.md) — output folder, date folders, and file naming
- [Settings](settings.md) — preferences, preset folders, and date format
