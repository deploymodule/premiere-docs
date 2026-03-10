# Replacement Map

**Step 1** of the Replace wizard. Build one or more rows mapping an "Old" (existing) media source to a "New" (replacement) media source.

## Selection Source

A toggle in the top-left switches between two sources for selecting media:

| Source | Icon | Description |
|--------|------|-------------|
| **Project Panel** | :material-folder: | Reads items selected in the Premiere Pro Project Panel |
| **Timeline** | :material-movie-open: | Reads clips selected on the active timeline |

## Adding Entries

1. Select one or more items in the Project Panel (or on the timeline).
2. Click the **+** button.
3. A new mapping row is created with the selected item as the **Old** source. The **New** source is left as "Not set".
4. Select the replacement media in the Project Panel.
5. Click the pointer button on the **New** row to assign it.

!!! tip "Batch Add"
    Select multiple items before clicking **+**. Each item creates its own mapping row. Duplicates within the batch and against existing rows are automatically skipped.

## Entry Cards

Each mapping row shows:

| Element | Description |
|---------|-------------|
| **Old:** | The filename of the current media (full path shown on hover) |
| **New:** | The filename of the replacement media (or "Not set") |
| **Swap** | Swaps old and new sources |
| **Remove** | Deletes the mapping row |

### Visual States

- **Normal** — gray border, both old and new are set.
- **Incomplete** — red-tinted border when old or new is missing.
- **Duplicate** — amber-tinted border when the old source appears in another row.

## Deduplication

Scrub performs two-phase deduplication:

1. **Within the batch** — if you select the same item twice, only one row is created.
2. **Against existing rows** — if the item is already mapped, it's skipped with a message.

Deduplication uses canonical media keys (name + path + ID), case-insensitive name matching, and normalized file paths.

## Validation

The **Next** button is enabled when at least one row has both old and new sources set. Rows with only one source show an error: *"Select both Old and New media."*

Duplicate old sources across rows show a warning but do not block navigation.
