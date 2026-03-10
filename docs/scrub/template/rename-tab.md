# Rename Tab

The Rename tab lets you batch-rename items using token-based [naming presets](naming-presets.md). It supports two modes: renaming selected project items, or formatting/versioning the project file itself.

## Workflow

### Renaming Selected Items

1. Select a **naming preset** from the dropdown (or create one with **+**).
2. Fill in the **token values** — text fields, dropdowns, etc. appear based on the preset's tokens.
3. Check the **Format Preview** to see the generated filename.
4. Select items in Premiere Pro's Project Panel.
5. Click **Rename**.

All selected items are renamed using the naming preset's formula.

### Renaming the Project File

1. Click the **Rename Target** button and switch to **Active Project** mode.
2. Select a naming preset and fill in token values.
3. Click **Format Project**.

Scrub performs a **Save As** with the generated filename. The project remains open at the new path.

!!! info
    In Active Project mode, sequence-specific and clip-specific dynamic tokens (like Source Name) are unavailable, since there's no specific clip context.

## Token Input Fields

Below the action buttons, dynamically generated input fields appear based on the active preset's tokens:

| Token Type | Input |
|------------|-------|
| **Text** | Text input field with label and optional default value |
| **Choice** | Dropdown select populated from inline options or a linked reusable dropdown |
| **Dynamic** | Read-only display showing auto-computed value (project name, frame rate, etc.) |
| **Counter** | Read-only display showing the formatted counter value (e.g., "v001") |
| **Separator** | Text input pre-filled with the separator character |

## Format Preview

A live preview shows the complete filename that will be generated from the current token values. It updates as you type.

- **Warnings** appear in amber (e.g., empty required fields).
- **Errors** appear in red (e.g., missing preset configuration).

Click the **refresh button** to regenerate the preview.

## Version Up

The **Version Up** button increments the counter token and performs the rename:

=== "Selected Items"

    Clones the selected sequence, moves the clone to the same bin, and renames it with an incremented counter. The original sequence is untouched.

=== "Active Project"

    Detects the current version from the project filename, increments the counter, generates a new filename, and performs a `Save As`. If the generated name already exists on disk, the counter bumps further (up to 30 attempts).

## Collision Detection

Before executing a batch rename, Scrub checks if any items would receive the same name. If duplicates are found, a confirmation dialog lists the duplicate names. You can proceed with **Rename Anyway** or **Cancel**.

## Settings

Click the **gear icon** (:material-cog:) in the Presets section header to open **Rename Settings**:

- **Reusable Dropdowns** — Create and manage named option lists that can be linked to choice tokens across presets.
- **Separator Settings** — Configure default separator character, trim ends, collapse duplicates, and strip illegal characters.
- **Format Defaults** — Set default date and duration formats for dynamic tokens.
