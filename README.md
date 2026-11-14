# Azeroth Atlas · WoW Forever Companion

A compact German-language fan companion for WoW Forever with builds and talent progressions, multiple characters, loot wishlists, dungeon and farming recommendations, and a session planner.

**Live site:** https://derb3rt.github.io/azeroth-atlas/

## Features · Companion 2.0 (2026-11-14)

- **Build library + talents:** 9 classes, level slider, offline Forever talent snapshots and optional updated community talent data.
- **Character manager:** multiple profiles, separate levels, factions, builds, professions, personal notes, manual talents, equipment text fields and loot wishlists.
- **Smart Loot Advisor:** curated dungeon drops with per-role and level heuristics, wishlist, obtained progress, source labels and manual equipment tracking.
- **Dungeon Companion:** dungeon selection with level and faction filtering, entrance and quest hints where documented, boss-level loot grouping and wishlist interaction.
- **Interactive farming map:** clickable schematic zone markers on Eastern Kingdoms / Kalimdor, level/material filters and a link to schedule a farm into the session planner.
- **Build comparison:** compare two builds of the same class, their level-scaled talent distribution and editorial solo/dungeon rotations, stat priority and professions.
- **Session planner:** 15–120 minute flexible plans for XP, loot, dungeons, professions or gold with checkable steps and per-character progress.
- **Local backup:** the original JSON backup now includes new profiles and is compatible with previous backups (schema 1).

## How it works

Static site: `index.html` + `assets/features.js` + `assets/features.css`. No framework, installation, account, API key, analytics or backend.

Azeroth Atlas stores user data only in browser `localStorage` with two separate keys:
- `azeroth-atlas-v1` for the original app state and historical build presets
- `azeroth-atlas-companion-v2` for profiles and new functions

**Privacy:** There is no cross-device synchronization. To move between devices, use the JSON backup under **Meine Notizen**. Browser storage can be cleared by browser maintenance.

## Source quality and boundaries

The curated loot index is a **shortlist**, not a complete item database. There are no independently measured item DPS values, drop rates or Gold/hour estimates. Score labels use *heuristics only*: role fit, distance to character level and dataset source.

- "Forever-Community" means a Community guide or beta dataset associates the item with Forever; verify details against your current in-game Dungeon Journal and tooltip.
- "Classic-Referenz" means the item and/or drop source may have changed on Forever and is **not confirmed**.
- Schematic farming pins are approximate **zone positions**, not spawn coordinates or navigable GPS routes.
- Level-scaled talent allocations derive from community level-60 presets and a planner heuristic; they are not simulator rankings.
- All advice is contextual and may change with hotfixes. No live game-character data is fetched.

Public sources consulted 2026-11-14:

- [Eternadex WoW Forever database](https://eternadex.com/en/datenbank/) — publicly described as client build **1.60.1.70938, 2026-11-13**. Links to item details and upgrade finder; no undocumented API use.
- [Foreveroth dungeon loot](https://foreveroth.com/en/donjons/) — boss/item listings, including early Forever dungeons.
- [Wowhead Ruins of Lordaeron walkthrough](https://www.wowhead.com/news/the-ruins-of-lordaeron-new-dungeon-walkthrough-for-wow-forever-383021) — beta quest and dungeon orientation.
- [Mobalytics Hall of Thanes guide](https://mobalytics.gg/wow-forever/dungeons/the-hall-of-thanes-dungeon-guide).
- [forever-xp community talent snapshots](https://github.com/Jweyant/forever-xp) — offline talent snapshot in the base app is version 1.60.1.70888; the base app also attempts to load the repository's latest available talent JSON at runtime.

This is an independent fan project, not affiliated with Blizzard Entertainment.

## GitHub Pages

Publish from **main / (root)** under `Settings → Pages → Build and deployment`. Main entrypoint is `index.html`.

## Testing

Validated in headless Chromium on 2026-11-14 with offline resources and an isolated localStorage shim:

1. All twelve page tabs render without JavaScript exceptions.
2. Create a second character, switch profiles, change levels and retain independent loot wishlists/equipment on reload.
3. Cross-class talent and comparison screens render for all nine classes.
4. Dungeons show tracked bosses/loot; all filters and farming map markers work.
5. Session planner sums exactly to selected time budgets, does not schedule full dungeons for 15/30-minute sessions, and persists completed steps.
6. Mobile viewport 390px renders map without document-wide horizontal overflow.

These are browser smoke tests, not a full in-game verification of WoW Forever drops, skills, or hotfixes.