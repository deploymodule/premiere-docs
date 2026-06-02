# Prep

The **Prep** module is a toolkit for getting a project and its timelines ready for the rest of your workflow. It provides four tabs: **Create** for building bins and sequences from saved presets, **Rename** for batch-renaming items with token-based naming presets, **Organize** for structuring project contents, and **Trim** for source-handle and disabled-clip cleanup on the timeline.

!!! note "Formerly the Template module"
    Prep is the successor to what earlier versions called the **Template** module. The Create, Rename, and Organize tabs carry over unchanged; the **Trim** tab is new. (Several experimental tools — Sort, Flatten, Timecode Sync, Close Gaps, and Normalize Durations — were removed, so the module now focuses on the operations that proved reliable.)

## Tabs

| Tab | Purpose |
|-----|---------|
| [**Create**](create-tab.md) | Build bin hierarchies and batch-create sequences from `.sqpreset` files |
| [**Rename**](rename-tab.md) | Rename selected items or the project file using naming presets |
| [**Organize**](organize-tab.md) | Mirror folder structures, sort by date, clean up unused media |
| [**Trim**](trim-tab.md) | Set source in/out handles on selected clips, and remove disabled (muted) track items |

## Templates

The **Create**, **Rename**, and **Organize** tabs share a top-level container still called a **Template** — it groups your bin presets, sequence preset groups, and naming presets. You can create multiple templates — for example, one per client or workflow — and switch between them using the dropdown at the top of those tabs.

To create or rename a template, use the **+** or **pencil** buttons next to the template dropdown. (The Trim tab works on the current timeline directly and does not use templates.)

## Key Concepts

**Bin Presets**
:   Saved folder hierarchies captured from your project. Recreate the same bin structure in any project with one click.

**Sequence Preset Groups**
:   Curated sets of Premiere Pro `.sqpreset` files. Batch-create multiple sequences at once.

**Naming Presets**
:   Token-based filename formulas. Combine text, counters, dropdowns, dynamic values, and separators to build consistent filenames.

**Reusable Dropdowns**
:   Named option lists (e.g., "Clients", "Aspect Ratios") that can be linked to choice tokens across multiple naming presets. Update the list once and it propagates everywhere.

## Sections

- [Create Tab](create-tab.md) — bin presets and sequence creation
- [Rename Tab](rename-tab.md) — batch renaming and version-up
- [Naming Presets](naming-presets.md) — the token-based naming system in depth
- [Organize Tab](organize-tab.md) — project cleanup tools
- [Trim Tab](trim-tab.md) — source-handle trimming and disabled-clip removal
