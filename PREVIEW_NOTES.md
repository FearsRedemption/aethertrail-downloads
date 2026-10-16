AetherTrail v0.9.6 improves collection persistence, location following and wide-window layouts.

- Pets and Materials expand across the available workspace to show more cards. Pet model/details and material-family panes remain adjustable.
- Pets default to Owned, then Missing, then Unknown, alphabetically within each group. Selection and ownership artwork remain intact.
- Automatic area following frames the detected location without clicking a search result or highlighting the entire area yellow. Camera-only URL changes no longer discard world tracking or area focus. Inner-area zoom and supported dungeon route switching remain available.
- Map progress waits for the hosted collection layer to be ready and retries after loading or changing regions. Saved positive screen completions restore for the selected character and region.
- Teleport/Kibelisk lists continue syncing without a reliable terrain match. Confirmed rows are saved even when the map marker is already checked; later observations can update earlier states.
- Older saved teleport sync records are recovered only when character, marker ID and name match a unique cached regional entry.
- Saved explicit 100% Sealed Dungeon summaries restore native sealed markers without requiring translated names to match. Newer explicit missing observations take precedence. Stronghold summaries remain regional progress because the hosted map has no native stronghold completion-marker type.

Collection reading is continuous while location reading runs; only visible, confidently read states are imported. Npcap currently decodes character identity and pets, not teleport/dungeon/stronghold completion. This release does not claim a new network collection decoder or infer completion from disappearing icons. Existing v0.9.5 crafting entry, Closet mixing and pet 3D previews are retained.

Download **AetherTrail-Setup-x64-v0.9.6-preview.exe** for a normal installation. Existing users can choose the built-in update action. Settings and character data are retained. The ZIP is provided for the updater and optional portable use; manual extraction is not required for Setup.
