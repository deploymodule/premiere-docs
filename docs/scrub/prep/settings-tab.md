# Settings Tab

The **Settings** tab batch-applies **sequence settings** to multiple sequences at once. Pick the sequences you want to change, enable only the fields you care about, and Scrub writes those settings to every target in a single undoable step — then reads each one back so you can confirm exactly what stuck.

Like the Trim tab, it operates directly on the current project and does not use templates or naming presets.

!!! info "Requires Premiere Pro 25.0 or newer"
    Writing sequence settings relies on API setters that only exist in Premiere Pro 25.0+. On older hosts the affected fields are reported as **not supported by API** in the results and left unchanged.

---

## Target sequences

The top section is the list of sequences the changes will apply to. The list **accumulates** — it only ever grows from selection, so you can build it up across several Project-panel selections without losing earlier picks.

| Action | What it does |
|--------|--------------|
| **Select in Project panel** | Any sequences you select are added to the list automatically (deduplicated). |
| **+** | Manually add whatever is currently selected in the Project panel. |
| **×** (per row) | Remove a single sequence from the list. |
| **Clear** | Empty the entire list. |

The list survives tab switches, so you can set it up, jump to another tab, and come back to it. Selecting other items in the Project panel never *removes* entries — use **×** or **Clear** for that.

---

## Settings to apply

Enable only the fields you want to change. Every field has a checkbox; **disabled fields are left completely untouched** on the target sequences. Each enabled field has a value control next to it.

| Field | Type | Notes |
|-------|------|-------|
| **Frame width** | Number | Horizontal frame size in pixels |
| **Frame height** | Number | Vertical frame size in pixels |
| **Audio sample rate** | Dropdown | 32 kHz · 44.1 kHz · 48 kHz · 96 kHz |
| **Preview width** | Number | Preview (render) frame width in pixels |
| **Preview height** | Number | Preview (render) frame height in pixels |
| **Maximum bit depth** | On/Off | Toggles the sequence's "Maximum Bit Depth" render flag |
| **Maximum render quality** | On/Off | Toggles the sequence's "Maximum Render Quality" render flag |

!!! note "Why frame rate isn't here"
    A sequence's **frame rate (timebase) is fixed at creation** and the API provides no setter for it, so it can't be batch-changed. **Display format**, **preview file format**, and **preview codec** are also omitted — they're writable but use opaque numeric/string codes with no selectable option list, so there's no safe UI for them.

---

## How to use it

1. Select one or more sequences in the **Project panel** (they appear in the **Target sequences** list), or click **+** to add the current selection.
2. In **Settings to apply**, tick the checkbox for each field you want to change and set its value.
3. Click **Apply to N sequences**.

Scrub mutates each sequence's settings, commits all of them in **one transaction**, then reads each sequence back to verify. A **Cancel** button appears while the operation is running.

!!! tip "One undo for the whole batch"
    All target sequences are committed in a single transaction, so a single **Undo** (Ctrl/Cmd+Z) reverts the entire batch at once.

---

## Results report

After applying, a report appears below the fields showing what happened per sequence and per field:

- **✓** — the value was written *and* the read-back matched what you requested (it stuck).
- **✗** — the change did not stick. The row shows the requested value and what was read back instead (or the error / *not supported by API*).

Each field line reads `req <requested> → got <readback>`, so you can see at a glance whether the host accepted the value. The summary at the top reports how many sequences were processed, and any warnings (for example, a sequence that couldn't be read, or a transaction that wasn't committed) are listed at the bottom.
