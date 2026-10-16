# AetherTrail preview testing

Download: https://github.com/FearsRedemption/aethertrail-downloads/releases

Recommended download: **AetherTrail-Setup-x64-v0.9.7-preview.exe**. Close the old app and run Setup; no manual ZIP extraction is required. Setup installs the complete runtime and shortcuts and offers to launch AetherTrail. Keep saved settings and character data in AppData when refreshing old program files. The ZIP is retained for the built-in updater and optional portable use. Windows 10/11 x64; no Python or IDE is needed. The app opens maximized. Internet is required for the hosted map; OCR runs locally.

Navigation keeps its controls together and wraps them when larger text needs more room. Character progress and Tracking setup and help are in Map tools. The capture helper is built into Aethertrail; Npcap is a separate driver, linked from Settings → Connection. No Wireshark/helper app needs to run. Npcap is not needed for screen area reading. Continuous network player position remains unverified and disabled.

The map site's first-run faction prompt lets you choose your side or “Not sure yet? Just show me the map”. Click **Start location reading** and choose your game monitor. Drag around minimap terrain first, then only the current-location title above it. Cancel leaves reading stopped. Click Capture screenshot, switch to Aion during the three-second countdown, then return. Capture runs in a separate helper with a timeout and no game input. Thin title strips are accepted; selection errors appear inline and Cancel remains available. The title selects regions and supported dungeon routes after repeated confident readings; dungeon entrance labels inside the terrain are excluded. Unknown titles keep the current map. Stop keeps saved setup; starting again reuses it. Reselect after moving or resizing the game. Browsing away pauses Follow detected area; check it to return to the detected location. Reload, Open in browser and advanced location setup are under Map tools. If Navigation flashes, select Compatibility (OpenGL) in Settings and restart.

## Self-tests

The daily rail has Navigation, Crafting, Timers and Checklists; Settings holds display, alert sounds, Updates and advanced tools. Crafting combines Recipes, Items, Plans and Materials. Search is always available; catalog filters expand on demand. Select a verified artwork row to see ingredients or crafting uses. Related links stay in Crafting and provide Back navigation. Add a recipe to My plans, choose crafts, and edit owned quantities directly in ingredient rows. Counts are shared with Materials, remain manual and are not consumed automatically. The offline catalog covers crafting items, not every game item.

Timers prioritizes running countdowns. New countdowns and saved observations use focused forms; each timer has Start / Pause and an options menu for reset/edit/remove. Known timers retains source-labelled Global schedules and requires your actual server UTC offset. Checklists supports group and completion filters, visible completed tasks and manual group resets. Settings has Display, Sounds, Updates, Connection, Location and Advanced pages. A glowing dot on Settings means a release is ready; clicking Settings opens Updates. Choose Download update & restart when convenient. The app verifies and installs the download, then relaunches; background checks never close or restart the app or show a tray popup; a new-version chime is configurable in Sounds. Existing experimental tracking and character progress retain their stated limitations.

Close the game and leave the Windows desktop available while running the self-tests. They open temporary application/label windows and close them automatically. They use isolated settings, and the area test captures its own generated label window; it does not automate the game.

On a locked computer, run `Test-Aethertrail.ps1 -SkipScreenCapture` to omit the desktop capture/OCR case. Full capture testing requires an unlocked interactive desktop.

From PowerShell in the extracted folder:

```powershell
powershell -NoProfile -File .\Test-Aethertrail.ps1
# Only the offline UI/simulation check:
powershell -NoProfile -File .\Test-Aethertrail.ps1 -OfflineOnly
```

If your PowerShell policy prevents unsigned scripts, run the equivalent commands directly:

```powershell
$env:AETHERTRAIL_DATA_DIR = Join-Path $env:TEMP 'Aethertrail-SelfTest'
.\Aethertrail.exe --smoke-test --report-dir "$env:TEMP\Aethertrail-Reports\offline"
.\Aethertrail.exe --map-smoke-test --report-dir "$env:TEMP\Aethertrail-Reports\map"
.\Aethertrail.exe --area-smoke-test --report-dir "$env:TEMP\Aethertrail-Reports\area"
.\Aethertrail.exe --workspace-smoke-test --report-dir "$env:TEMP\Aethertrail-Reports\workspace"
Remove-Item Env:AETHERTRAIL_DATA_DIR
```

The script also verifies maximized workspaces, tab separation, scaling, timer notifications and manual planning using labeled acceptance fixtures. The script prints the report folder and writes summary.json. Online checks can fail during a website outage. Passing checks establish UI launch, hosted-map rendering and synthetic capture/OCR switching, not live dungeon reliability or a player marker on the hosted map.

## Report a problem

Open an issue at https://github.com/FearsRedemption/aethertrail-downloads/issues with preview version, Windows version, resolution/HUD scale, steps, expected/actual behavior, and relevant JSON report or startup.log. Public issues are visible to everyone: inspect attachments and remove private details. Attach only the location-label crop when diagnosing OCR, not a full desktop screenshot. Actual dungeon labels may need an alias.

## Verify the download

Download SHA256SUMS.txt from the same release. Run `Get-FileHash .\Aethertrail-Windows-x64-v0.8.11-preview.zip -Algorithm SHA256` and compare with the matching line. A checksum detects corruption; it is not a code signature.

The app is unofficial and is not endorsed by NCSOFT or Aion2Maps.com. Exact catalog-linked game item icons are bundled for offline use, with NC Corporation attribution and per-image source/hash records. No website source is bundled. Aethertrail captures configured screen pixels, with no memory reads, injection or gameplay input automation. Source remains private; this public repository hosts test binaries, documentation and issue reports. Third-party notices and library replacement/source information are included under licenses.

Character progress: use Navigation's Character selector and add a separate profile before switching characters. Open the game's Kibelisk list to sync visible completed/incomplete rows. Only visible readable evidence changes progress; scroll the list yourself to expose more points. Initial calibrated local terrain references and private visual templates are required for experimental tracking/icon sync and are not shipped with this download. Relative terrain tracking expires after 20 seconds without a map match. See release notes for verified behavior and remaining gameplay checks.

Game connection: Settings defaults to Auto. Installed usable Npcap starts game-owned passive traffic observation when one AION 2 client is running. Off persists and Pause lasts for the launch. No driver is bundled or installed. This release provides diagnostics, a bounded local recorder and Global Steam identity/login pet observations. Live pet updates, claim eligibility and map position remain unavailable. Existing screen/manual features remain available. Recordings can contain private chat/character/session data and are never uploaded automatically.

## Login diagnostic recording (v0.8.2)

Settings -> Connection -> Record 60-second game diagnostic. Recordings now follow socket changes for the same single AION 2 process, so you can return to character selection and enter the same character while recording. The time/size limit is preserved. Recording ends on game exit, process replacement or multiple game instances. Files stay private; only validated Global Steam identity/login pet observations are available. Endpoint discovery can miss the earliest traffic of a new socket.

## Automatic login pet progress (v0.8.9)

With Auto enabled, the Global Steam client sends your identity and pet list when you enter the world. After starting this version, return to character selection and enter the same character. The app automatically creates/selects a separate character profile; then open Pets. Restarting only AetherTrail while already in the world does not replay login data. Ownership, levels and explicit soul points appear with readable names and search/filter controls. Values reflect the last login; relog to refresh them. Missing fields stay unknown. Live soul gains, claim eligibility, feathers and map position remain unavailable. Other client distributions continue connection diagnostics without this decoder. Raw diagnostics remain private.

## Pets and regional progress

**Pets** is a dedicated sidebar page. Search the 207 reference pet names, filter confirmed or unknown ownership, and read the last login's level and soul points. Reference names alone do not establish that a pet is missing or ready to claim.

**Regions** opens Regional Progress. Choose a map on Navigation first, then open Regions to read its feathers and Kibelisks. Filter category/state or search by name or marker ID. The checklist refreshes while visible, and previously viewed regions remain selectable during this session. Counts distinguish verified collected, verified missing, unknown and saved map marks. Unmarked map icons remain unknown. Map marks belong to the selected Navigation character profile; this page reads them without changing them. Automatic feather/Kibelisk decoding and full regional completion totals are still pending protocol verification.

## Location capture setup (v0.8.9 and later)

Click Start location reading to choose the game monitor, minimap terrain and current-location title. This is a one-time setup: later starts reuse both saved boxes. Reading resumes after restart if it was running at close; Stop keeps setup and prevents resume. Use Map tools or Settings → Location → Redo minimap and title setup after a layout change. Location reading also starts experimental terrain/visible-progress tracking. Last known regions are restored without treating old positions as live. Off persists.

Fresh title evidence selects regions and supported dungeons; it does not establish precise coordinates. Terrain dots require calibrated local references. Unknown titles and expired frames remove current-location evidence. Exact feather IDs, historical ownership, live pet soul changes and claim eligibility remain unverified.

## UI stability (available since v0.8.6)

Pets and Regions preserve unchanged rows during automatic polls. Location messages stay on one line; hover for the complete message. The hidden map pauses on native pages and resumes for Navigation/Regions without reloading. Compare Navigation, Pets, Regions and Crafting for rapid flashing, especially while the connection/location status changes. The native stress check passed, but the user reported flashing continued with the default renderer.

Existing recordings have not established continuous precise coordinates for your own character. A login placement and other entities' movement are insufficient for a live player dot. Automatic HUD discovery identifies the location strip and minimap crop; absolute terrain position still needs calibration.

## Offline regional review (v0.8.9)

Open Regions to view previously loaded checklists while offline or after restarting. Each checklist and its map marks belong to the selected character profile and region. Visit a region on Navigation to load it the first time; Refresh current map updates its saved snapshot. Unchanged refreshes do not rewrite the cache.

Saved map marks remain Marked, not verified Collected. If a verified linked character has saved positive collection evidence and a validated exact marker reference, offline review labels it Last known verified collection. Stale missing states stay Unknown; partial captures cannot establish full completion. No stable automatic feather IDs have yet been validated, so the supplied recordings do not automatically mark the feathers you gathered. Pet login observations remain saved separately.

Settings -> Display -> Map rendering -> Compatibility (OpenGL) is a saved option for flashing. Restart Aethertrail to apply it. The user confirmed the temporary OpenGL trial stopped the flashing with the map loaded. System default remains available. No Windows graphics settings are changed.

## Location confidence (v0.8.10)

Navigation shows a dot only for a fresh supported position match. Terrain dots require a calibrated reference and strong independent feature evidence. Exact live network position is still unavailable. A known location title can instead highlight the real named subarea outline, or show the broader mapped region when only its name is known. This is area evidence, not a precise position or an accuracy radius.

A lost/expired location shows a red question mark in the map's upper-right area. Only that icon pulses slowly; the app does not flash. Pausing or turning reading Off makes it steady. Evidence older than three seconds is removed, including frames delayed by slow OCR. Switching characters, browsing another region or losing the title cannot retain an old dot. If the map is zoomed away from the matching location, the position label remains available even when the projected dot is off screen.

The position/area/expiry UI passed isolated native fixtures. Real exact-position acceptance still requires verified location evidence; the login/flight recording did not establish continuous self movement.

Startup update prompts are enabled by default. A newer release offers Yes, No, or Disable startup notifications. Yes starts the verified download and restart; No leaves the app open. Disabling this prompt only changes the startup-popup preference; scheduled checks and the Settings dot remain available. Re-enable it in Settings → Updates.


## Screenshot controls and update guidance (v0.8.21)

Use the mouse wheel to zoom a screenshot, hold middle mouse and drag to pan, and left-drag to draw terrain/title boxes. Fit screenshot returns to the full image without clearing boxes. Saved crops remain in original physical pixels, including after zoom/pan and window resizing. A newly found update sends a brief golden sparkle trail down the sidebar toward Settings; opening Settings stops the trail and preserves the update dot. Checks never install automatically.

## Automatic character and map setup (v0.8.21)

Keep AetherTrail open on Connection → Auto, return to AION character selection and enter the desired character to receive identity and supported pet data. The app automatically creates/selects a separate profile. Restarting the companion alone cannot replay a login snapshot. Connection, Pets and Regions explain this step. Advanced packet recording/reference imports are troubleshooting tools, not normal setup.

Verified completion evidence syncs to the linked character’s Navigation map. Existing screen-based teleport/icon sync starts with location reading and still needs calibrated visual references. Network collectible completion remains unavailable; login pets do not establish map completion. Cached positive network marks can be restored for that same linked character when an exact verified mapping exists, while old absence cannot clear newer progress.

## Sound choices and pet readability (v0.8.21)

Settings → Sounds contains four original bundled chimes, separate update/reminder choices and enable switches, volume, Preview and Mute all app sounds. New-version discovery chimes once; duplicate checks remain quiet across restarts. Nearby timer expirations coalesce sound playback. Audio failure leaves visual alerts available without a Windows error beep fallback. Settings persist.

Pets shows separate ownership, level/souls and last-observed columns, with a selected-row detail summary. Unknown stays unknown. This table layout was replaced by the v0.9.0 portrait gallery and Closet browser described below.

Collection coverage in v0.8.21 was limited to supported teleport/feather screen evidence. v0.9.0 adds Exploration summaries as described below.

## Pets, Closet and exploration completion (v0.9.0)

Pets shows 207 original game portraits, observed ownership, level and soul points. Select a card for soul requirements, named soul sources, known source locations and its reference link. The catalog is browsable offline before connecting. Unknown stays unknown. Leave Connection on Auto, return to character selection and enter your character once to receive login observations; relog to refresh them. Mount eligibility is not separately verified.

Closet contains Armor, Weapons and Decoration collections from 1,463 Global-client appearances. Search by set or piece name; select a collection to view its full-set appearance and inspect individual pieces and unlock items/source links. Armor entries distinguish game SkinSet membership from browsing name families. Obtained, Missing and Unknown are manual appearance notes saved separately for each selected character. The app does not infer Closet unlocks from inventory, equipped gear or pet packets. The renderer is bundled; full-set model files download from AetherTrail and are cached. Some icons and acquisition routes are unavailable; a listed unlock item does not establish a dungeon drop location.

Start location reading, then open AION’s full map → Exploration. Repeated, confident **100%** Sealed Dungeon summaries mark the current region’s native sealed-dungeon markers, including older completions. Explicit **0%** clears that category for the selected character; partial percentages alone do not identify which individual dungeons remain. Repeated, clearly checkmarked named rows can sync older completions as you scroll; blank rows stay unknown. This summary reading works without a matched terrain reference. Stronghold 100%/0% is saved as regional completion and displayed above Navigation and in Regions, because the hosted map has no native stronghold checklist marker type. Scanning stays on the remembered game monitor.

Visible supported icon evidence remains available with aligned terrain references. Screen observations are saved per character and region, separate from manual map marks. Opening another character’s map does not transfer these observations. A hidden or disappearing dungeon icon never proves completion. Network collectible decoding remains unavailable; pet imports alone cannot mark a map.

Settings → Sounds contains four original bundled chimes, separate update/reminder choices and enable switches, volume, Preview and Mute all app sounds. New-version discovery chimes once; duplicate checks remain quiet across restarts. Nearby timer expirations coalesce playback. Audio failure leaves visual alerts available without a Windows error beep fallback. Checks notify; installation is your choice.

## v0.9.2 appearance checks

In Closet, select a full Armor set, choose Male and Female, and confirm the character appearance changes. Drag to rotate, scroll to zoom, right-drag to pan and use Reset view. Inspecting a piece must keep the full model in view. The game base body is a reference, not the player's customized character. Model files download only from the AetherTrail downloads repository and then use a verified cache. All 119 full sets have both variants; other individual appearance families may not have models. Confirm Missing and Unknown pets are grayscale in both the gallery and large preview, with only Owned pets in color.

### Mix armor pieces
Choose an Armor collection to show its entire set. Change an individual Helm, Pauldrons, Top, Gloves, Legs, Shoes or Cloak field to replace that slot on the model. Type part of a name for suggestions, or click Browse beside the slot for a searchable image picker. Choosing a collection again restores the complete set and resets the mixed preview. Male/Female changes the complete outfit. The preview does not change equipped gear or ownership. Only pieces with separate geometry in both body models are offered. Some combinations may clip.

### Table headers
Drag the divider between table headers to resize columns; drag a header to reorder columns. Double-click a divider to fit its contents. Use Ctrl+C to copy selected cells as tab-separated text for Excel. Click any header (or right-click it) for ascending/descending sort, text and value filters, clearing filters, and fitting widths to contents. Filters combine across columns. Select none hides all values; Select all restores them. Table actions and editable counts continue to address the correct records after sorting. Catalog list/card views retain their existing search and category controls.

### Connection data limits
Npcap supplies packet capture, not decoded inventory or position data. Character identity and pet observations are supported. Inventory, personal/account storage totals and continuous player coordinates are not yet validated by the game decoder. Crafting quantities remain manual; opening a storage does not currently import it. The map can consume verified network positions when a decoder and map calibration become available; current screen-based positioning remains the available fallback.

### Material grid and batch entry
Open Crafting → Materials. With the default All ingredients view and an empty search, the grid shows every available crafting material in the bundled catalog, plus saved custom materials and plan ingredients. Cards are ordered by family and grade: Orichalcum Ore, Fine, Pure, Radiant and Ingot stay together, followed by Odyle and other families. Search filters card names and families immediately; searching Fine Odyle shows that grade, while Odyle shows its related types. Clear the search to show the full current view again.

Choose a family on the left to narrow the grid. Gathering & refining shows core gathered/refined resources and retains your tracked counts and plan ingredients. All tracked, Owned, Zero stock and Used in saved plans provide focused views; other pages' table header controls do not apply to this card grid.

Type your available total directly in a card's Owned field. Tab saves and moves to the next quantity; Shift+Tab moves back and Enter saves. Counts immediately update crafting readiness and save through the normal settings workflow. Looking at or tabbing past an untouched field does not create a count. Not entered is separate from an explicit zero: type 0 to record that you have none. Forget selected count removes only the saved quantity; the catalog card remains available. Add custom material handles names outside the catalog.

Inventory and storage still require manual totals. No scan or automatic game import is implied by the catalog cards.

### Workspace sizing
Search inputs and forms have bounded widths on large windows, and utility workspaces keep a readable content width. The map and Closet keep their larger visual workspaces. Text scaling remains available in Settings → Display; material columns adjust for the chosen scale.


### Pet and mount 3D previews
Select a pet in Pets to view its creature model. Drag to rotate, scroll to zoom, and use Reset view to center it. Verified models are available for 197 of the 207 catalog pets; the others keep their portrait. Load 3D retries a failed download. The app downloads only the selected model from AetherTrail’s public repository, checks its checksum, and renders it locally. Unknown and Missing pets stay grayscale until ownership is observed. These models use the creature’s rest pose: a separate small-pet form or mounted rider is not available. The preview does not establish a separate mount unlock.


## v0.9.6 collection and layout checks

Resize Pets and Materials: cards should use the extra width while the side panes stay adjustable. Pets should list observed Owned, Missing and Unknown groups in that order and preserve the selected pet.

With location reading running, the game teleport binding list should continue syncing without a terrain match. Repeated confirmed rows save even if the companion marker already has a check. Change region or reload Navigation: saved positive observations should return after the hosted collection layer becomes ready. A 100% Sealed Dungeon summary restores native sealed markers; newer explicit missing observations remain protected. Stronghold completion is regional because the hosted map lacks native completion markers for it. Each character uses separate evidence.

Area following should frame the detected geographic location without typing into search, clicking a result or turning the whole area yellow. Existing dungeon entry/exit routing and minimap configuration persistence should remain intact. These are screen-evidence checks; Npcap collectible decoding is not newly supported.


## v0.9.7 character refresh checks

With a valid saved network link but a missing settings character-list entry, reopen the app: the linked profile should be recovered. With one saved character and no saved selection it should be selected; multiple characters should not select an arbitrary profile. Re-entering the world must select the exact linked character and update existing pet timestamps/details. Restart and verify that selection remains saved.

In Regions, a confirmed 100% sealed-dungeon summary should resolve native sealed entries as Collected without requiring name matches. An unrelated feather should remain Unknown. Later individual Missing observations override older summaries. Summary rows must not inflate collectible counts. Connection status must identify pet-data freshness rather than imply a full map snapshot arrived.
