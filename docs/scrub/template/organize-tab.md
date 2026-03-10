# Organize Tab

The Organize tab provides four project cleanup tools.

## Mirror Folder Structure

Recreates the source file paths of selected items as bin hierarchies inside a new `REORG_<timestamp>` bin.

**How it works:**

1. Select items in the Project Panel.
2. Click **Mirror Selected Items**.
3. Scrub reads the source file path of each item and builds matching folder hierarchies inside a new bin.
4. Items are moved into their corresponding folders.

**Use case:** Re-organize imported footage to match the original folder structure on disk.

---

## Organize By Date Created

Sorts selected media items into date-based bins.

**Settings:**

| Field | Description |
|-------|-------------|
| **Base Bin Name** | Parent bin for the date folders. Leave empty to use project root. |
| **Date Structure** | Format for the date folder names (8 options: DDMM through YYYYMMDD). |

**How it works:**

1. Select items in the Project Panel.
2. Set the base bin name and date format.
3. Click **Organize Selected**.
4. Scrub reads each item's creation date (from XMP metadata or file metadata) and moves it into a date-named bin.

**Example:** With base bin "Footage" and format YYYYMMDD:

```
Footage/
  ├── 20260301/
  │   ├── A001.mov
  │   └── A002.mov
  └── 20260305/
      └── B001.mov
```

---

## Move Unused to \_Not\_Used

Scans all sequences to identify used media, then moves everything else into a `_Not_Used` bin at the project root.

**How it works:**

1. Click **Move Unused**.
2. A progress bar shows the scan progress.
3. Scrub builds a set of all project items referenced in any sequence.
4. Items not in that set are moved to `_Not_Used`.

**Use case:** Clean up projects with large amounts of imported but unused footage.

!!! tip
    Run this after picture lock to identify footage that was imported but never used in any sequence.

---

## Delete Empty Bins

Scans the entire project and removes all bins that contain no items.

**How it works:**

1. Click **Delete Empty Bins**.
2. Scrub scans all bins in the project.
3. Empty bins are removed.

**Use case:** Clean up after reorganizing or removing footage, which often leaves behind empty folder structures.
