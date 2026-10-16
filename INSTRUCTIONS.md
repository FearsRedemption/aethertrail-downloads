# AetherTrail instructions

This guide covers the Windows preview. It is included offline and updated with each application release. Use **Find in instructions** and press Enter or **Find next** to locate a topic. Clear the search using its × button. Links open in your browser.

## 1. Install, upgrade and uninstall

For a normal installation, download **AetherTrail-Setup-x64-vVERSION-preview.exe** from the [public releases](https://github.com/FearsRedemption/aethertrail-downloads/releases). Run Setup, select your installation folder and shortcut options, then install. Python, Rider and PyCharm are not needed. The preview is unsigned.

Setup installs for your Windows account. Its initial folder is **LocalAppData\Programs\AetherTrail**. It adds Start menu access, an optional desktop shortcut and a Windows Installed apps entry. Application files belong in that installation folder; the desktop contains a shortcut rather than the runtime. A later Setup download remembers the previously registered folder. Close the copy using that folder before upgrading; Setup does not force-close it. Old runtime and licence files in a recognized AetherTrail installation are cleared before the new versions are installed, so obsolete libraries do not accumulate there. Personal files and saved app data are kept separate.

You can also choose the portable ZIP. Extract the **entire** ZIP into a dedicated folder and keep Aethertrail.exe, the updater, _internal and licences together. Launch the executable in that folder. The portable ZIP does not register a normal installation. A browser download alone does not install or replace an existing copy.

Use Windows **Settings → Apps → Installed apps → AetherTrail → Uninstall** to remove an installed copy. The uninstaller removes the program and its installed shortcuts; it preserves local saved data. Do not manually move a registered installation. Use Setup to change its location. A portable copy can be moved as a complete folder.

Settings, timer deadlines, crafting plans and character data are stored under **LocalAppData\Aethertrail**, separately from program files. Private recordings are stored where you explicitly choose. Back up saved data with the app closed before transferring it to another computer. Copying a shortcut alone does not transfer the app or its data.

## 2. First launch and window controls

The app opens maximized by default. The left rail switches between Navigation, Pets, Closet, Regions, Crafting, Timers, Checklists and Settings. Each destination shows its own workspace. Switching away from Navigation hides the map while timers continue running.

Open **Settings → Display** to choose Dark or Light theme, adjust UI scale, or maximize/restore. UI scale enlarges text and icons and also scales the hosted map. Controls can wrap or scroll when larger text needs more room. Press **F11** for full screen and **Escape** to leave full screen. Display preferences are saved between launches.

If the map flashes or fails to render, try **Settings → Display → Map rendering → Compatibility (OpenGL)** and restart when convenient. You can switch back to the system default. Rendering behaviour can vary by graphics driver; changing the preference takes effect after restart.

When a new update is found, a brief golden sparkle trail flows down the left sidebar toward **Settings**. Click Settings to view the available update; the trail stops and the update dot stays until availability clears. Repeated checks for the same version do not replay it. Turning off update notices in Settings -> Updates also turns off the trail. Downloading and restarting still require your choice.

## 3. Use the Navigation map

Navigation embeds the existing [Aion2Maps.com](https://aion2maps.com/) interactive map. It needs internet access. The site's own menus handle faction selection, regions and dungeon maps, search, layers, collectable filters, zoom and collection controls. Follow its first-run faction prompt; the app does not duplicate those map menus.

The toolbar holds your character progress profile, **Start location reading**, **Follow detected area**, and **Map tools**. At larger scales it wraps so controls stay readable. The line beneath reports map loading, position evidence and the local reader's state. Hover truncated status text to read its full tooltip.

Use **Map tools → Reload map** for a failed load, or **Open in browser** to view the site externally. Other Map tools expose character progress, character creation, tracking help, location-label configuration and experimental tracking. They do not require a second map-selector sidebar.

Select the correct character profile before reviewing or marking progress. Use **Map tools → Add character** to create a separate profile. Cached map/progress data is separated by character. A detected game character automatically gets a separate linked profile, which is selected on Navigation. Existing manual profiles are preserved; Advanced diagnostics can link to an existing profile if you explicitly choose that.

## 4. Start screen location reading

1. Open AION 2, enter the world, and leave its minimap visible. This computer must have the game running for real screen reading.
2. In Navigation, click **Start location reading**. Choose the monitor containing the game.
3. Click **Capture screenshot**, switch to Aion during the three-second countdown, then return. Use the **mouse wheel to zoom**, **hold the middle mouse button and drag to pan**, and **left-drag to select** the minimap terrain, excluding its title.
4. Zoom or pan again if needed, then left-drag around **only the current-location name above the minimap**, such as Dawn Legion Base. Exclude dungeon entrance labels inside the terrain, quest text and other HUD elements.
5. Confirm **Start reading**. Cancel leaves reading stopped. The app uses a local screenshot and does not send controls to the game.
6. Watch the reader and location status. Repeated confident title readings identify a supported area before switching the map.

Click Capture screenshot and switch to Aion during the three-second countdown, then return to select the crops. Capture runs in a separate helper with a 15-second timeout. The title strip may be as short as 8 pixels; minimap terrain must be at least 32 by 32. Errors appear inline and Cancel stays available. Keep the game visible. Select again after changing monitors, game resolution, HUD layout or window size. Select these boxes once: Start reuses them after stopping or restarting. If reading was running when you closed the app, it resumes automatically with the saved setup. Stop keeps the boxes and prevents automatic resume. Use **Map tools → Redo minimap and title setup** or **Settings → Location → Redo minimap and title setup** if the game layout changes. The last confirmed region/subarea opens as last known; a fresh reading is required for live tracking.

**Fit screenshot** returns to the full screenshot without clearing your boxes. Zooming and panning change only the view: both saved crops stay in original screen pixels, so tracking uses the same terrain/title areas you selected. The terrain and title buttons let you redraw either box; changing the terrain requires selecting the title again.

Keep **Follow detected area** checked to follow confirmed regions and supported dungeon routes. Choosing another map pauses following, allowing you to browse freely. Check it again to return to the detected area. Unknown, obscured or unsupported titles keep the current map; they do not trigger a guessed switch.

**Settings → Location** holds the Game HUD mode and the explicit Redo setup control. Auto HUD mode, manual label crops and Off are available. The ordinary Start workflow guides crop selection rather than requiring numeric pixel coordinates. Advanced aliases allow alternate/localized names; use them only when you know which map a label belongs to.

## 5. Understand the location marker

An **area outline** means the named geographic area is known. It is not an exact player coordinate. A **position dot** needs fresh, validated position evidence, such as a sufficiently confident match to a calibrated terrain reference. A **question mark** means the location evidence is missing, stale or too uncertain. Paused reading uses a steady unknown indicator. A stale coordinate is removed rather than shown as if current.

Minimap-title OCR alone cannot tell where you stand inside a region. Starting location reading also enables the existing terrain and visible-progress reader with the saved minimap setup. Experimental terrain tracking requires calibrated references and has limited coverage. Use **Map tools → Tracking setup and help** for the guided explanation, or **Settings → Advanced → Minimap tracking setup** for experimental setup. Confirm the right game monitor, minimap crop and reference calibration before trusting a position match. If the status reports low confidence or missing references, use area-following until better evidence is available.

**Positioning Lab** is an advanced testing workspace. Its simulated/manual positions and synthetic maps are labelled fixtures. They do not prove a live position on the hosted game map. Do not confuse a test marker with live player tracking.

Continuous network player coordinates and party/invite-code location sharing are **not available** in this preview. Being able to read a character identity or pet information does not establish a working navigation arrow. Live game tracking needs verification with the actual game, including region and dungeon transitions.

## 6. Game connection and Npcap

The capture helper is **included inside AetherTrail**. You do not need Wireshark or another companion application running. Npcap is a separate Windows packet-capture **driver**. Install it only from its [official download page](https://npcap.com/#download), linked in **Settings → Connection**. It is not bundled. Screen-based area reading works without it.

AION can run an idle launcher parent alongside its connected game process. AetherTrail recognizes that verified parent/child pair as one client. Separate or ambiguous clients remain blocked; no game process is closed.

Connection **Auto** observes the exact supported AION 2 process when the driver and one usable game client are available. **Off** is saved between launches; **Pause** lasts for the current launch. Connection diagnostics show whether the driver, game process and transport are available. With no game running, waiting for a game connection is expected. The app does not install drivers automatically.

Verified Global Steam login observations can populate character identity, pet ownership, levels and soul points. Enter the world/relog to refresh supported login information. Live soul gains, claim eligibility, continuous map position and automatic feather identification remain unverified. Unknown information stays unknown.

**To load or refresh character/pet data:** leave AetherTrail open with **Settings → Connection → Auto**, return to AION’s character selection, then enter the character you want to sync. Restarting only AetherTrail while already in the world will not replay login messages. A separate profile is created and selected automatically when identity arrives. Repeat world entry after switching characters or to refresh pets. No recording or reference import is required for supported login data. Connection shows whether it is waiting for traffic, waiting for character data, or has imported pets.

**Record 60-second game diagnostic** is an optional troubleshooting tool. It requires a usable game connection and explicit confirmation. Choose a private folder. The bounded recording may contain character names, chat and session information; it is not uploaded automatically. Use Stop recording to finish early. **Export connection summary** produces a reduced diagnostic summary without raw packet contents or character identifiers. Importing verified reference catalogs and reviewing corrections are advanced functions, not requirements for normal navigation.

## 7. Pets and regional progress

**Pets** displays a searchable portrait gallery with supported login pet observations for the selected character, soul requirements, named soul sources and recorded source locations. Unseen pets remain unknown; a blank/unknown row is not proof you lack the pet. Claim eligibility is not verified. Relog into the world to refresh login-derived ownership and levels.

**Regions** reviews saved regional checklists and map marks, including offline. Use the same character-selection/world-entry step above to select the correct linked character. Login currently imports pets, not a full collectible checklist. Visible game-map completion evidence is synced automatically while location reading is running; unknown/missing evidence never becomes an invented completion mark. Visit a region in Navigation to load it initially; refresh the current map to update its saved snapshot. Select the intended character and region. Manual marks are stored per character/region. Saved positive observations can be shown as last known; stale absence is not proof of missing progress.

**Map tools → Character progress** expands the optional progress panel. Search and category/state filters help review linked observations and references. The collapsed panel does not occupy a separate Navigation row. Verified corrections can change completion marks while preserving manual notes. A hosted-site mark and a verified game observation may have different evidence; inspect the source/status rather than assuming everything is live inventory.

## 8. Crafting: Recipes, Items, Plans and Materials

Open **Crafting** and select its internal destination. **Recipes** and **Items** use the bundled offline crafting catalog. The catalog is not a complete list of every game item. Artwork is shown only when mapped to a verified entry; unknown artwork is not replaced with an invented item picture.

Type part of a name to search. Use the search field's × to clear it. Expand filters when you want to narrow the catalog. Select a row to view ingredients or crafting uses. Related ingredient/use names are clickable when linked; follow them within Crafting and use Back to return. Suggestions and name pickers help choose an existing entry rather than creating a duplicate spelling.

Add a recipe to **My plans**, choose the number of crafts and review each ingredient's needed, owned and missing quantities. Edit owned counts directly or use its completion checkbox where offered. These counts are shared with **Materials** and other plans. Readiness is based on your saved counts; quantities are not automatically consumed when a plan becomes ready.

Use **Materials** to add, edit or remove owned quantities. You can type counts instead of using the spinner arrows. Check spelling or choose a catalog name so related plans use the same material. The app saves changes and refreshes readiness. Inventory counts remain manual: live inventory OCR, automatic item recognition and game inventory synchronization are not connected.

Custom recipe/planning forms let you maintain personal lists. Clearly name custom entries and check their ingredient amounts. The app does not validate every custom recipe against an official crafting feed. Treat them as your own planning data.

## 9. Timers and sounds

**Timers** prioritizes your active countdowns. Create a Boss, Event or Custom countdown, enter its duration and choose whether it repeats. Start it explicitly. Use Pause/Resume to control a running reminder and the timer's options menu to reset, edit or remove it. Search and category filters reduce the list. The persistent reminder area reports active/expired reminders across workspaces.

Known/server schedules are source-labelled reusable information, not live spawn observations. Set your actual **server UTC offset** before relying on a server-clock schedule. Selecting a saved observed interval prepares the countdown form; it does not start the timer automatically. Add personal intervals only when you know their basis, and store source/server/region notes so they are not confused with verified schedules.

On expiry, AetherTrail updates its alert area and plays your chosen reminder chime when enabled. **Settings → Sounds** offers Starlight, Gentle bells, Woodland notes and Bright chime, separate update/reminder switches and choices, volume, Preview and Mute all app sounds. Muting keeps visual alerts. Reminder sounds close together are coalesced, and unavailable audio fails quietly. Check Windows volume, mute and notification settings if it is silent. The app must be open: it does not install a reminder service.

Running timers preserve an absolute deadline when the app closes. Paused timers preserve their remaining duration. An overdue one-shot timer alerts once after reopening. Missed repeating cycles collapse into one alert instead of producing a flood of old notifications. Timers are personal reminders; they do not guarantee the boss/event is currently available.

## 10. Checklists

Use **Checklists** to create and maintain personal tasks/groups. Group and completion filters help focus on pending work; completed entries remain available when you choose the matching filter. Click an entry's completion control when you finish it. Add/edit/remove tasks with the available controls.

Group resets are manual. The app does not assume a game's daily or weekly reset time. Review the selected group before resetting it. These personal tasks are separate from character/region map progress and verified network observations.

## 11. Updates and notifications

Open **Settings → Updates** for scheduled checks, startup prompts and downloads. Background checks default to every 30 minutes while the app is open. You can disable them, change the interval, or choose a daily local-clock time. **Check for updates** requests a check immediately. Source commits and draft releases alone do not create a ready update; a newer public release must have its Windows ZIP fully uploaded.

A quiet glowing dot on **Settings** means a newer release is ready. Clicking it opens Updates. Failed checks keep the last known indicator. Repeated checks preserve unchanged release notes. A soft Starlight chime accompanies discovery of a new version unless muted or disabled in Settings → Sounds. Repeated checks of the same version remain quiet across restarts. Scheduled checks never install, restart or switch your workspace.

Startup update prompts are enabled by default. **Yes** starts the verified download/restart flow; **No** leaves the app open. **Disable startup notifications** turns off only the startup popup. Scheduled checks and the Settings dot remain separate. Re-enable the popup in Updates. If you want a startup check without a popup, enable the startup-check option while leaving the popup disabled.

Choose **Download update & restart** when convenient. The app downloads to staging, checks the release checksum/archive/version and replaces files in the folder containing the running executable. It does not choose Desktop as a default update destination. You can cancel during download. After verification, the helper waits for this app to close, replaces the managed program files and relaunches from that same folder. Failed replacement/relaunch rolls back the previous files. Saved app data is separate.

Downloading a new **Setup** executable in your browser is the normal alternative: run it to upgrade the registered installation. It remembers the prior installation folder. A source checkout uses Git instead of binary replacement. Keep release files together and use the public installer/ZIP rather than GitHub's automatically generated Source code archive.

## 12. Troubleshooting and testing

If startup fails, record the exact message and installed version. Get the newest Setup release if the old app cannot open its own update page. AetherTrail v0.8.14 fixed the earlier “os not defined” startup error. Keep the full runtime with the executable; copying only the EXE is insufficient for portable builds.

For a blank hosted map, check internet access, wait for initial loading, Reload map, and try Open in browser. For rendering flashes, test the alternative renderer and restart when ready. A renderer change does not repair incorrect minimap crops or unverified coordinates.

For incorrect area following, pause reading, select the monitor/crops again and verify that the title is readable and above the terrain. Unknown localized labels may need advanced aliases. Area-only status is expected without reliable position calibration. No game installed/running means live tracking cannot be tested.

The optional **Test-Aethertrail.ps1** beside the program runs isolated application checks and writes reports. Online checks require the hosted site. Use its **-SkipScreenCapture** option when a usable unlocked desktop/game screenshot is unavailable, or **-OfflineOnly** for launch checks. Test fixtures are labelled synthetic; a passing report does not prove live dungeon/player tracking. Tests do not control the game.

When reporting an issue, include your app version, affected page, UI scale/theme/renderer, steps and the error or a cropped screenshot. Review screenshots/reports before sharing them. Raw private game recordings are not ordinary shareable test reports.

## 13. What is still experimental

Continuous player coordinates, reliable all-dungeon terrain coverage, live inventory/material tracking, automatic feather identification and party/invite-code location sharing are not complete. This guide will be revised when their actual implementation and verification change. Existing manual/offline tools remain useful independently of those features.

## Fresh install from an older version

Download the latest **AetherTrail-Setup-x64** executable from the public releases page. Close the old app, run Setup and follow its prompts; it installs the complete app and offers to launch it. No manual ZIP extraction is required. Keep saved settings and character progress in AppData. The built-in updater remains available for existing installations; ZIP downloads are optional portable/updater packages.

## Pets, Closet and exploration completion (v0.9.0)

Pets shows 207 original game portraits, observed ownership, level and soul points. Cards default to Owned, then Missing, then Unknown, with names alphabetical within each group. Select a card for soul requirements, named soul sources, known source locations and its reference link. The catalog is browsable offline before connecting. Unknown stays unknown. Leave Connection on Auto, return to character selection and enter your character once to receive login observations; relog to refresh them. Mount eligibility is not separately verified.

Pets and Materials use the available window width to show more cards. Drag the divider to adjust the pet preview/details or material families panel. Extra window space expands the card list. Automatic location following frames the detected geographic area without selecting it or adding a search highlight. Saved positive screen completions are restored for the selected character and region once the hosted map is ready; old negative observations do not clear newer manual marks on reload.

Closet contains Armor, Weapons and Decoration collections from 1,463 Global-client appearances. Search by set or piece name; select a collection to view its full-set appearance and inspect individual pieces and unlock items/source links. Armor entries distinguish game SkinSet membership from browsing name families. Obtained, Missing and Unknown are manual appearance notes saved separately for each selected character. The app does not infer Closet unlocks from inventory, equipped gear or pet packets. The renderer is bundled; full-set model files download from AetherTrail and are cached. Some icons and acquisition routes are unavailable; a listed unlock item does not establish a dungeon drop location.

Start location reading, then open AION’s full map → Exploration. Repeated, confident **100%** Sealed Dungeon summaries mark the current region’s native sealed-dungeon markers, including older completions. Explicit **0%** clears that category for the selected character; partial percentages alone do not identify which individual dungeons remain. Repeated, clearly checkmarked named rows can sync older completions as you scroll the list; blank rows stay unknown. This summary reading works without a matched terrain reference. Stronghold 100%/0% is saved as regional completion and displayed above Navigation and in Regions, because the hosted map has no native stronghold checklist marker type. Scanning stays on the remembered game monitor.

Visible supported icon evidence remains available with aligned terrain references. Screen observations are saved per character and region, separate from manual map marks. Opening another character’s map does not transfer these observations. A hidden or disappearing dungeon icon never proves completion. Network collectible decoding remains unavailable; pet imports alone cannot mark a map.

Collection reading continues while location reading is running; it is not a one-time import. Visible teleport binding lists and Exploration summaries are checked repeatedly, including without a reliable terrain match. Later confirmed states update that character's saved observations. Teleport observations are saved even when their companion-map markers are already checked. Older saved teleport sync records are recovered when their character, marker ID and name match exactly one cached regional entry. Only visible entries can be read; a list showing twelve rows does not establish the state of off-screen rows.

Names vary between interfaces: the game's Kibelisks are teleport/TP markers in Navigation; Sealed Dungeons use the hosted map's sealed-dungeon markers. A saved explicit 100% Sealed Dungeon summary can restore that region's native sealed markers without matching individual translated names. Newer explicit missing observations take precedence over an older summary. Stronghold completion is regional because the hosted map does not expose native stronghold completion markers.

Settings → Sounds contains four original bundled chimes, separate update/reminder choices and enable switches, volume, Preview and Mute all app sounds. New-version discovery chimes once; duplicate checks remain quiet across restarts. Nearby timer expirations coalesce playback. Audio failure leaves visual alerts available without a Windows error beep fallback. Checks notify; installation is your choice.

## Closet: character appearance preview

Select an Armor set to view its full appearance on the game's base body. Choose Male or Female above the preview. Drag to rotate, scroll to zoom, and right-drag to pan; Reset view returns to the full body. Individual piece buttons update acquisition information without replacing the character model with an icon. The base body is a reference, not your custom character, and does not include your hairstyle or body customization.

The first view of each body downloads its model from AetherTrail's own GitHub downloads repository; subsequent views use the verified cache. The local renderer and male reference images ship with the app. No separate model-viewer app or external wardrobe site is needed. If a model cannot download or graphics rendering is unavailable, collection browsing and manual notes still work. A missing or unavailable female model never displays the male image as female. Single appearance families outside the 119 full sets may not have a model.

Only confirmed Owned pets use color portraits. Missing and Unknown pets use grayscale in both the gallery and preview. Unknown remains a separate evidence state; it does not mean confirmed missing.

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
