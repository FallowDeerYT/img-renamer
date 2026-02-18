# IMG Renamer

A Windows desktop app to rename photos and videos using **date + location** metadata — with a **preview-first** workflow, configurable rules, conflict handling, undo and CSV logs.

## Download

- **Installer (recommended):** download from the latest release assets  
- **Portable ZIP:** unzip and run the executable

You can also use the project website (GitHub Pages) for direct download links.

## Features

- Preview-first: scan and review renames before applying
- Date extraction:
  - Photos: EXIF (DateTimeOriginal / Digitized)
  - Videos **(beta):** ffprobe creation_time (fallback to file modified date)
- Location extraction:
  - Photos: GPS → reverse geocoding to an address
- Rules matrix: configure action based on Date/Location availability
- Conflict strategy: skip / add _1 / overwrite
- Max filename length + sanitization
- Uniqueness tag:
  - Use last 4 digits if available
  - Otherwise generate a 5-digit code (duplicate-safe)
- Undo last run + CSV log export
- Light/Dark theme + EN/NL language

## How it works (high level)

1. Select a folder and file types
2. Scan to build a rename plan
3. Review the plan (preview)
4. Run to rename (or enable dry-run if available)
5. Logs are written to `.img_renamer_logs` in the selected folder

## FAQ

### Why does antivirus/SmartScreen sometimes warn?
This is common for new or unsigned Windows executables/installers. Some security tools use reputation-based detection: files that are new and not widely downloaded may be flagged.
**Only download from the official GitHub Releases page.** Code signing typically reduces these warnings.

### Does the app upload my files?
No. Scanning and renaming happens locally. Reverse geocoding may call an online service to convert GPS coordinates to an address.

### Why do some files have no date/location?
Not all media contains EXIF/GPS metadata. Videos often miss creation_time metadata (e.g., forwarded or downloaded files).
