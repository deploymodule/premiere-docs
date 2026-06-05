# Privacy Policy

_Last updated: 2026-06-04_

Scrub is a workflow plugin that runs entirely on your local machine inside Adobe Premiere Pro. This policy describes what Scrub does and does not do with your data.

## Data Scrub does not collect

!!! success "Nothing leaves your machine"
    Scrub does **not** transmit any of the following off your computer.

- Project files, sequences, clips, or any media.
- Filesystem paths, folder structures, or user-chosen output locations.
- Plugin settings, preset configurations, or naming token values.
- Adobe IDs, user identifiers, or session information.
- Telemetry, crash reports, or usage analytics.
- IP address, location, or device information.

Scrub does not connect to any remote server during normal operation.

## Data Scrub stores locally

Scrub persists the following data on your machine to support its features. All of this stays on your computer:

- **User settings** — preferences, preset folders, naming tokens. Stored in UXP's local storage area.
- **Folder authorization tokens** — UXP-provided persistent tokens that let the plugin re-access folders you have explicitly authorized via Premiere's folder-picker. The token does not grant access to any other folder.
- **Build identifier** — a non-identifying string written by the build process, used for diagnostic reporting if you choose to file a bug.

You can delete all locally stored Scrub data by removing the plugin from Premiere Pro's Plugin Manager.

## External processes Scrub may launch

When you use the **Conform** module with R3D footage, Scrub launches two external tools from paths you have configured in plugin settings:

- **REDCINE-X PRO** (`redline`) — to render R3D intermediates.
- **FFmpeg** — to convert intermediates as part of the conform pipeline.

These tools are not bundled with Scrub. Scrub passes them arguments constructed from your project state and the file paths you have authorized. Whatever those tools do with the data is governed by their own respective policies.

## Adobe Premiere Pro's role

Scrub runs inside Adobe Premiere Pro and uses Premiere's official UXP API to read and modify your project. Adobe Premiere Pro's own privacy policy applies to anything Premiere itself sends to Adobe. Scrub does not piggy-back on Premiere's network connections.

## Changes to this policy

If this policy materially changes — for example, if a future Scrub version introduces optional telemetry — the change will be documented in the plugin's release notes and a new "Last updated" date will appear at the top of this document. Material changes will never apply retroactively.

## Contact

Privacy questions: [zacsurprenant@gmail.com](mailto:zacsurprenant@gmail.com).
Support and documentation: [Support](support.md).
