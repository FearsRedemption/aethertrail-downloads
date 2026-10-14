# Aethertrail preview testing

Download: https://github.com/FearsRedemption/aethertrail-downloads/releases

Choose **Aethertrail-Windows-x64-v0.8.9-preview.zip** under Assets, not GitHub's Source code archive. Extract the complete ZIP into a folder and run **Aethertrail.exe**. Keep `_internal`, `licenses` and the included scripts beside it. Windows 10/11 x64; no Python, PyCharm or Rider needed. This preview is unsigned. The app opens maximized; use Settings for Maximize / restore and UI scale, or F11 / Escape to adjust the display. Internet is needed for the hosted map; OCR models are bundled and run locally.

The map site's first-run faction prompt lets you choose your side or “Not sure yet? Just show me the map”. Click **Start location reading** and choose your game monitor. Drag around minimap terrain first, then only the current-location title above it. Cancel leaves reading stopped. Aethertrail temporarily hides its own windows for the local screenshot and sends no game input. The title selects regions and supported dungeon routes after repeated confident readings; dungeon entrance labels inside the terrain are excluded. Unknown titles keep the current map. Pause stops reading; starting again asks for the crops again. Reselect after moving or resizing the game. Browsing away pauses Follow detected area; check it to return to the detected location. Reload, Open in browser and advanced location setup are under Map tools. If Navigation flashes, select Compatibility (OpenGL) in Settings and restart.

## Self-tests

The daily rail has Navigation, Crafting, Timers and Checklists; Settings holds display, alert sounds, Updates and advanced tools. Crafting combines Recipes, Items, Plans and Materials. Search is always available; catalog filters expand on demand. Select a verified artwork row to see ingredients or crafting uses. Related links stay in Crafting and provide Back navigation. Add a recipe to My plans, choose crafts, and edit owned quantities directly in ingredient rows. Counts are shared with Materials, remain manual and are not consumed automatically. The offline catalog covers crafting items, not every game item.

Timers prioritizes running countdowns. New countdowns and saved observations use focused forms; each timer has Start / Pause and an options menu for reset/edit/remove. Known timers retains source-labelled Global schedules and requires your actual server UTC offset. Checklists supports group and completion filters, visible completed tasks and manual group resets. Updates downloads and verifies newer previews before relaunching. Existing experimental tracking and character progress retain their v0.7.5 limitations.

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

Download SHA256SUMS.txt from the same release. Run `Get-FileHash .\Aethertrail-Windows-x64-v0.8.9-preview.zip -Algorithm SHA256` and compare with the matching line. A checksum detects corruption; it is not a code signature.

The app is unofficial and is not endorsed by NCSOFT or Aion2Maps.com. Exact catalog-linked game item icons are bundled for offline use, with NC Corporation attribution and per-image source/hash records. No website source is bundled. Aethertrail captures configured screen pixels, with no memory reads, injection or gameplay input automation. Source remains private; this public repository hosts test binaries, documentation and issue reports. Third-party notices and library replacement/source information are included under licenses.

Character progress: use Navigation's Character selector and add a separate profile before switching characters. Open the game's Kibelisk list to sync visible completed/incomplete rows. Only visible readable evidence changes progress; scroll the list yourself to expose more points. Initial calibrated local terrain references and private visual templates are required for experimental tracking/icon sync and are not shipped with this download. Relative terrain tracking expires after 20 seconds without a map match. See release notes for verified behavior and remaining gameplay checks.

Game connection: Settings defaults to Auto. Installed usable Npcap starts game-owned passive traffic observation when one AION 2 client is running. Off persists and Pause lasts for the launch. No driver is bundled or installed. This release provides diagnostics, a bounded local recorder and Global Steam identity/login pet observations. Live pet updates, claim eligibility and map position remain unavailable. Existing screen/manual features remain available. Recordings can contain private chat/character/session data and are never uploaded automatically.

## Login diagnostic recording (v0.8.2)

Settings -> Game connection -> Record 60-second game diagnostic. Recordings now follow socket changes for the same single AION 2 process, so you can return to character selection and enter the same character while recording. The time/size limit is preserved. Recording ends on game exit, process replacement or multiple game instances. Files stay private; only validated Global Steam identity/login pet observations are available. Endpoint discovery can miss the earliest traffic of a new socket.

## Automatic login pet progress (v0.8.9)

With Auto enabled, the Global Steam client sends your identity and pet list when you enter the world. After starting this version, return to character selection and enter the same character. Confirm the first profile link in Aethertrail, then open Pets in the sidebar. Ownership, levels and explicit soul points appear with readable names and search/filter controls. Values reflect the last login; relog to refresh them. Missing fields stay unknown. Live soul gains, claim eligibility, feathers and map position remain unavailable. Other client distributions continue connection diagnostics without this decoder. Raw diagnostics remain private.

## Pets and regional progress

**Pets** is a dedicated sidebar page. Search the 207 reference pet names, filter confirmed or unknown ownership, and read the last login's level and soul points. Reference names alone do not establish that a pet is missing or ready to claim.

**Regions** opens Regional Progress. Choose a map on Navigation first, then open Regions to read its feathers and Kibelisks. Filter category/state or search by name or marker ID. The checklist refreshes while visible, and previously viewed regions remain selectable during this session. Counts distinguish verified collected, verified missing, unknown and saved map marks. Unmarked map icons remain unknown. Map marks belong to the selected Navigation character profile; this page reads them without changing them. Automatic feather/Kibelisk decoding and full regional completion totals are still pending protocol verification.

## Automatic HUD discovery (available since v0.8.5)

Settings -> Automatic location reading -> Game HUD defaults to Auto HUD detection. Bring one supported Global Steam game client to the foreground on the normal gameplay HUD. Discovery requires a recognized title, minimap boundaries and clock/layout evidence across repeated frames; it then reads the location strip and follows confirmed areas. Hidden/obscured windows, unknown titles or layout changes clear the reading. No game inputs are sent and normal frames are not saved. Auto HUD detection does not require Npcap.

Manual label crops remain saved and selectable. Off persists; the Navigation pause button lasts for the current launch. Test frames at 2560x1440 and simulated 1920x1080 were acquired; smaller 1280x720 samples remained unknown when border evidence was ambiguous. Use Manual label crop if Auto cannot recognize your HUD. This preview still needs live foreground/resize acceptance on the running client.

Detecting the minimap's screen rectangle does not provide precise world coordinates. Terrain position still requires calibration. Existing claimed feathers, exact feather IDs, live pet soul changes and claim eligibility remain unverified. Feather receipts cannot mark the nearest map collectible automatically. Regional unknown/marked distinctions remain in place.
## UI stability (available since v0.8.6)

Pets and Regions preserve unchanged rows during automatic polls. Location messages stay on one line; hover for the complete message. The hidden map pauses on native pages and resumes for Navigation/Regions without reloading. Compare Navigation, Pets, Regions and Crafting for rapid flashing, especially while the connection/location status changes. The native stress check passed, but the user reported flashing continued with the default renderer.

Existing recordings have not established continuous precise coordinates for your own character. A login placement and other entities' movement are insufficient for a live player dot. Automatic HUD discovery identifies the location strip and minimap crop; absolute terrain position still needs calibration.

## Offline regional review (v0.8.9)

Open Regions to view previously loaded checklists while offline or after restarting. Each checklist and its map marks belong to the selected character profile and region. Visit a region on Navigation to load it the first time; Refresh current map updates its saved snapshot. Unchanged refreshes do not rewrite the cache.

Saved map marks remain Marked, not verified Collected. If a verified linked character has saved positive collection evidence and a validated exact marker reference, offline review labels it Last known verified collection. Stale missing states stay Unknown; partial captures cannot establish full completion. No stable automatic feather IDs have yet been validated, so the supplied recordings do not automatically mark the feathers you gathered. Pet login observations remain saved separately.

Settings -> Map rendering -> Compatibility (OpenGL) is a saved option for flashing. Restart Aethertrail to apply it. The user confirmed the temporary OpenGL trial stopped the flashing with the map loaded. System default remains available. No Windows graphics settings are changed.
