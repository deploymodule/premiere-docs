# Delivery Presets

A **Delivery Preset** is a named collection of [export configurations](export-configs.md). Each preset groups the outputs you need for a specific delivery scenario.

## Examples

| Preset Name | Exports |
|-------------|---------|
| Client Delivery | Full Mix, Dialog Only, M&E |
| Social Package | 16:9 Full, 9:16 Vertical, 1:1 Square |
| Internal Review | ProRes HQ, H.264 Proxy |

## Creating a Preset

1. Click the **+** button next to the Delivery Preset dropdown.
2. Enter a **Name** (e.g., "Client Delivery").
3. Optionally add a **Description** (shown below the dropdown when the preset is selected).
4. Click **Save**.

The new preset is selected automatically and ready for you to add export configurations.

## Editing a Preset

1. Select the preset from the dropdown.
2. Click the **pencil icon** (:material-pencil:) to open the preset editor.
3. Update the name or description.
4. Click **Save**.

## Deleting a Preset

1. Open the preset editor (pencil icon).
2. Click **Delete** (bottom-left, red button).
3. Confirm the deletion in the dialog.

!!! warning
    Deleting a preset removes all its export configurations. This cannot be undone.

## Switching Presets

Use the **Delivery Preset** dropdown to switch between presets. The export list updates immediately to show the selected preset's configurations.

## Sharing Presets Between Machines

Delivery presets are included in the [Settings Transfer](../global-settings.md) feature. Export your settings to a JSON file, transfer it to another machine, and import — your presets are merged alongside existing ones without deleting anything.
