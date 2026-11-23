[b][color=#ff7700][size=6]Modlist Manager[/size][/color][/b]

Modlist Manager is a Mod Organizer 2 plugin that opens a web-based interface in your browser to manage, view, edit, and back up your mod load order. It was born from a simple problem: I had an Excel spreadsheet tracking my entire load order with comments, categories, and links for every mod. After months of not updating it, the idea of manually syncing hundreds of rows was unbearable. So instead of updating the spreadsheet, I built this plugin with the help of an AI agent, iterated on it through extensive testing and bug fixing, and arrived at what you see here.

This plugin serves as a living backup of your load order. If a game update breaks your setup, if you lose mods, or if you install something that prevents your game from launching, you have a complete record of what was there, in what order, with your own notes.

[size=5][b]Requirements[/b][/size]

[list]
[*]Mod Organizer 2 (version 2.4 or later, tested on 2.5.2)[/*]
[*]Python 3 (included with MO2)[/*]
[*]No external dependencies — the plugin runs entirely on the Python stdlib and vanilla JavaScript[/*]
[/list]

[size=5][b]Installation[/b][/size]
[list=1]
[*]Download the [b]modlist_manager.py[/b] file.[/*]
[*]Copy it into your MO2 [font=Courier New]plugins[/font] folder: [font=Courier New]<your-MO2-folder>\plugins\modlist_manager.py[/font][/*]
[*]Copy the translation files ([font=Courier New]modlist_manager_es.json[/font] and [font=Courier New]modlist_manager_en.json[/font]) into your MO2 [font=Courier New]translations[/font] folder: [font=Courier New]<your-MO2-folder>\translations\[/font][/*]
[*]Restart MO2.[/*]
[*]Go to [b]Tools → Modlist Manager[/b] (or find it in your plugins list and double-click it).[/*]
[*]A browser tab will open at [font=Courier New]http://127.0.0.1:8765/[/font] (or another port if that one is taken).[/*]
[/list]

[b][size=5]Video[/size][/b]
[b][size=5][youtube]ks06mUEqoNI[/youtube][/size][/b]

[size=5][b]Getting Started (First Run)[/b][/size]

[center][color=#ff0000][size=5]Starting with version 5.0, an initial loading method is required; this can be done via CSV or directly from a modlist. For large lists, using a CSV file is recommended, as it is faster.[/size][/color][/center]
[center][img]https://staticdelivery.nexusmods.com/mods/1704/images/187686/187686-1790899949-692884328.png[/img]
[/center]
When you open the plugin for the first time, it will ask you to export a CSV from MO2. This is required to capture the correct load order priority. Here's how:
[img]https://staticdelivery.nexusmods.com/mods/1704/images/187686/187686-1786154414-310777527.png[/img]

[list=1]
[*]In MO2, go to [b]Open List Options → Export CSV[/b][/*]
[*]Select [b]All installed mods[/b][/*]
[*]Check all columns (especially [b]Mod_Priority[/b])[/*]
[*]Save the file as [font=Courier New]modlist.csv[/font] in your MO2 root folder or your active profile's [font=Courier New]ModlistManager[/font] folder[/*]
[*]Click [b]Refresh[/b] in the plugin's top bar[/*]
[/list]
After the initial import, the plugin maintains its own database ([font=Courier New]database.json[/font]) inside your profile folder. You only need to re-export the CSV if you want to force a full refresh of mod data (versions, categories, links).


[size=5][b]Main Features — Tab by Tab[/b][/size]

[b][size=5]1. Mod List[/size][/b]

[img]https://staticdelivery.nexusmods.com/mods/1704/images/187686/187686-1790385671-1662608850.png[/img]
[img]https://staticdelivery.nexusmods.com/mods/1704/images/187686/187686-1786154411-965996353.png[/img]

This is the main tab. It displays your mods in the same priority order as MO2, with separators acting as collapsible sections (just like in MO2). DLCs and game files marked with [font=Courier New]*[/font] in modlist.txt are hidden automatically.

[color=#0099ff][b]Columns:[/b][/color]
[list]
[*][b]Act[/b] — Shows X (active) or O (inactive). For deleted mods, a red × button appears here to remove the mod from the plugin's memory.[/*]
[*][b]N°[/b] — Priority number, centered. Click to edit and the list auto-reorders.[/*]
[*][b]Trad[/b] — This column only appears if the translation add-on is installed and displays the same information as the add-on's "Trad" column.[/*]
[*][b]Mod[/b] — Mod name.[/*]
[*][b]Category[/b] — From MO2. Can be edited via double-click (opens edit modal).[/*]
[*][b]Version[/b] — From MO2's meta.ini.[/*]
[*][b]Comment MO2[/b] — The comment set in MO2. Synced from meta.ini, not editable here.[/*]
[*][b]Personal Comment[/b] — Your custom comment, stored in the plugin's memory. Survives CSV updates.[/*]
[*][b]Link[/b] — Nexus link (auto-generated from mod ID) or custom link.[/*]
[*]📂 — Opens the mod folder.[/*]
[/list]

[color=#0099ff][b]Features:[/b][/color]
[list]
[*][b]Search & Filters[/b] — Search by mod name, filter by separator, status (active/inactive/deleted), category, or custom tags. Empty separators are automatically hidden when filtering.[/*]
[*][b]Real-time auto-refresh[/b] — Auto-refresh is ON by default. Changes to mod order/separators/active state made in MO2 appear in the plugin within seconds. Uses a "light sync" mode that only reads modlist.txt (no meta.ini reads during polling).[/*]
[*][b]Priority Editing[/b] — Click the N° column to type a new priority number directly.[/*]
[*][b]Separator Colors[/b] — Click the 🎨 button on any separator to set a custom color. Mods under that separator get alternating shades of the same color.[/*]
[*][b]Sync from MO2[/b] — Reads meta.ini of all installed mods to update versions, comments, active state, and Nexus links.[/*]
[*][b]Update from CSV[/b] — Force-refreshes ALL data from the CSV file. Only preserves your Personal Comments and tags.[/*]
[*][b]Deleted Mods[/b] — Uninstalled mods appear in red with a × button.[/*]
[*][b]Profile Switching[/b] — Switch between MO2 profiles from the dropdown in the top bar without restarting MO2.[/*]
[*][b]Settings (⚙)[/b] — Change data source mode (csv/modlist) from a modal in the UI.[/*]
[/list]

[img]https://staticdelivery.nexusmods.com/mods/1704/images/187686/187686-1786154753-902447997.png[/img]
[img]https://staticdelivery.nexusmods.com/mods/1704/images/187686/187686-1786155115-1697282606.png[/img]

[b]Hide deleted[/b] - button on the Mod List tab
[img]https://staticdelivery.nexusmods.com/mods/1704/images/187686/187686-1786392832-527636563.png[/img]

[b][size=5]2. Deleted Mods Tab[/size][/b]

Isolates all mods whose folder no longer exists on disk from the main list. Stats, filters (search, separator, type), forget individual or bulk.

[b][size=5]3. Nemesis / Pandora / Custom[/size][/b]

[img]https://staticdelivery.nexusmods.com/mods/1704/images/187686/187686-1786154430-1375465437.png[/img]

Manages animation engine mods across three sub-tabs: Nemesis (auto-detect), Pandora (auto-detect), and Custom (manual entries). Editable tables, image uploads, persistent state.

[b][size=5]4. Backups[/size][/b]

[img]https://staticdelivery.nexusmods.com/mods/1704/images/187686/187686-1786154437-2132560168.png[/img]

Create and restore backups of your mod list and Nemesis state. View, Compare (side-by-side with synchronized scrolling), Restore, Delete. Collapsible separators in view and compare modes.

[img]https://staticdelivery.nexusmods.com/mods/1704/images/187686/187686-1786158898-892046983.png[/img]

[b][size=5]5. Plugins Tab[/size][/b]

[img]https://staticdelivery.nexusmods.com/mods/1704/images/187686/187686-1786323286-1554602989.png[/img]

Analyzes your load order by reading [b]plugins.txt[/b] and scanning mod folders for .esp/.esm/.esl files. Reads the binary TES4 header to detect ESL-flagged .esp files (ESPFE). Shows accurate stats on how many of the 255 plugin slots you are using.

[b][size=5]6. Versions Tab[/size][/b]

Lists all installed mods with their Nexus ID, File ID, version, mod link, and direct download links extracted from [b]meta.ini[/b]. This tab has [b]4 sub-tabs[/b]:

[size=4][b][color=#D9822B]Sub-tab: Mods[/color][/b][/size]
[img]https://staticdelivery.nexusmods.com/mods/1704/images/187686/187686-1789614655-985092009.png[/img]

Shows all installed mods with their version links. The table has 10 columns: Act, Mod, Nexus ID, File ID, Version, [b]Link[/b] (mod page on Nexus), Version Link (specific file download), Separator, Comment (editable), Actions (copy to custom).

[size=4][b][color=#D9822B]Sub-tab: Updated[/color][/b][/size]
[center][img]PLACEHOLDER_IMAGE_HERE[/img][/center]

Compares the current database against a backup (auto-backup or manual) and lists only the mods whose version has changed. Features:
[list]
[*][b]Auto-backup[/b] — A single [font=Courier New]auto_backup.json[/font] file is created automatically when you open the plugin. It is overwritten on each MO2 restart, serving as the baseline for comparison.[/*]
[*][b]Reference backup selector[/b] — Choose any backup (auto or manual) from a dropdown to compare against.[/*]
[*][b]Table with 8 columns[/b]: Act, N°, Mod, Old Version, Current Version, Mod Link, Old Version Link, Current Version Link.[/*]
[*][b]Separators[/b] shown as styled section headers (solid blue background, white bold text), only for sections that have updated mods.[/*]
[*][b]Filters[/b]: search by name, filter by separator.[/*]
[/list]

[size=4][b][color=#D9822B]Sub-tab: Custom[/color][/b][/size]
[img]https://staticdelivery.nexusmods.com/mods/1704/images/187686/187686-1789614654-179202609.png[/img]

Manually add entries for specific mod versions. Live URL preview, editable comments, double-click to edit file IDs.

[size=4][b][color=#D9822B]Sub-tab: Backups[/color][/b][/size]
[img]https://staticdelivery.nexusmods.com/mods/1704/images/187686/187686-1789614659-2025048654.png[/img]

Create, view, restore, and delete backups of version data (mods list and custom list).

[line]
[b][size=5]7. Traduction Extension[/size][/b]

[img]https://staticdelivery.nexusmods.com/mods/1704/images/187686/187686-1790388133-1040877170.png[/img]

When installed, adds a [b]"Traducciones"[/b] tab with translation classification (TR/DSD/MCM/SC/SK/OT/NO), auto-detection, and a "Trad" column in the Mod List. Fully self-contained with its own data storage and backups.

[b][u][color=#00ff00][size=5]Extension Installation[/size][/color][/u][/b]
[list=1]
[*]Install Modlist Manager v4.0+[/*]
[*]Copy [font=Courier New]modlist_manager_traduction.py[/font] to [font=Courier New]plugins\[/font][/*]
[*]Copy translation JSONs to [font=Courier New]translations\[/font][/*]
[*]Restart MO2[/*]
[/list]
[line]

[b][size=5]8. Import / Export[/size][/b]

[img]https://staticdelivery.nexusmods.com/mods/1704/images/187686/187686-1786154447-2014193244.png[/img]

Export your mod list or Nemesis state as JSON. Import from another profile/machine with preview and side-by-side compare.

[size=5][b]Plugin Settings (in MO2)[/b][/size]

[list]
[*][b]auto_open_browser[/b] — Automatically open the browser when the plugin starts (default: true)[/*]
[*][b]start_on_mo2_startup[/b] — Start the web server when MO2 launches (default: false)[/*]
[*][b]web_server_port[/b] — Web server port, 0 = auto (default: 0)[/*]
[*][b]data_source[/b] — 'csv' or 'modlist' or '' (ask on first launch)[/*]
[*][b]debug_enabled[/b] — Debug logging to [font=Courier New]modlist_manager_debug.txt[/font], cleared on each MO2 restart (default: false)[/*]
[/list]

[size=5][b]Data Storage[/b][/size]

[font=Courier New]<profile>\ModlistManager\[/font] — database.json, memory.json, nemesis.json, collapse_state.json, backups/ (manual + auto_backup.json), images/, version_backups/, custom_versions.json, version_comments.json

[size=5][b]Languages[/b][/size]
[list]
[*]Spanish[/*]
[*]English[/*]
[*]Easily extensible — just copy [font=Courier New]modlist_manager_es.json[/font] to [font=Courier New]modlist_manager_<code>.json[/font][/*]
[/list]

[size=5][b]Shout Outs[/b][/size]
[list]
[*][b]AI Agent (Z.ai / GLM)[/b] — Built through conversation with an AI agent.[/*]
[*][b]64Saratov[/b] — Bug reports for non-standard MO2 paths and Russian translation.[/*]
[*][b][url=https://www.nexusmods.com/skyrimspecialedition/mods/186942]FOMOD DB Explorer[/url][/b] — Structural template.[/*]
[*][b]Everyone who tests and reports bugs[/b] — Your feedback helps us improve.[/*]
[/list]

[line]
[size=5][b]Changelog[/b][/size]

[b][size=5][color=#ff7700]Version 6.0.0[/color][/size][/b]

[b]Changes from 5.0.9 to 6.0.0 (all changes compressed as one release):[/b]

[b]New Features[/b]
[list]
[*][b]Version Updates sub-tab[/b] — New sub-tab in the Versions tab (between Mods and Custom) that compares the current database against a backup and shows only mods whose version changed. Columns: Act, N°, Mod, Old Version, Current Version, Mod Link, Old Version Link, Current Version Link. Filters: search by name, filter by separator. Separators shown as styled headers.[/*]
[*][b]Auto-backup on startup[/b] — A single [font=Courier New]auto_backup.json[/font] is created when you open the plugin, overwritten on each MO2 restart. Serves as the baseline for the Version Updates comparison. Old timestamped auto-backups are cleaned up automatically.[/*]
[*][b]Link column in Versions/Mods[/b] — Added a Link column between Version and Version Link, showing the mod's Nexus page URL for quick access.[/*]
[*][b]Profile switching without restart[/b] — Select any profile from the dropdown in the top bar. The plugin recreates its reader/store/api on the fly.[/*]
[*][b]Settings modal (⚙)[/b] — Change data source mode (csv/modlist) from the plugin UI. Automatically deletes database.json and reloads with the new mode.[/*]
[*][b]Batch collapse API[/b] — "Collapse all" and "Expand all" now use a single batch API call ([font=Courier New]/api/collapse_batch[/font]) instead of N individual calls, fixing a race condition that caused the collapse state to be lost.[/*]
[/list]

[b]Performance & Optimization[/b]
[list]
[*][b]Light sync polling[/b] — Auto-refresh only reads modlist.txt (no meta.ini reads during polling). Polling is nearly instantaneous even with 3000+ mods. Interval: 3s (≤1000 mods), 5s (1001-2000), 8s (>2000).[/*]
[*][b]meta.ini cache[/b] — Repeated reads of the same mod in a session are cached by (mtime, size).[/*]
[*][b]categories.dat cache[/b] — Cached to avoid re-reading on every sync.[/*]
[*][b]Profile list cache[/b] — Cached by directory mtime; only re-scans when the profiles directory changes.[/*]
[*][b]Debug log cleanup[/b] — Single file [font=Courier New]modlist_manager_debug.txt[/font], cleared on each MO2 restart. Removed the old daily rotation that created 30+ files. Removed the [font=Courier New]debug_rotation[/font] setting.[/*]
[/list]

[b]Bug Fixes[/b]
[list]
[*]Fixed profile switching reverting to MO2's current profile — auto-follow disabled in polling; the plugin detects MO2's profile on startup but lets the user switch freely afterward.[/*]
[*]Fixed non-standard MO2 paths — profiles root, mods directory, and overwrite path now use [font=Courier New]organizer.profile()[/font], [font=Courier New]organizer.modsPath()[/font], and [font=Courier New]organizer.overwritePath()[/font] instead of assuming [font=Courier New]basePath()/profiles[/font] and [font=Courier New]basePath()/mods[/font]. (Reported by 64Saratov)[/*]
[*]Fixed settings tooltips appearing in English before translations load — lazy-load translations on first [font=Courier New]_tr()[/font] call. (Reported by 64Saratov)[/*]
[*]Fixed DLC detection — DLCs now detected by the [font=Courier New]*[/font] prefix in modlist.txt (not by name patterns). In CSV mode, detected by [font=Courier New]"Creation Club:"[/font] and [font=Courier New]"DLC:"[/font] prefixes. No more false positives on mods like "All in one Address Library (Anniversary Edition)".[/*]
[*]Fixed separator detection — Only the [font=Courier New]_separator[/font] suffix indicates a separator. The [font=Courier New]_[/font] prefix no longer triggers false positives (e.g., [font=Courier New]_Fuse00_ArmorRagnar_Vanilla[/font]).[/*]
[*]Fixed [font=Courier New]meta.ini[/font] comments with quotes — MO2 wraps values containing spaces or special characters in double quotes; [font=Courier New]configparser[/font] does not strip them. Added [font=Courier New]_strip_meta_quotes()[/font] to clean all fields.[/*]
[*]Fixed collapse state lost on polling — local hash is synchronized after collapse/expand operations.[/*]
[*]Fixed empty separators showing when filtering — separators with no matching mods are now hidden during search/filter.[/*]
[*]Fixed separator rows not collapsible in backup view and compare modes — added click event delegation.[/*]
[*]Fixed [font=Courier New](actual)[/font] profile indicator following the plugin's selected profile instead of MO2's actual profile.[/*]
[*]Fixed auto-backup creating files in the wrong profile ([font=Courier New]\Default\[/font] instead of the active profile) — moved creation from [font=Courier New]init()[/font] to [font=Courier New]_start_server()[/font].[/*]
[*]Fixed [font=Courier New]refresh_from_mo2()[/font] NameError on new separators (indentation bug).[/*]
[*]Fixed [font=Courier New]/api/profiles[/font] and [font=Courier New]/api/switch_profile[/font] returning HTTP 500 — Api class now has a reference to the plugin instance.[/*]
[*]Fixed column N° not centered — [font=Courier New]text-align: center[/font] with padding on both [font=Courier New]th[/font] and [font=Courier New]td[/font].[/*]
[*]Removed dead code: [font=Courier New]is_dlc_name()[/font], [font=Courier New]DLC_PATTERNS[/font], [font=Courier New]DLC_EXACT_NAMES[/font], [font=Courier New]_generate_from_modlist_txt()[/font].[/*]
[*]Debug messages translated to English (were in Spanish regardless of language setting).[/*]
[/list]

[b]New Translations[/b]
[list]
[*]28 new i18n keys added (ES + EN): version updates sub-tab, settings modal, profile switching UI, auto-refresh, etc.[/*]
[*]Total: 349 keys per language.[/*]
[/list]

[b]Compatibility[/b]
[list]
[*]Existing [font=Courier New]database.json[/font] and [font=Courier New]memory.json[/font] are preserved across the upgrade.[/*]
[*]The extension plugin ([font=Courier New]modlist_manager_traduction.py[/font] v3.0) is fully compatible.[/*]
[*]GPL-3.0 license — permission granted to 64Saratov to publish Russian translation and patched builds on gamer-mods.[/*]
[/list]

[size=5][b]Known Issues / Limitations[/b][/size]
[list]
[*][b]Server timeout[/b] — Shuts down after 5 minutes of inactivity. Reopen the plugin or click "Retry connection".[/*]
[*][b]Renaming mods in MO2[/b] — Plugin sees it as deleted + new mod (identifies by folder name).[/*]
[*][b]Pandora[/b] — Auto-detection implemented but not extensively tested.[/*]
[/list]

If you encounter bugs, have feature requests, or want to contribute translations, please leave a comment or post in the bugs tab.

I left this in Skyrim SE since it has only been tested with lists from this game; I don't know if it will work in other games.
