# FCP XML & Output

## FCP XML Generation

When **Generate FCP XML** is enabled, Scrub creates Final Cut Pro XML files suitable for import into DaVinci Resolve, Baselight, or other color grading applications.

### What's in the XML

The generated XML contains:

- A timeline matching the conform sequence
- References to the exported media files (not the originals)
- Timecodes matching the source clips
- Frame rate and resolution matching the source sequence

### Single Group vs. Multi-Group

| Scenario | Result |
|----------|--------|
| All clips share the same fps and resolution | One XML file |
| Clips have different fps or resolutions | One XML file per group |

When clip grouping splits clips into multiple groups, each group gets its own:

- Conform sequence (e.g., `A001_CONFORM_24fps`, `A001_CONFORM_30fps`)
- FCP XML file
- Set of exported clips

### Importing into DaVinci Resolve

1. Open DaVinci Resolve.
2. Go to **File → Import → Timeline** (or drag the XML into the Media Pool).
3. Select the generated `.xml` file.
4. Resolve creates a timeline with the exported clips at their correct positions.

---

## Output Folder Structure

The output folder is built from the **Output Base Path** plus the **Folder Structure** segments configured in the Settings modal.

### Default Structure Example

```
D:\Projects\                     ← Output Base Path
  └── 07_Color\                  ← Static folder
      └── to Color\              ← Static folder
          └── 031026\            ← Dated folder (MMDDYY)
              ├── A001_CONFORM.xml
              ├── A001_001.mov
              ├── A001_002.mov
              └── ...
```

### Customizing the Structure

In the Settings modal, build your folder hierarchy:

- **Static folders** — fixed names like "07_Color", "Dailies", "Exports"
- **Dated folders** — auto-named from the current date with format options: DDMM, DDMMYY, DDMMYYYY, MMDD, MMDDYY, MMDDYYYY, YYMMDD, YYYYMMDD

A live preview at the bottom shows the full computed path.

## Completion

After the pipeline finishes, Step 4 shows a summary:

| Field | Description |
|-------|-------------|
| Sequence Name | Name of the created conform sequence |
| Total Clips | Number of clips processed |
| R3D Clips | Number of R3D clips exported via REDLINE |
| Other Clips | Number of non-R3D clips exported |
| Clip Groups | Number of distinct fps/resolution groups |
| XML File | Full path to the generated FCP XML |
| Output Folder | Full path to the output directory |

Any **warnings** (non-fatal issues) and **errors** (failures that didn't prevent completion) are shown in dismissible banners.

Click **Start New** to reset all state for a fresh conform run, or **Back** to review the clip list.
