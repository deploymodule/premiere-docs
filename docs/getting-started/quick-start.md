# Quick Start

Export your first batch of deliverables in under 5 minutes.

## 1. Open a Sequence

Open a sequence in Premiere Pro, then click **Refresh** in the Scrub panel to detect it. You'll see the sequence name, timecode range, frame rate, and track counts.

## 2. Choose an Output Folder

Click **Browse** in the Output Location section. Select a folder where exported files will be saved. A green checkmark confirms write permission is granted.

## 3. Create a Delivery Preset

1. Click the **+** button next to the Delivery Preset dropdown.
2. Give your preset a name (e.g., "Client Delivery").
3. Click **Save**.

## 4. Add an Export Configuration

1. Click the **+** button in the "Exports to Generate" section.
2. In the Export Editor, fill in:
    - **Name** — a label for this export (e.g., "Full Mix")
    - **Suffix** — appended to the output filename (e.g., `_FULL`)
    - **Export Preset** — select an Adobe Media Encoder `.epr` preset
    - **Tracks** — choose "All Tracks" or select specific tracks
3. Click **Save**.

!!! tip
    Add multiple export configs to a single delivery preset. Each config produces a separate output file with different settings.

## 5. Export

Click the **Export** button. Scrub will:

1. Create the output directory (with a date subfolder if enabled).
2. For each enabled export, temporarily apply track selection and queue to Adobe Media Encoder.
3. Restore your original track states when finished.

A green checkmark and success message appear when complete.

---

## What's Next?

- [Learn about Delivery Presets](../scrub/deliverables/delivery-presets.md) for reusable export workflows.
- [Set up Track Selection](../scrub/deliverables/track-selection.md) to automate stem exports.
- [Explore all four modules](../scrub/index.md) — Deliverables, Replace, Template, and Conform.
