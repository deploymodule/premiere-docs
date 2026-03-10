# Scrub

**Scrub** is a UXP panel plugin for Adobe Premiere Pro that bundles four post-production modules into a single interface. It replaces scattered manual workflows with batch operations, smart defaults, and team-shareable configurations.

<div class="grid cards" markdown>

-   :package:{ .lg .middle } **Deliverables**

    ---

    Batch-export sequences with custom encoder presets, track selection, and automatic folder organization.

    [:octicons-arrow-right-24: Learn more](deliverables/index.md)

-   :arrows_counterclockwise:{ .lg .middle } **Replace**

    ---

    Find and replace media files across one or more sequences with validation, preservation, and three execution modes.

    [:octicons-arrow-right-24: Learn more](replace/index.md)

-   :page_facing_up:{ .lg .middle } **Template**

    ---

    Create bins and sequences from saved presets, rename items with token-based naming templates, and organize your project.

    [:octicons-arrow-right-24: Learn more](template/index.md)

-   :clapper:{ .lg .middle } **Conform**

    ---

    Flatten nested sequences, export clips via REDLINE, FFmpeg, or AME, and generate FCP XML for DaVinci Resolve.

    [:octicons-arrow-right-24: Learn more](conform/index.md)

</div>

---

## Who is Scrub for?

| Audience | How Scrub Helps |
|----------|-----------------|
| **Beginners** | Simplifies repetitive export tasks into one-click workflows. No scripting required. |
| **Professionals** | Saves hours on deliverables, media versioning, and conform prep with batch operations and smart defaults. |
| **Agencies & Post Houses** | Standardize naming, folder structures, and delivery specs across teams. Share settings between machines. |

---

## Requirements

- **Adobe Premiere Pro 25.6** or later (UXP support required)
- **Windows 10/11** or **macOS 13+**
- **UXP Developer Tools v2.2+** (for loading the plugin during development)

---

## Using the Panel

When you open the Scrub panel, you see the **main menu** with a card for each module. Click a card to enter that module.

- The **← Menu** button in the top-left returns you to the main menu from any module.
- The **gear icon** (:material-cog:) in the top-right (visible on the main menu) opens [Global Settings](global-settings.md) — including settings transfer for sharing configurations between machines.

---

## Quick Links

- [Installation Guide](../getting-started/installation.md)
- [Quick Start](../getting-started/quick-start.md)
- [Global Settings & Transfer](global-settings.md)
- [Troubleshooting](../troubleshooting/index.md)

---

## Technical Notes

Scrub runs as a UXP panel inside Premiere Pro:

- **Runtime**: UXP — Adobe's modern plugin runtime replacing CEP
- **UI Framework**: Svelte compiled to an IIFE bundle
- **Data Storage**: All settings and presets stored in `localStorage`
- **File Access**: UXP persistent tokens for file system operations
- **Export Engine**: Queues exports to Adobe Media Encoder via the `EncoderManager` API
