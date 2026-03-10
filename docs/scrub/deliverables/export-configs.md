# Export Configurations

An **Export Configuration** defines a single output file within a [Delivery Preset](delivery-presets.md). Each configuration specifies what to export and how.

## Adding an Export

1. Select a delivery preset from the dropdown.
2. Click the **+** button in the "Exports to Generate" section.
3. The **Export Editor** opens — configure the fields below, then click **Save**.

## Export Editor Fields

### Name

A display label for this export (e.g., "Full Mix", "Dialog Only"). This is shown in the export list but does not affect the output filename.

### File Suffix

A string appended to the sequence name in the output filename.

| Sequence Name | Suffix | Output Filename |
|---------------|--------|-----------------|
| MySequence | `_FULL` | `MySequence_FULL.mp4` |
| EP01_Edit | `_VO` | `EP01_Edit_VO.mov` |
| A001 | *(empty)* | `A001.mp4` |

A live preview is shown below the field.

### Export Preset

Select an Adobe Media Encoder `.epr` preset from the dropdown. Presets are discovered from the folders configured in [Settings](settings.md).

!!! note
    If no presets appear, go to **Settings → Export Preset Folders** and add the folder containing your `.epr` files. See [Settings](settings.md) for details.

### Track Selection

Choose **All Tracks** or **Selected Tracks** for both video and audio independently. See [Track Selection](track-selection.md) for the full guide.

## Managing Exports

### Enable / Disable

Each export has a **checkbox** in the export list. Disabled exports are dimmed and skipped during batch export. Use this to temporarily exclude an export without removing it.

### Edit

Click an export row (or its pencil icon) to reopen the Export Editor.

### Remove

Click the **×** button on an export row. A confirmation dialog appears before deletion.

### Reorder

Exports run in the order they appear in the list. The order is determined by the sequence they were added.

## What Happens at Export Time

For each **enabled** export configuration, Scrub:

1. Resolves the preset name to a `.epr` file path.
2. Applies track selection (temporarily mutes/unmutes tracks).
3. Builds the output filename: `{SequenceName}{Suffix}.{Extension}`.
4. Queues the export to Adobe Media Encoder.
5. Restores original track mute states.

All exports share the same output folder and optional date subfolder.
