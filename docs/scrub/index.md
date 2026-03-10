# Scrub Overview

**Scrub** is a UXP panel plugin for Adobe Premiere Pro (v25.6+) that bundles four modules into a single interface. Each module targets a specific post-production workflow.

## Modules

| Module | Icon | Purpose |
|--------|------|---------|
| [**Deliverables**](deliverables/index.md) | :package: | Batch-export sequences with custom encoder presets and per-export track selection. |
| [**Replace**](replace/index.md) | :arrows_counterclockwise: | Find and replace media files across sequences with validation and three execution modes. |
| [**Template**](template/index.md) | :page_facing_up: | Create bins/sequences from saved presets, rename items with token-based naming, and organize your project. |
| [**Conform**](conform/index.md) | :clapper: | Flatten nested sequences, export clips via REDLINE / FFmpeg / AME, and generate FCP XML for color grading. |

## Navigation

When you open the Scrub panel, you see the **main menu** with a card for each module. Click a card to enter that module.

- The **← Menu** button in the top-left returns you to the main menu from any module.
- The **gear icon** (:material-cog:) in the top-right (visible on the main menu) opens [Global Settings](global-settings.md) — including settings transfer for sharing configurations between machines.

## Architecture at a Glance

Scrub runs as a UXP panel inside Premiere Pro. Key technical details:

- **Runtime**: UXP (Unified eXtensibility Platform) — Adobe's modern plugin runtime replacing CEP.
- **UI Framework**: Svelte compiled to an IIFE bundle.
- **Data Storage**: All settings and presets are stored in `localStorage`, organized by module.
- **File Access**: Uses UXP persistent tokens for file system operations (browse dialogs grant permission).
- **Export Engine**: Queues exports to Adobe Media Encoder (AME) via the `EncoderManager` API.
