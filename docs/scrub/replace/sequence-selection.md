# Sequence Selection

**Step 2** of the Replace wizard. Choose which sequences the replacement will apply to.

## Scope Options

### All Sequences

Replaces in **every sequence** in the project. No further selection needed — click Next to proceed.

### Selected Sequences

Replaces only in sequences **you specify**. A selection panel appears:

1. Select one or more sequences in the Premiere Pro Project Panel.
2. Click the **+** button.
3. The sequences are added to the list.

Each sequence shows its name and a red **×** button to remove it.

!!! warning
    If you select non-sequence items (bins, media files), an error message appears: *"Selected item(s) are not sequences. Select sequences in Project Panel."*

## What to Replace

Below the scope options, a **What to replace** control picks which halves of a clip get swapped. This gates the scan — only the chosen halves are matched and replaced.

| Option | Behavior |
|--------|----------|
| **Video + audio** *(default)* | Replace both the picture and its linked audio. |
| **Video only** | Replace only the picture; keep the original audio. |
| **Audio only** | Replace only the audio; keep the original picture. |

!!! info "Linked clips are split"
    For a linked A/V clip, Scrub processes the video and audio as **separate instances** (see [Execution Modes → Linked A/V](execution-modes.md#linked-av-clips)). The **What to replace** setting decides which of those instances are included.

## Validation

- **All Sequences**: always valid — you can proceed immediately.
- **Selected Sequences**: at least one sequence must be added before the Next button is enabled.

## State Persistence

Your scope selection and chosen sequences are saved in the store. If you navigate away from the Replace module and return, your choices are preserved.
