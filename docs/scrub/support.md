# Support

## Where to get help

- **Documentation:** you're reading it. Use the search bar at the top, or jump to the [Scrub overview](index.md).
- **Bug reports and feature requests:** email [hello@zacsurprenant.com](mailto:hello@zacsurprenant.com) with the details listed below.
- **Email:** [hello@zacsurprenant.com](mailto:hello@zacsurprenant.com).

Average response time: within 3 business days.

## Before reporting a bug

To save a round-trip, please include:

1. **Premiere Pro version** — _Help → About Premiere Pro_.
2. **Operating system** — Windows or macOS, and the version.
3. **Scrub version** — visible at the bottom of Scrub's Settings panel.
4. **Module affected** — Deliverables, Replace, Conform, or Prep.
5. **Steps to reproduce.**
6. **Console output** — open UXP Developer Tool → your plugin → Console, then reproduce the bug and copy the relevant lines.

If the bug involves Conform, include the redline binary path and FFmpeg path you have configured. If it involves Replace, include whether the source media paths are local or on a mounted share.

## Common issues

### "No active sequence" error

Scrub follows Premiere's active sequence. If nothing is open in the Timeline panel, most modules will refuse to run. Open a sequence and click inside the Timeline to make it active.

### Output folder permission revoked

Premiere will occasionally invalidate authorization tokens after a Premiere restart or system update. Re-pick the output folder in the module settings to re-authorize.

### Redline / FFmpeg not found

Conform requires both tools. Open _Settings → Conform_ and set the binary paths. On macOS, ensure the launchers have execute permission:

```bash
chmod +x /path/to/RedlineLauncher.command
chmod +x /path/to/FFmpegLauncher.command
```

### Language is wrong

By default Scrub follows Premiere's UI language. To override, open _Settings → Language_ and pick a specific locale.

## Compatibility

| Component             | Minimum             | Notes                                          |
| --------------------- | ------------------- | ---------------------------------------------- |
| Premiere Pro          | 25.1 (Nov 2024)     | UXP host requirement.                          |
| macOS                 | 12 Monterey         | Matches Premiere Pro's own minimum.            |
| Windows               | 11 22H2             | Matches Premiere Pro's own minimum.            |
| Adobe Media Encoder   | 25.0                | Required for the Deliverables module.          |
| REDCINE-X PRO         | Recent              | For R3D conform only.                          |
| FFmpeg                | 6.0+                | For conform pipeline only. Static builds work. |

## Refunds and licensing

Scrub is a paid plugin sold through the Adobe Marketplace. Licensing, billing, and refunds are handled by Adobe per their marketplace policy. Open _Adobe Exchange → My Subscriptions_ to manage your license or request a refund within Adobe's refund window.

## Privacy

See the [Privacy Policy](privacy.md) for what Scrub does and does not do with your data.
