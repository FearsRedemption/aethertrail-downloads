# AetherTrail instructions

This guide covers the Windows preview. It is included offline and updated with each application release. Use **Find in instructions** and press Enter or **Find next** to locate a topic. Clear the search using its × button. Links open in your browser.

## 1. Install, upgrade and uninstall

For a normal installation, download **AetherTrail-Setup-x64-vVERSION-preview.exe** from the [public releases](https://github.com/FearsRedemption/aethertrail-downloads/releases). Run Setup, select your installation folder and shortcut options, then install. Python, Rider and PyCharm are not needed. The preview is unsigned.

Setup installs for your Windows account. Its initial folder is **LocalAppData\Programs\AetherTrail**. It adds Start menu access, an optional desktop shortcut and a Windows Installed apps entry. Application files belong in that installation folder; the desktop contains a shortcut rather than the runtime. A later Setup download remembers the previously registered folder. Close the copy using that folder before upgrading; Setup does not force-close it. Old runtime and licence files in a recognized AetherTrail installation are cleared before the new versions are installed, so obsolete libraries do not accumulate there. Personal files and saved app data are kept separate.

You can also choose the portable ZIP. Extract the **entire** ZIP into a dedicated folder and keep Aethertrail.exe, the updater, _internal and licences together. Launch the executable in that folder. The portable ZIP does not register a normal installation. A browser download alone does not install or replace an existing copy.

Use Windows **Settings → Apps → Installed apps → AetherTrail → Uninstall** to remove an installed copy. The uninstaller removes the program and its installed shortcuts; it preserves local saved data. Do not manually move a registered installation. Use Setup to change its location. A portable copy can be moved as a complete folder.

Settings, timer deadlines, crafting plans and character data are stored under **LocalAppData\Aethertrail**, separately from program files. Private recordings are stored where you explicitly choose. Back up saved data with the app closed before transferring it to another computer. Copying a shortcut alone does not transfer the app or its data.

## 2. First launch and window controls

The app opens maximized by default. The left rail switches between Navigation, Pets, Regions, Crafting, Timers, Checklists and Settings. Each destination shows its own workspace. Switching away from Navigation hides the map while timers continue running.

Open **Settings → Display** to choose Dark or Light theme, adjust UI scale, set reminder sounds, or maximize/restore. UI scale enlarges text and icons and also scales the hosted map. Controls can wrap or scroll when larger text needs more room. Press **F11** for full screen and **Escape** to leave full screen. Display preferences are saved between launches.

If the map flashes or fails to render, try **Settings → Display → Map rendering → Compatibility (OpenGL)** and restart when convenient. You can switch back to the system default. Rendering behaviour can vary by graphics driver; changing the preference takes effect after restart.

## 3. Use the Navigation map

Navigation embeds the existing [Aion2Maps.com](https://aion2maps.com/) interactive map. It needs internet access. The site's own menus handle faction selection, regions and dungeon maps, search, layers, collectable filters, zoom and collection controls. Follow its first-run faction prompt; the app does not duplicate those map menus.

The toolbar holds your character progress profile, **Start location reading**, **Follow detected area**, and **Map tools**. At larger scales it wraps so controls stay readable. The line beneath reports map loading, position evidence and the local reader's state. Hover truncated status text to read its full tooltip.

Use **Map tools → Reload map** for a failed load, or **Open in browser** to view the site externally. Other Map tools expose character progress, character creation, tracking help, location-label configuration and experimental tracking. They do not require a second map-selector sidebar.

Select the correct character profile before reviewing or marking progress. Use **Map tools → Add character** to create a separate profile. Cached map/progress data is separated by character. A detected game character is linked only after you choose or confirm the corresponding profile.

## 4. Start screen location reading

1. Open AION 2, enter the world, and leave its minimap visible. This computer must have the game running for real screen reading.
2. In Navigation, click **Start location reading**. Choose the monitor containing the game.
3. Drag around the **minimap terrain**, excluding the title above it. The next step asks for the title.
4. Drag around **only the current-location name above the minimap**, such as Dawn Legion Base. Exclude dungeon entrance labels inside the terrain, quest text and other HUD elements.
5. Confirm **Start reading**. Cancel leaves reading stopped. The app uses a local screenshot and does not send controls to the game.
6. Watch the reader and location status. Repeated confident title readings identify a supported area before switching the map.

Click Capture screenshot and switch to Aion during the three-second countdown, then return to select the crops. Capture runs in a separate helper with a 15-second timeout. The title strip may be as short as 8 pixels; minimap terrain must be at least 32 by 32. Errors appear inline and Cancel stays available. Keep the game visible. Select again after changing monitors, game resolution, HUD layout or window size. Starting/resuming asks you to confirm the crops again. **Pause location reading** stops that session.

Keep **Follow detected area** checked to follow confirmed regions and supported dungeon routes. Choosing another map pauses following, allowing you to browse freely. Check it again to return to the detected area. Unknown, obscured or unsupported titles keep the current map; they do not trigger a guessed switch.

**Settings → Location** holds the Game HUD mode and advanced label configuration. Auto HUD mode, manual label crops and Off are available. The ordinary Start workflow guides crop selection rather than requiring numeric pixel coordinates. Advanced aliases allow alternate/localized names; use them only when you know which map a label belongs to.

## 5. Understand the location marker

An **area outline** means the named geographic area is known. It is not an exact player coordinate. A **position dot** needs fresh, validated position evidence, such as a sufficiently confident match to a calibrated terrain reference. A **question mark** means the location evidence is missing, stale or too uncertain. Paused reading uses a steady unknown indicator. A stale coordinate is removed rather than shown as if current.

Minimap-title OCR alone cannot tell where you stand inside a region. Experimental terrain tracking requires calibrated references and has limited coverage. Use **Map tools → Tracking setup and help** for the guided explanation, or **Settings → Advanced → Minimap tracking setup** for experimental setup. Confirm the right game monitor, minimap crop and reference calibration before trusting a position match. If the status reports low confidence or missing references, use area-following until better evidence is available.

**Positioning Lab** is an advanced testing workspace. Its simulated/manual positions and synthetic maps are labelled fixtures. They do not prove a live position on the hosted game map. Do not confuse a test marker with live player tracking.

Continuous network player coordinates and party/invite-code location sharing are **not available** in this preview. Being able to read a character identity or pet information does not establish a working navigation arrow. Live game tracking needs verification with the actual game, including region and dungeon transitions.

## 6. Game connection and Npcap

The capture helper is **included inside AetherTrail**. You do not need Wireshark or another companion application running. Npcap is a separate Windows packet-capture **driver**. Install it only from its [official download page](https://npcap.com/#download), linked in **Settings → Connection**. It is not bundled. Screen-based area reading works without it.

Connection **Auto** observes the exact supported AION 2 process when the driver and one usable game client are available. **Off** is saved between launches; **Pause** lasts for the current launch. Connection diagnostics show whether the driver, game process and transport are available. With no game running, waiting for a game connection is expected. The app does not install drivers automatically.

Verified Global Steam login observations can populate character identity, pet ownership, levels and soul points. Enter the world/relog to refresh supported login information. Live soul gains, claim eligibility, continuous map position and automatic feather identification remain unverified. Unknown information stays unknown.

If a link-character dialog appears, select the intended existing profile or create a separate one. Cancel if the identity is wrong. Do not link different characters to the same profile just to suppress the prompt.

**Record 60-second game diagnostic** is an optional troubleshooting tool. It requires a usable game connection and explicit confirmation. Choose a private folder. The bounded recording may contain character names, chat and session information; it is not uploaded automatically. Use Stop recording to finish early. **Export connection summary** produces a reduced diagnostic summary without raw packet contents or character identifiers. Importing verified reference catalogs and reviewing corrections are advanced functions, not requirements for normal navigation.

## 7. Pets and regional progress

**Pets** displays supported login pet observations for a linked character, with search/filter controls. Unseen pets remain unknown; a blank/unknown row is not proof you lack the pet. Claim eligibility is not verified. Relog into the world to refresh login-derived ownership and levels.

**Regions** reviews saved regional checklists and map marks, including offline. Visit a region in Navigation to load it initially; refresh the current map to update its saved snapshot. Select the intended character and region. Manual marks are stored per character/region. Saved positive observations can be shown as last known; stale absence is not proof of missing progress.

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

On expiry, AetherTrail updates its alert area and requests a Windows sound/system notification when enabled and available. **Settings → Display → Test reminder sound** exercises the reminder path. Check Windows volume, mute and notification settings if it is silent. The app must be open: it does not install a reminder service.

Running timers preserve an absolute deadline when the app closes. Paused timers preserve their remaining duration. An overdue one-shot timer alerts once after reopening. Missed repeating cycles collapse into one alert instead of producing a flood of old notifications. Timers are personal reminders; they do not guarantee the boss/event is currently available.

## 10. Checklists

Use **Checklists** to create and maintain personal tasks/groups. Group and completion filters help focus on pending work; completed entries remain available when you choose the matching filter. Click an entry's completion control when you finish it. Add/edit/remove tasks with the available controls.

Group resets are manual. The app does not assume a game's daily or weekly reset time. Review the selected group before resetting it. These personal tasks are separate from character/region map progress and verified network observations.

## 11. Updates and notifications

Open **Settings → Updates** for scheduled checks, startup prompts and downloads. Background checks default to every 30 minutes while the app is open. You can disable them, change the interval, or choose a daily local-clock time. **Check for updates** requests a check immediately. Source commits and draft releases alone do not create a ready update; a newer public release must have its Windows ZIP fully uploaded.

A quiet glowing dot on **Settings** means a newer release is ready. Clicking it opens Updates. Failed checks keep the last known indicator. Repeated checks preserve unchanged release notes. Scheduled checks do not install, restart, play an update sound or switch your current workspace.

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
