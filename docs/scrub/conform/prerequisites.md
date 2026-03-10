# Prerequisites

The Conform module's export engines rely on two third-party tools that must be installed separately. Neither is included with Scrub or Adobe Premiere Pro.

| Tool | Required For | Free? |
|------|-------------|-------|
| **FFmpeg** | Trimming non-R3D clips | Yes — open source |
| **REDCINE-X PRO** (REDline) | Exporting R3D (RED camera RAW) clips | Yes — requires RED account |

If you only use Adobe Media Encoder for exports, neither tool is required.

---

## FFmpeg

FFmpeg is a free, open-source media tool used by Scrub to trim clips with frame-accurate precision. It must be installed and accessible on your system before using the FFmpeg engine.

### Install on macOS

The recommended method is [Homebrew](https://brew.sh). If you don't have Homebrew installed, install it first:

```bash
/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"
```

Then install FFmpeg:

```bash
brew install ffmpeg
```

Homebrew installs the binary to `/usr/local/bin/ffmpeg` (Intel) or `/opt/homebrew/bin/ffmpeg` (Apple Silicon). Scrub auto-detects `/usr/local/bin/ffmpeg` — if you're on Apple Silicon, use **Browse** in the Conform settings to point to the correct path.

**Verify the installation:**

```bash
ffmpeg -version
```

You should see version info starting with `ffmpeg version 7.x...`.

#### macOS Gatekeeper Warning

macOS may block FFmpeg when Scrub tries to call it from the command line, even if you can run it yourself in Terminal. This happens when the binary carries a quarantine flag from the download.

**Fix — run this once in Terminal:**

```bash
# Intel Mac (Homebrew default)
xattr -d com.apple.quarantine /usr/local/bin/ffmpeg

# Apple Silicon (Homebrew default)
xattr -d com.apple.quarantine /opt/homebrew/bin/ffmpeg
```

If you installed FFmpeg manually to a different location, replace the path with wherever your `ffmpeg` binary lives. You can find it with:

```bash
which ffmpeg
```

Then run:

```bash
xattr -d com.apple.quarantine $(which ffmpeg)
```

!!! note
    FFmpeg installed via Homebrew usually doesn't need this — Homebrew strips the quarantine flag automatically. You're most likely to hit this if you downloaded a pre-built binary from ffmpeg.org manually.

---

### Install on Windows

**Option 1 — winget (built into Windows 10/11, recommended):**

Open **Terminal** or **PowerShell** as Administrator and run:

```powershell
winget install Gyan.FFmpeg
```

This installs FFmpeg and adds it to your PATH automatically.

**Option 2 — Chocolatey:**

If you have [Chocolatey](https://chocolatey.org) installed:

```powershell
choco install ffmpeg
```

**Option 3 — Manual install:**

1. Download the latest build from [ffmpeg.org/download.html](https://ffmpeg.org/download.html) (choose the Windows release from **gyan.dev** or **BtbN**)
2. Extract the zip to `C:\ffmpeg`
3. The binary should be at `C:\ffmpeg\bin\ffmpeg.exe` — this is where Scrub auto-detects it

Optionally, add `C:\ffmpeg\bin` to your system PATH so you can run `ffmpeg` from any terminal.

**Verify the installation:**

```powershell
ffmpeg -version
```

---

### After Installing

In Scrub's Conform settings, click **Auto** next to the FFmpeg path field. Scrub will scan the default locations and fill in the path if found. If auto-detection fails, click **Browse** and navigate to the `ffmpeg` (macOS) or `ffmpeg.exe` (Windows) binary manually.

---

## REDCINE-X PRO (REDline)

REDCINE-X PRO is RED's official post-production application for R3D (RED camera RAW) footage. It includes **REDline**, a command-line tool that Scrub uses to debayer and export R3D clips.

!!! note
    REDCINE-X PRO is only required if your project contains `.R3D` files from RED cameras. If you're not working with RED footage, you can skip this entirely.

### Download

REDCINE-X PRO must be downloaded directly from RED's website. A free RED account is required.

1. Go to [red.com/downloads](https://www.red.com/downloads)
2. Sign in or create a free RED account
3. Download **REDCINE-X PRO** for your platform

There is no package manager installation for REDCINE-X PRO — the installer from RED's site is the only method.

---

### Install on macOS

1. Open the downloaded `.dmg` file
2. Drag **REDCINE-X PRO** to your Applications folder
3. Launch it once to accept the license agreement

REDline will be located at:

```
/Applications/REDCINE-X Professional/REDCINE-X PRO.app/Contents/MacOS/REDline
```

**Verify REDline is accessible:**

```bash
"/Applications/REDCINE-X Professional/REDCINE-X PRO.app/Contents/MacOS/REDline" --version
```

#### macOS Gatekeeper Warning

Even if REDCINE-X PRO opens fine, macOS may still block the **REDline binary** when Scrub tries to call it from the command line. This is a separate Gatekeeper restriction — the app and its internal binaries each carry their own quarantine flag.

**Fix — run this once in Terminal:**

```bash
xattr -dr com.apple.quarantine "/Applications/REDCINE-X Professional/REDCINE-X PRO.app"
```

The `-dr` flags recursively remove the quarantine attribute from the entire app bundle, including REDline. After running this, Scrub can call REDline without macOS blocking it.

If you're unsure of the install path, you can find it with:

```bash
find /Applications -name "REDline" 2>/dev/null
```

Then substitute that path into the `xattr` command above.

!!! note
    If REDCINE-X PRO itself was also blocked when you first opened it, you may need to allow it in **System Settings → Privacy & Security → Allow Anyway** before the `xattr` command will fully take effect.

---

### Install on Windows

1. Run the downloaded installer
2. Follow the on-screen prompts (default install location is fine)

REDline will be located at:

```
C:\Program Files\REDCINE-X PRO 64-bit\Redline.exe
```

**Verify REDline is accessible:**

```powershell
& "C:\Program Files\REDCINE-X PRO 64-bit\Redline.exe" --version
```

---

### After Installing

In Scrub's Conform settings, click **Auto** next to the REDLINE path field. Scrub checks all standard install locations automatically. If not found, click **Browse** and navigate to `REDline` (macOS) or `Redline.exe` (Windows) inside your REDCINE-X PRO installation.

---

## Quick Reference

| Tool | macOS Default Path | Windows Default Path |
|------|--------------------|----------------------|
| **FFmpeg** | `/usr/local/bin/ffmpeg` | `C:\ffmpeg\bin\ffmpeg.exe` |
| **REDline** | `/Applications/REDCINE-X Professional/REDCINE-X PRO.app/Contents/MacOS/REDline` | `C:\Program Files\REDCINE-X PRO 64-bit\Redline.exe` |

Both paths are where Scrub's **Auto** detection looks first. If your install is in a non-standard location, use **Browse** to set the path manually — Scrub saves it and remembers it between sessions.
