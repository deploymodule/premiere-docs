# Naming Presets

A **naming preset** defines a filename formula as an ordered list of tokens. Each token contributes a segment to the final filename.

## Token Types

### Text

A free-text field that the user fills in at rename time.

- **Label** — display name (e.g., "Project Name", "Client")
- **Default Value** — pre-filled value (optional)

### Counter

An auto-incrementing number. Configured in the **Counter tab** of the preset editor.

| Setting | Description | Default |
|---------|-------------|---------|
| **Padding Width** | Number of digits (1–4) | 2 |
| **Prefix** | String prepended to the number (e.g., "v") | *(empty)* |
| **Start Value** | Initial counter value | 1 |
| **Increment By** | Step between items | 1 |

**Examples:**

| Padding | Prefix | Value | Output |
|---------|--------|-------|--------|
| 3 | v | 1 | v001 |
| 2 | *(none)* | 5 | 05 |
| 1 | V | 12 | V12 |

### Choice (Dropdown)

A selection from predefined options. Two sources:

- **Custom options (inline)** — define the options directly in the preset, one per line.
- **Linked reusable dropdown** — reference a named dropdown list created in Rename Settings. Updates to the list propagate to all presets that link to it.

### Dynamic

Auto-populated from project/sequence metadata. No user input required.

| Data Source | Example Output |
|-------------|---------------|
| Project Name | `MyProject` |
| Source Name | `A001_C003_0310AE` |
| Frame Rate | `23.976` |
| Duration | `30s`, `1m30s` |
| Date Created | `20260310` |
| Current Date | `2026-03-10` |

**Duration formats**: Auto, Seconds (45s), Minutes (1m30s), Hours (1h30m45s), Frames (1080f)

**Date formats**: YYYYMMDD, YYYY-MM-DD, MMDDYYYY, MMDDYY, DDMMYYYY, DDMMYY

Each dynamic token can override the preset-level default format, or use the global default.

### Separator

A literal character inserted between other tokens.

| Character | Example |
|-----------|---------|
| `_` | `Name_v001` |
| `-` | `Name-v001` |
| `.` | `Name.v001` |
| *(space)* | `Name v001` |

Maximum 3 characters.

---

## Creating a Naming Preset

1. Click **+** in the Presets section of the Rename tab.
2. Enter a **Preset Name**.
3. Use the **Tokens tab** to add tokens:
    - Click **+ Text**, **+ Dynamic**, **+ Counter**, **+ Dropdown**, or **+ Separator**.
    - Configure each token's settings.
    - Drag to reorder (or delete and re-add).
4. Configure the counter in the **Counter tab** (if using a counter token).
5. Optionally override format defaults in the **Settings tab**.
6. Click **Save**.

## Editing a Preset

Click the **pencil icon** next to the preset dropdown. The same editor opens with the current configuration.

## Duplicating a Preset

In the preset editor (edit mode), click **Duplicate** in the footer. A copy is created with a modified name.

## Deleting a Preset

In the preset editor, click **Delete** (red button, bottom-left). Confirm in the dialog.

## Built-In Presets

Five presets are provided on first run:

| Name | Format | Example |
|------|--------|---------|
| Standard_HD | Name_Duration_Version | `MyProject_30s_v001` |
| Social_Export | Name-AspectRatio-Platform-Version | `MyProject-16x9-TikTok-01` |
| Client_Delivery | Client_Project_Date_Version | `Nike_MyProject_20260201_v01` |
| Minimal | ProjectNameVersion | `MyProjectv01` |
| Archive_Format | Project_Title_Duration_Version | `Archive_Untitled_30s_v001` |

## Reusable Dropdowns

Reusable dropdowns are named option lists managed in **Rename Settings** (gear icon). They can be linked to choice tokens in any preset.

### Creating a Reusable Dropdown

1. Open Rename Settings (gear icon in the Presets header).
2. Click **+ Add**.
3. Enter a **Label** (e.g., "Client Names") and optional description.
4. Add options one at a time using the text input and **Add** button.
5. Click **Save Option**.

### Linking to a Preset

In the preset editor, expand a choice token and change **Dropdown Source** from "Custom options (inline)" to the name of your reusable dropdown.
