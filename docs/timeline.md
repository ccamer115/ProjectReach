# Timeline

The first battle sim ran on 1 September 2026; this page lists every numbered build since then, one line each.

All dates are 2026. A build named with a suffix (`_1`, `_2`) is a smaller follow-up build on the one before it; a letter (a, b) means one planned build was split in two.

## September

### 1–6 September: the first battles

| Build | Date | What it added |
|---|---|---|
| V2 | 1 Sep | The first battle sim, built and played: a top-down fight over a planet. Its station-defence battle became the yardstick every later balance change was measured against. |
| V4 | 2–3 Sep | Weapon hardpoints, real projectiles, damage by hull section, a shared crew pool, six visual effects, a super capital, saved reference battles to catch regressions, and a five-tier test system. |
| V5a | 4 Sep | The code split into a pure simulation and a separate display layer; ships, weapons and scenarios became data files; real scale (fleet sizes span 400:1); architecture rules checked by tests. |
| V5b | 4 Sep | Battle replays you can scrub through, ships that withdraw, click-to-select ships with a detail panel, a new capital ship, and ship interiors with crew that appear as you zoom in. |
| V6 | 4 Sep | Crew who walk the corridors, a planet whose gravity can drag a crippled ship down, a pre-battle build phase, and fleet command (box select, orders, control groups). The project took its current name. |
| V6_1 | 4 Sep | You choose where each purchase goes on the hull; armour and shield modules can be shot off; ships arrive out of hyperspace with a streak and flash. |
| V6_2 | 4 Sep | A turret picker with seven guns, optional hangar bays and slipways, a bigger build budget, and a measured look at frame-rate drops. |
| V7 | 4 Sep | Artillery platforms, an area-damage nuke and homing swarm missiles, projectiles visible at every zoom, and the first galaxy map (24 worlds, 42 lanes). |
| V8 | 5 Sep | Sound (35 synthesised effects with a mixer), factions and resources on the galaxy map, and a first "massive battle" scenario. |
| V11 | 5 Sep | A performance pass: targeting about three times faster, draw calls cut from 1,664 to 329 for the same picture, and an on-screen cost readout. |
| V12a | 5 Sep | The strategic layer: worlds, lanes, credits and enemy fleets on a clock; battles start from the galaxy with a visible approach, jump and staggered arrival. |
| V12b | 5 Sep | The simulation moved off the render thread; a first economy (supply, growth, income); hazards and planetary defences as terrain. |
| V13 | 6 Sep | Crew aboard idle ships walk their rounds through real doorways (a bug fix), plus a consistency check for the battle record. |
| V14 | 6 Sep | The world never pauses: battles and the economy run whether you watch or not; survivors raid or retreat; planets get building slots and three resources that shipbuilding spends. |
| V15 | 6 Sep | A flight recorder for every battle, placing several items at once, and fleet orders (hold on a leash, or move). |
| V16a | 6 Sep | The groundwork for planets: the rules between the space and surface layers, and a generated hex surface map. |

### 7–13 September: planets, art and better flying

| Build | Date | What it added |
|---|---|---|
| V16b | 7 Sep | The planet surface view and its colony loop, linked to the space layer (built overnight, unattended). |
| V16b_1 | 7 Sep | A crash fix (two threads reading the same data) and orbital bands around planets. |
| V17 | 7 Sep | Fixes from a play session, flak guns, swarming craft, a battle log and jump points. |
| V18 | 7 Sep | A round battle area, cruise travel, a new HUD and the first pipeline for ship sprites. |
| V19 | 8 Sep | Ships turn and fly more naturally, the off-screen battle resolver rewritten, and a planet-surface test bench; built by four agents in parallel. |
| V19_1 | 9 Sep | A review pass: separation fixes, readable zoom text, and the AI made about three times faster. |
| V20 | 10 Sep | The approved ship art replaces the placeholder shapes. |
| V21 | 10 Sep | About 45 files fixed so everything works with the new art. |
| V22 | 10 Sep | A hull-authoring tool and collision outlines for every ship. |
| V23 | 11–13 Sep | Collision follows the real hull shapes; bombers restored; movement fixes. |
| V24 | 13 Sep | A bigger hand-built battle area, short jumps inside a system, combat postures, and a zoom that changes how ships are drawn as you pull out. |
| V25 | 13 Sep | Asteroids, moons and other scenery as their own object type, and the first hand-built star system. |

### 14–20 September: one zoom from galaxy to hull

| Build | Date | What it added |
|---|---|---|
| V26 | 15–16 Sep | One continuous camera from a whole star system down to a single hull; the first fully green test run since V20. |
| V27 | 16–17 Sep | A generated galaxy (40 systems, about 148,000 bodies) with one continuous zoom from galaxy to system, plus a combat test bench with photographed gun mounts and new weapon classes; then a fix that cut zoom lag from 130 ms to 9 ms a frame. |
| V28 | 17 Sep | Planets become economic hubs: population, buildings, storage, capital tiers and an economy panel. |
| V29 | 18–19 Sep | The project goes under version control; a quick and a full test pass with a log of every check; two parallel combat branches merged. |
| V30 | 19 Sep | Weapons get sizes and types, twin guns fire from their real muzzles, the interface gets a design system, and a first refit screen. |
| V31 | 19–20 Sep | Every ship carries the guns and effects from its approved art package, and the galaxy zooms all the way down to a ship. |

### 20–28 September: a living galaxy

| Build | Date | What it added |
|---|---|---|
| V32 | 20–21 Sep | A civilian layer: 16 unarmed ship types flying 40 trade loops, and ship art memory cut by three quarters. |
| V33 | 21–22 Sep | Every code-drawn stand-in replaced by approved art; four named worlds; warp points and trade routes; stations and patrols. |
| V34 | 22–23 Sep | Safety checks that trip on bad changes first, rules for the star-system generator, building placement rules, and weapon charge-up art. |
| V35 | 23 Sep | Guns that read like the movies, point defence that guards against strike craft, torpedoes, and limited ammunition. |
| V36 | 24 Sep | Shields as a single pool, damageable modules and engines, blasts and friendly fire, solid stations, and a galaxy map you can read at a glance. |
| V37 | 26 Sep | Tougher hulls, retreats that end at a jump zone, targeting by kill value, stances and fleet focus fire; the first build on the new reference PC. |
| V38 | 27–28 Sep | A planet screen, a constructor ship that builds stations, the first outpost, duels that always end, and tests running in parallel. |

## October

### 1–5 October: building and fog of war

| Build | Date | What it added |
|---|---|---|
| V39 | 1–2 Oct | Building placement with a ghost preview and a confirm step, stations that fill in as they build, tier upgrades, and shipbuilding queues. |
| V40 | 3 Oct | The Covenant joins the main game, three kinds of shipyard build ships, art packages swap in without code changes, and the first sensor fog. |
| V41 | 4 Oct | Fog of war, second pass: steady sensor rings and a sight range for every ship class. |
| V41_1 | 4–5 Oct | The nuke drawn end to end from its art package, nebulae that block sight, and aggressive, defensive and passive engagement choices. |

### 9–11 October: fleets become real

| Build | Date | What it added |
|---|---|---|
| V42 | 9 Oct | Test tooling that sorts known failures from new ones, and an owner recorded on every ship and station. |
| V43 | 10 Oct | Fleets as real records, flak against strike craft, and a lighter test mode for in-between builds; combines four small builds from 9 Oct. |
| V44 | 10–11 Oct | A new fog look, larger asteroid fields, fleets you can click and build into, and real fighters (switched off for now); built overnight by a lead and four parallel agents. |
| V44_1 | 11 Oct | The approved "moderate haze" fog look becomes the default. |

### 11–18 October: fighters, deaths and new warships

| Build | Date | What it added |
|---|---|---|
| V45 | 11–12 Oct | Fleets move as one; fighters launch from real hangar bays; start placement; a station panel; new asteroid art and shot sounds; the first full-length test run. |
| V46 | 12–14 Oct | A smooth zoom transition between galaxy and system, 22 new warships from their art packages, new stations and a UNSC start, faction relations, and a new interface theme. |
| V46_1 | 14 Oct | Covenant fighter and bomber hit shapes from the artist, and a fix for fleet orders that pointed outside the arena. |
| V47 | 15–16 Oct | Ship deaths and break-up, fleet markers on the galaxy, admirals, hangars, an interdictor ship, faction shields, engine glow, new UNSC guns, and the art library reorganised (12,245 files); built by a lead and nine helpers. |
| V47_1 | 16–17 Oct | Shields block everything until they break, UNSC battery fire staggers, and tests run side by side (the quick pass in 2 h 24). |
| V48 | 17–18 Oct | Save and load, salvage, swarming strike craft, cruise travel, more admiral work, and nine UNSC stations; eight experiments folded into one build. |

### 18–26 October: a playable start

| Build | Date | What it added |
|---|---|---|
| V49 | 18–19 Oct | A fixed start flow with a starting destroyer, a demo map, morale, an armed Covenant fleet, tugs, and interface and sound work from play notes. |
| V50 | 20–21 Oct | One range system every weapon uses, a weapon table, hold-fire, galaxy saves, planets and world names on the galaxy, battle aftermath, and sound levels. |
| V51 | 23–24 Oct | A main menu (Start, Load, Settings, Tests), CIS hulls that fracture, wreck debris at every zoom, targeting by firepower, and one table of ship stats. |
| V52 | 25–26 Oct | Ships collide, hold formation and attack-move; micro-jump travel; a buildable interdictor; nukes on capitals; a junkyard for wrecks; pirates and an AI high command. |

### 27 October–1 November: one game across every zoom

| Build | Date | What it added |
|---|---|---|
| V53 | 27–29 Oct | A Sandbox balance bench in the main menu, tougher pirates, named saves, and a memory guard for test runs after a PC crash. |
| V54 | 29–30 Oct | New combat numbers, a siege plasma cannon, new shot effects, jump bug fixes, a stats page and playbook in the Sandbox, and texture streaming. |
| V55 | 30–31 Oct | Facing and route jumps, right-click jump and queued orders, guard and screen orders, fire lanes, ship roles, and new death effects; the full test sweep was stopped and a core set run instead. |
| V55_1 | 31 Oct–1 Nov | Galaxy and system play as one game: the same orders, keys and clock in both views, and a fleet queue that crosses systems; shots land on the drawn shield; a lean core test run becomes every build's standard. |

## November

| Build | Date | What it added |
|---|---|---|
| V56 | 1–2 Nov | Standing guard and screen tasks, fleets that keep pace, orders into a system you are watching, a new default HUD, new impact and fire effects, ion guns, point defence against missiles, and a shot-scale tuning page. |

## Notes on the numbering

- **V1 (1 Sep):** the first prototype (eight ships, one beam weapon, placeholder shapes). It has no build record, so it is not in the table.
- **V3:** a real build between V2 and V4, but no surviving record gives its date, so it is not in the table.
- **V2's date:** V2's own build record is not on disk; its 1 September date comes from the project's later records.
- **V5:** built as two halves, V5a and V5b (both in the table).
- **V9 and V10:** never existed as builds. The numbering jumped from V8 to V11 so build numbers and document numbers could match from then on.
- **V12:** split into V12a and V12b by its own plan (both in the table).
- **V16:** not a separate build; it was V15 with the V16a groundwork applied.
- **The V27 zoom fix (17 Sep):** a same-day fix, folded into the V27 row.
- **Four small builds (9 Oct):** combined into V43 rather than listed on their own.
- **Experiments:** about thirty trial builds were tried on the side and folded into numbered builds; they are not builds themselves.
- **Version history:** before 18 September each build kept its own history inside its archive; the PC's current version history starts there (V29).

## Totals

| | |
|---|---|
| Numbered builds | **64** dated builds in the table, V2 to V56, counting every follow-up (`_1`, `_2`) and split (a, b) build separately; 65 with the undated V3 |
| Commits | **289** across all branches at the V56 commit |
| Test battles | **2,283** since 16 October, when the battle counter was added |
| Shots fired in those battles | **20,982,453** |
| Ships destroyed | **4,763** (not counting fighters and bombers) |
| Fighters launched | **287,813** |
| Hand-written code | **about 503,000 lines** (game code, tests and tools) |
