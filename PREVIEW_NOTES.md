AetherTrail v0.9.7 fixes character-profile recovery and collection reporting after world re-entry.

- A saved network character link now restores its missing character-list entry. If no selection was saved and exactly one linked character exists, the app restores that character. Explicit selections and multiple-character ambiguity are preserved.
- Re-entering the world can recover a missing linked profile immediately, select it and refresh existing pet observations. Character selection is saved across restarts.
- Connection status shows when pet data last refreshed and distinguishes pet import from map-completion observations.
- Regional rows resolve explicit category summaries as well as individual records. Confirmed 100% sealed-dungeon completion no longer leaves those native dungeon rows labelled Unknown. Teleport completion summaries are also supported when explicitly confirmed; partial lists never imply full completion.
- Category summaries are shown separately from unrelated unknown collectibles, and summary rows no longer inflate item totals. Evidence sources remain visible. Newer individual missing observations override older complete summaries.
- Repeated screen observations refresh their last-confirmed timestamp at bounded intervals; older observations cannot overwrite newer data.

This retains v0.9.6 layout, ownership sorting, map-highlight and tracking fixes. Npcap imports character identity and supported pet data; this release does not add network decoding of teleport, dungeon, stronghold or feather ownership. Strongholds remain regional completion because the hosted map has no native stronghold completion-marker type. Unseen feathers remain unknown rather than being inferred from another category's 100% summary.

Download **AetherTrail-Setup-x64-v0.9.7-preview.exe**, or choose the built-in update action. Settings and character records are retained. No manual ZIP extraction is required for Setup; the ZIP supports the updater and optional portable use.
