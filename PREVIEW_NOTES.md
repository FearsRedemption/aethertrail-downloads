AetherTrail v0.9.9 improves saved-data safety and everyday usability.

- Reject malformed observation timestamps so unreadable records can be handled through Character data instead of breaking its overview.
- Prevent two copies of this version from using the same data folder at once. Close older versions before launching the update; older builds do not participate in the new lock.
- Remove an update download's own temporary folder if it fails or is cancelled. Previously abandoned folders are retained rather than risking an active updater job.
- Settings → Character data now offers Restore a cleanup backup. Restore requires confirmation, runs on the next launch, refuses unreadable backups and saves affected current data first. Restoring shared files can undo newer progress for other characters; the confirmation explains this. Current preferences, timers, recipes, material counts and calibration remain intact.
- Tables remember column widths, ordering, sorting and header filters. Header menus still let you clear filters and restore ordering.
- Coalesce repeated progress and connection notifications before refreshing the main progress views.

Npcap decoding remains identity and pets only. These changes do not add inventory, collectible-ownership or continuous-coordinate decoding.

Download **AetherTrail-Setup-x64-v0.9.9-preview.exe**. Setup and the built-in updater retain saved user data. No GitHub Actions build was used.
