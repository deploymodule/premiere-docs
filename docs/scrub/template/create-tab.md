# Create Tab

The Create tab lets you build bin (folder) hierarchies and batch-create sequences from saved presets.

## Bin Presets

### What Are Bin Presets?

A bin preset saves a folder hierarchy from your project that you can recreate in any other project with one click. For example, you might save a standard folder structure like:

```
Audio/
  ├── Dialog/
  ├── Music/
  └── SFX/
Video/
  ├── Footage/
  ├── Graphics/
  └── B-Roll/
```

### Capturing a Bin Preset

1. Create your desired folder structure in Premiere Pro's Project Panel.
2. Select the top-level bin(s) you want to capture.
3. In the Template module's Create tab, click the **+** button in the Bin Preset section.
4. Click **Save Bin(s)** in the modal to read the selected hierarchy.
5. Enter a **Preset Name** (e.g., "Standard Project Folders").
6. Click **Save**.

The preset now appears in the bin preset dropdown.

### Creating Bins from a Preset

1. Select a bin preset from the dropdown.
2. Optionally select a target bin in the Project Panel (bins will be created inside it).
3. Click **Create**.

The entire folder hierarchy is recreated in your project.

### Editing / Deleting

- Click the **pencil icon** to edit a bin preset (recapture from selection or rename).
- Click **Delete** in the editor modal to remove the preset.

---

## Sequence Preset Groups

### What Are Sequence Preset Groups?

A sequence preset group is a curated set of Premiere Pro sequence presets (`.sqpreset` files). Create all sequences in a group with one click — useful for standardized project setups.

### Setting Up Sequence Preset Sources

Before creating groups, tell Scrub where your `.sqpreset` files live:

1. Click the **gear icon** (:material-cog:) in the Sequence section.
2. In the **Sequence Preset Sources** modal, click **+ Add Folder**.
3. Select a folder containing `.sqpreset` files.
4. Repeat for additional folders.
5. Click **Done**.

### Creating a Sequence Preset Group

1. Click the **+** button in the Sequence section.
2. Enter a **Group Name** (e.g., "4K Project Setup").
3. Click **Refresh Presets** to scan all source folders.
4. A folder tree shows all discovered `.sqpreset` files, organized by directory.
5. Check the presets you want in this group.
6. Click **Save**.

### Creating Sequences from a Group

1. Select a group from the dropdown.
2. Click **Create**.
3. One sequence is created for each preset in the group.

### Editing / Deleting

- Click the **pencil icon** to add or remove presets from a group.
- Click **Delete** in the editor modal to remove the group.
