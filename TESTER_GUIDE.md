# Aethertrail preview testing

Download: https://github.com/FearsRedemption/aethertrail-downloads/releases

Choose **Aethertrail-Windows-x64-v0.7.4-preview.zip** under Assets, not GitHub's Source code archive. Extract the complete ZIP into a folder and run **Aethertrail.exe**. Keep `_internal`, `licenses` and the included scripts beside it. Windows 10/11 x64; no Python, PyCharm or Rider needed. This preview is unsigned. The app opens maximized; use Maximize / restore, F11 / Escape and the saved UI scale control to adjust the display. Internet is needed for the hosted map; OCR models are bundled and run locally.

The map site's first-run faction prompt lets you choose your side or “Not sure yet? Just show me the map”. Test zoom/pan, Maps menu, search and layers. Under Location label setup, choose the game monitor and drag around only the text above the minimap. Preview, save and Start area capture. Dawn Legion Base selects Verteron. Other map names or configured aliases can select dungeon/region routes after repeated confident readings. Unknown labels keep the current map. Stop area capture pauses capture. No automatic start on launch. Use the hosted Maps menu to browse. Browsing away pauses Follow detected area while capture stays active; check Follow detected area to return to your detected area. Reload and Open in browser are under Map tools.

## Self-tests

Navigation shows the full-width hosted map, with no native sidebar. Other tabs replace it with their own tools. Search fields have X clear buttons and catalog-name suggestions. Click recipe ingredients to open Items, item crafting uses to open Recipes, and tracked material names to edit counts. Plan options groups recipe actions. Quantity steppers have bright chevrons; scaled catalog/planner views scroll instead of squeezing tables. The offline catalog covers crafting items, not every game item. Known timers has source-labelled Global schedules: choose your actual server UTC offset before starting the next-opening reminder. My countdowns and Saved schedules retain personal reminders and observed intervals. Updates checks public previews, downloads and verifies the newest build, replaces managed files and relaunches. Versions through v0.7.1 need one manual installation to gain automatic updating. Counts and plans remain manual; live inventory, player arrows and shared invite rooms are unfinished.

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

Download SHA256SUMS.txt from the same release. Run `Get-FileHash .\Aethertrail-Windows-x64-v0.7.4-preview.zip -Algorithm SHA256` and compare with the matching line. A checksum detects corruption; it is not a code signature.

The app is unofficial and is not endorsed by NCSOFT or Aion2Maps.com. Exact catalog-linked game item icons are bundled for offline use, with NC Corporation attribution and per-image source/hash records. No website source is bundled. Aethertrail captures configured screen pixels, with no memory reads, injection or gameplay input automation. Source remains private; this public repository hosts test binaries, documentation and issue reports. Third-party notices and library replacement/source information are included under licenses.
