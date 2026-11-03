# V56 phone brief (2 Nov 2026)

*A real project document, lightly edited for privacy. Internal file names and IDs are left in to show the record-keeping; the files themselves aren't public.*

V56 is the sixth build, on V55_1: a lead agent, ten helper work streams and follow-ups, built overnight from the build's kickoff. Everything in it is fiction (a video game).

## 1. What to play first
- **`PLAY_V56.bat`** opens the main menu: Start, Load, Settings, Tests, Sandbox, Quit.
- **The A UI.** Start your faction and select a ship. The dock along the bottom shows its picture, its SHIELDS and HULL bars and its task. Pick **Guard** or **Screen** from the Escort dropdown (it reads [pending], then [accepted]), then deselect and reselect: the task is kept. Inspect works in both views. The ribbon shows your stocks; the report bar is top right, collapsed.
- **Orders.**
  - Select a fleet on the galaxy map, zoom into another system and right-click a spot: one order, the trip plus that point.
  - Press X while a fleet is charging a micro-jump: the charge stops, in both views.
  - A plain click during a galaxy trip replaces the trip; Shift adds to the queue.
- **The Sandbox (main menu):**
  - **Bodyguard vs Raider:** eight Paris with an Epoch. Bodyguards hug the Epoch and read "Guarding Epoch". Raiders take no guard; they move with the fleet until in range, then swarm (Tests row `plays_differ`).
  - **A mixed fleet arriving together** (Tests `fleet_pace`): the fleet closes at its slowest ship's closing speed.
  - **The Subjugator:** the ion ring fires from its side, the ship turns its side to the target when the cannon is charged, and there are no blue engine circles (Tests `v56_ion_broadside`; the first ion shot comes at about 50 s).
  - **Archers vs PD:** PD now shoots Archers (Tests `cf_point_defence`).
  - **A siege shot with fighters crossing the fire:** impact A and three 15 s fire zones that burn strike craft (Tests `v56_siege_impact`; place fighters yourself, as the bench has none).
  - **The far view:** heavy shots stay as glows, nuke brightest (Tests `v56_far_glows`).
  - **The stats page (F10) → SHOTS:** one k slider per gun family (0.25–1). Shots a second ×k, damage a shot ÷k, damage per second unchanged. The crowding line shows live shots, shots on screen and shots fired a second.
- Then the review questions (§9) and the clips in the review folder.

## 2. The commit and the result
- **Committed 00be2656 on `gate/v56`**, branched from `gate/v55_1` (20a822ba). Not pushed; main untouched (yours to move).
- **B13 (`./ci/verify.sh --core`):** `VERIFY: FAIL (point build: core) - 171 checks and 184 controls ran, 56 controls skipped as unchanged, 14 red section(s), 7859 s`.
- **Run time: 2 h 11** against V55_1's 1 h 57. V56 added 49 rows (every new gauge) to the lean list.
- **After B14:** ten of the fourteen fixed or re-aimed; the targeted re-run (88 sections, 35 min) had only TIER 4 §15.11 red. Left: TIER 4 §15.11, SPRITE, RULE6 (all known) and RESOLVE (your call, as on V55_1).
- **Records commit** 82f5178e (the brief, state, post-commit hashes); B16's commit follows (hash in `V56_DONE.txt`).
- **Fun stats:** refreshed 04:04, about 503,000 lines of hand-written code, 2,283 battles counted.

## 3. The master list

Kickoff §1, in its order. Status: **done**, **partly**, or **not**. "Both views" = the galaxy map and the system view act the same (Rule 10).

### Costa's 12 rulings
1. **Guard and Screen, either-or, standing tasks** — **done**.
   - The dropdown (Escort: Guard / Screen / Off) is `ui_a_v56`; the standing tasks, spread and close station are `guard_standing_v56`, `guard_spread_v56`, `guard_close_v56` (all ON).
   - Task kept after deselect and after a fleet move. Default guard re-posts. Screen covers the fleet. Guard then a ship click is never moved by the spread.
   - Views: sim rule, same in the system view and on the resident board the map keeps. **Gap:** the unwatched (coarse) board does not run the standing step, spread or first post (G-V56-GUARD-1). The chart's Guard and Off refuse with a reason (GAP-UICORE-2). An explicit task does not survive a jump (G-V56-GUARD-5).
2. **A guarded fleet moves at its slowest ship's pace** — **partly**.
   - `fleet_pace_v56` (fine model) and `coarse_pace_v56` (zoomed-out model), both ON. Printed fit: watched 96 s, unwatched 100 s, ratio 1.04 (V55_1: 54 s, ratio 0.56).
   - **Not done:** RESOLVE not re-aimed (D-V56-14, left red as in V55_1); the `FIT_UNDER` stamp (18,000 u) untouched (G-V56-GUARD-2). Clip 4 cannot tell pace ON from OFF (F-V56-STILLS-4).
   - Views: both (pace in the fine model and the coarse model).
3. **Order a fleet into a system you're looking at** — **done**, both views.
   - `remote_order_v56` ON. System-view right-click with the chart's fleet selected = trip plus that exact point (Shift appends). Chart planet right-click = jump point and hold. Same plan from either view (SAMEPLAN, 0.00 u apart).
   - Note: acts only when no hull of yours is selected on that board (D-V56-ORDERS-01). The System View's own jump-point pick is unchanged (GAP-V56-ORDERS-6).
4. **X cancels a charging jump; a plain click replaces a galaxy trip; Shift queues** — **done**, both views.
   - `stop_charge_v56`, `trip_replace_v56` ON. Gauges STOPCHARGE, TRIPREPLACE.
5. **Clicks don't follow the hit shake** — **kept** (V55_1 already does it). No V56 change and no V56 gauge (not recorded as re-checked).
6. **A loaded save keeps its pause** — **kept** (V55_1's). No V56 change (not recorded as re-checked).
7. **Far-zoom glows** — **done**, `far_glows_fx14` ON (six types, nuke brightest, fog respected, no crowd dimming; R2 steady, Round 6 centred backlight; no R4).
   - Views: system view far zoom only. The map draws no shots, so nothing to show there (G-V56-FX14-G1).
   - Only the generic bolt sprite cross-fades into the glow; plasma head, siege comet and Archer glow keep the hard cut at 0.35 (G-V56-FX14-G2). Clip 9 is weak.
8. **"Fewer, heavier shots"** — **tool done, numbers are yours**.
   - `tune_bench_v56` ON: SHOTS tab on the Sandbox stats page, one slider k (0.25 to 1) per gun family, shots a second x k, damage a shot / k. PD, flak, MACs and nukes are left out. Crowding readout. Nothing is written to game data (NOKEEP2).
   - Views: Sandbox bench page (n/a: bench). The numbers wait for your tuning session (G32).
9. **The A UI (A over B and C, compact M11 queue, four faction examples)** — **partly** (built in the kickoff's order; gaps below).
   - UICORE (`ui_a_v56`, ON): faction framing from LIGHT tokens, resource ribbon, command dock, bars and picture, Guard/Screen dropdown, capability-driven controls, text 9-12 px and buttons 28 px+, Inspect. Both views.
   - UIBUILD (`ui_build_v56`, ON): build flow, M07 to M10 cards, the M11 tray (472 x 132) and the overview (176 x 132). **System view only** (GAP-UIBUILD-1: the game has no site building on the map).
   - UIREPORTS (`ui_reports_v56`, ON): report and contact bars, collapsed 320 x 52. Both views. Contacts are live; **allied operations not built** (no record exists, GAP-UIREPORTS-1); objectives, payouts and NPC messages are a labelled Tests preview only.
   - **Not built:** an "Attack..." button (no arm-attack command exists, GAP-UICORE-4). The planet-surface view keeps V55_1's chrome (GAP-UICORE-9). No keyboard route for the report bar (GAP-UIREPORTS-2).
10. **Today's accepted Astra art** — **done**, one part not ON.
    - N01's eight packages: bound and sha-checked. Beam contact (in the FX-07 package) stays **OFF**, no match. See §5.
    - FX-14 A/B: impact A, three 15 s fire zones, far glows: ON.
    - FX-14 Part C: matched all six stills, ON, replaces the purple `impact_b`. Reads real contact events (weapon, receiver, shield or hull). Clip 10 is weak: the hit is hard to see on film.
11. **The 12 px draw-size rule (R-ZL-1)** — **done**, `draw_min_12_v56` ON (`weapon_art_min_px` 12; V55_1's 2.0 kept beside it). Views: system view draw (n/a on the map).
12. **Bugs from your play:**
    - Bodyguard and Raider acting alike — **done** (`play_beats_default_v56`, `raider_picket_v56`). Cause: V55_1's default guard is an order, and an order beats a play. Raider "pull back when it can't do damage" is only V54's shield pull-back (G-V56-GUARD-3). Hunter also yields the default guard: confirm (G-V56-GUARD-R1).
    - Bench shields recharging fast — **done** (`bench_battle_v56`). Cause: the game's 60 s hit timer, not the rate; a bench ship nobody hit for a minute refilled 10x faster. A number you edit on the bench stays absolute and is forgotten on close.
    - Old engine glow — **done** (`no_flare_v56`). Nothing drawn instead (Rule 5). CIS and Republic hulls without Astra plume anchors now draw no engine (G-V56-ASTRABIND-R1; Astra ask 1).
    - No damage marks on the Subjugator — **not fixed, no art**. Only 10 hulls have DMG-01. The list for Astra is made, Subjugator first (G-V56-ASTRABIND-5; Astra ask 2).
    - Citadel turning 90 degrees when placed — **done** (`citadel_rot_v56`). Sandbox placer; the other 93 palette hulls keep their heading.
    - Projector beams stopping short — **done** (`beam_reach_v56`). Cause: not the sim; the drawn lance faded while the round was still flying. Presentation only, no hash event.
    - Map hover stutter — **done** (`map_nav_v56`, gauge HOVERZOOM prints a frame-time trace). Chart only.
    - Huge HUD after a monitor move — **partly**. A scale watcher recomputes on size, monitor, DPI and scene change (UIASCALE). **The bug itself was not reproduced** (GAP-UICORE-1); your screenshot fits a saved 2x on a widescreen. A "follow the monitor" scale is your call.
    - Archers PD can't stop — **done** (`archer_pd_v56`; 50 hit points, damage x0.5, both guesses). Sim, every fine-tier battle. The coarse tier does not model Archers being shot down (G-V56-COMBATFIX-3). Clip 15 is weak.
    - Covenant pulse laser not PD — **done** (`pulse_pd_v56`). Hash event E-PULSEPD-V56-1 (tyrant). Side effect: the Kerel and SDV now count as PD ships and default-guard their fleet's biggest ship (COV-08 question, G-V56-GUARD-R2).
    - Bodies card blocking clicks — **done** (`card_fix_v56`, gauge CARDCLICK). Hover only, never sticks, lists stations, names the body. Chart only.

### Also in the kickoff blocks
- Map G, J, Shift+F (G8) — **partly**: `map_keys_v56` ON. J and Shift+F done. The chart's G works for two fleets **in the same system** only (GAP-V56-ORDERS-1).
- Map fixes F3, F4, F9 — F4 done (wheel on a fleet marker opens the system). F3 **partly**: panel proven, the banner not reproduced headless (GAP-V56-ORDERS-4). F9 (`watch_covenant_hc`) handed to the Tests list (GAP-V56-ORDERS-2, closed).
- Fleet card shows each ship's task — **not** on the map card (GAP-V56-ORDERS-3); the dock shows it.
- Ion guns ON + broadside (G20) — **done**, `subjugator_ion_fx12` and `ion_broadside_v56` ON. Both tiers (watched turns the side; unwatched counts the ion mount only when the hull can bear). Hash event: none seen (no fixture carries a Subjugator). Ring EMP contact arcs not ported (G-V56-ASTRABIND-1).
- Canopies (Citadel, two v6 pirate platforms) and three station colliders — **done**, ON. Canopies proved by data, not a pixel match (G-V56-ASTRABIND-6).
- Hull heat — **done**, ON by G19 (reads about 1.6x Astra's brightness, inside her bar; your eye, G-V56-ASTRABIND-3).
- F5 (12 s glow dot) — **not**: no cause found, gap row. F7 (CCS outline after death) — **not**: cause found, no fix (G28).
- PD table Run button (GAP-V551-STATS-2) — **done**.
- RATES — **partly**: 26 of the 40 measured (see §4).
- G33 tidy-ups — **partly**: RULE6 31 to 20 uses (still red, deny lists for you); SAVETRIP-ANCHOR retired; SPRITE still red (1 of 18); HOLDBAND prints only.

## 4. Printed for you

### Exchange rates (RATES, G31; 20 seeds, bisection; printed, never pass/fail)

26 new pairings measured on the merged tree.

| # | Rate | Mode |
|---|---|---|
| 1 | 1 ORS capital is about 3.5 CCS cruiser | forward |
| 2 | 1 ORS capital is about 5.5 SDV Destroyer | forward |
| 3 | 1 Providence is about 7.2 Munificent | forward |
| 4 | 1 Providence is about 8.5 Geonosian cruiser | forward |
| 5 | 1 Epoch is about 1.4 ORS capital | forward |
| 6 | 1 Epoch is about 1.5 Marathon | forward |
| 7 | 1 Epoch is about 11.5 Hillsborough | forward |
| 8 | 1 Halcyon is about 6.5 Hillsborough | forward |
| 9 | 1 ORS capital is about 4.0 RCS cruiser | forward |
| 10 | 1 ORS capital beats 24 CPV destroyer at least half the time: worth at least 24 | over (still winning at the 24 cap) |
| 11 | 1 CCS cruiser is about 4.5 CPV destroyer | forward |
| 12 | 1 Providence is about 5.6 Bulwark Mark I | forward |
| 13 | 1 Providence is about 7.5 Recusant | forward |
| 14 | 1 Munificent is about 1.5 Recusant | forward |
| 15 | 1 Halberd is about 3.5 CPV destroyer | forward |
| 16 | 1 Halcyon is about 2.5 RCS cruiser | forward |
| 17 | 1 Epoch is about 0.67 Kerel Carrier (it loses 1 v 1; 1.5 Epoch win half the time) | inverse |
| 18 | 1 Stalwart is about 0.81 SCC sword frigate (it loses 1 v 1; 1.2 Stalwart win half the time) | inverse |
| 19 | 1 Spirit of Fire is about 1.5 Halcyon | forward |
| 20 | 1 Spirit of Fire is about 2.5 Halberd | forward |
| 21 | 1 Marathon is about 0.67 Halberd (it loses 1 v 1; 1.5 Marathon win half the time) | inverse |
| 22 | 1 RCS cruiser is about 2.5 SDV Destroyer | forward |
| 23 | 1 Bulwark Mark I is about 2.5 Geonosian cruiser | forward |
| 24 | 1 Hillsborough is about 1.5 SDV Destroyer | forward |
| 25 | 1 Marathon is about 2.8 CCS cruiser | forward |
| 26 | 1 Spirit of Fire is about 1.5 ORS capital | forward |

All rows: 20 seeds. The tool's own wording is "1 X is about N Y (20 seeds)".

**14 not measured** (cut at the tail of the tool's order; RATES stopped for B13; two Kerel pairings were still running when it stopped):
- `kerel|cov_ccs`, `kerel|sdv`, `kerel|cov_rcs`, `kerel|cov_cpv`
- `paris|cov_makar`, `paris|cov_scc`
- `spirit_of_fire|unsc_marathon`, `spirit_of_fire|unsc_hillsborough`, `spirit_of_fire|kerel`
- `cov_rcs|cov_cpv`, `cis_bulwark|cis_recusant`, `unsc_hillsborough|cov_cpv`, `unsc_marathon|cov_rcs`
- `unsc_infinity|cov_hierophant`

**The 9 old V55_1 rows are gone.**
- The ship table and weapon files changed in V56, so the data fingerprint changed. The tool's own `--append` rule drops rows measured on other data. They were not re-measured and are not kept as "old".
- Dropped: Marathon/Hillsborough (your own example; V55_1 read 3.3 Hillsborough per Marathon), Epoch/Halcyon, Epoch/Halberd, Halcyon/Halberd, CCS/SDV, Munificent/Geonosian, Halberd/SDV, Stalwart/Makar, Halcyon/CCS.
- Re-measure Marathon/Hillsborough first (about 12 min alone).
- The PD table was measured on the older data (the tool's merge note says so).

### Measured in-night (the lead fills)
- Crowding: B13's SHOTSCALE on the merged tree (7 a side, 60 s, a fixed 40,000 x 22,500 u camera): k = 1: live shots 60.6 mean / 77 peak, on screen 56.0 / 76, fired a second 4.65 / 6.75; k = 0.75: 44.3 / 59, 44.0 / 59, 4.05 / 6.75; k = 0.5: 30.3 / 52, 30.3 / 52, 2.75 / 6.50. Damage per second is unchanged (48.6 at k = 1 and 0.5). TUNE's own run read higher (k = 1: 68.4 / 111 live) on its pre-fold tree.
- FX-14 frame cost: 6.06 ms mean frame time, the real threaded game on the siege bench, all five FX-14 switches ON, 30 s (`tools/v56_fx14_perf.sh`). The OFF run was cut by the script's timeout, so FX-14's own share is unknown (gap row).
- UI measurements: the A UI's envelope is 12.33 % to 14.77 % of the screen across the measured states (quiet, ship, group, ...), the centre of the screen 0 %; text 9-12 px, buttons 28 px and up.
- Fleet pace: a mixed fleet to engagement range: watched 96.0 s; unwatched with `coarse_pace_v56` 100.0 s (ratio 1.042); V55_1's unwatched 54.0 s (ratio 0.563).

## 5. Astra

### Bound (all ten passed the byte-for-byte check at B0, D-V56-05)

| Package | Version | ZIP SHA-256 (short) | Switch | State |
|---|---|---|---|---|
| FX-14 A/B (impact A, 3 fire zones, far glows), `Shared\effects\fx-14-siege-impact-far-glows` | v1 | 1484784b | `siege_impact_fx14`, `fire_burn_fx14`, `far_glows_fx14` | ON |
| FX-14 Part C (plasma bolt hit), `Covenant\effects\plasma-bolt-hit` | v1 (Stage 2) | 116e4eb2 | `plasma_bolt_hit_fx14c`, `plasma_bolt_orientation_fx14c` | ON |
| FX11-Damage-8A-N01, `Shared\effects\fx-11-damage-8a` | v1 | 58f6cffb | `damage_8a_n01_v56` | ON |
| FX11-Wake-9-N01 (new nuke wake), `UNSC\effects\fx-11-nuke-wake` | v1 | 292feeb0 | `wake_n01_v56` | ON |
| FX07-Beam-Heat-N01, `Covenant\effects\fx-07-beam-contact-heat` | v1 | 633aca1b | `hull_heat_v551` | ON |
| (same package) beam contact | v1 | 633aca1b | `beam_contact_v551` | **OFF** |
| FX12-Ion-Ring-N01, `CIS\effects\fx-12-ion-ring` | v1 | fb75c191 | `ion_ring_v56` + `subjugator_ion_fx12` | ON |
| CIS-Canopies-N01 (Citadel, two v6 pirate platforms), `CIS\effects\n01-station-canopies` | v1 | d7b2f2d7 | `canopies_n01_v56` | ON |
| N01-Collider-Covenant-L4 | v1 | 6c9d7495 | `colliders_n01_v56` | ON |
| N01-Collider-UNSC-Large-Shipyard | v1 | 935320dd | `colliders_n01_v56` | ON |
| N01-Collider-UNSC-L4 | v1 | 698373b3 | `colliders_n01_v56` | ON |

- FX-14 A/B and Part C were installed in `Official Sprites` at B0 (G2): 137/137 and 110/110 files re-checked, INDEX regenerated (148 assets), ledger rows added. Full SHAs: A/B `1484784b37209e55569a0aec382f7e0fda0c4ceae64e043f53c8f252ae8ed911`, Part C `116e4eb228a449c949bbba4bb34ff40a2cdcb0290f66811360d2897e6204e6b1`. The Part C selection file matched 12 of 12.
- Matches: Part C against her six stills (mean diff 1.35/255 or less), impact A and fire zone (0.32/255 or less), the wake against her reference layer (0.000000), hull heat (NCC 0.931 / 0.890 / 0.838 holding).
- Colliders: Covenant L4 703 u to 45.6 u past the art, UNSC large shipyard 449 to 65.7, UNSC L4 298 to 33.7 (bar 75 u).

### Built OFF, and why
- **Beam contact** (`beam_contact_v551`): does not match her clocked stills. Holding: NCC 0.765 / 0.615 / 0.750 and 1.74x her brightness. Rising: 0.656 / 0.660 / 0.751 and 2.00x. Ours is arcs inside a large soft disc; hers is a small bright dot (G-V56-ASTRABIND-2).
- **FX-11 Archer 14A**: carried OFF from V55 (FX11PORT-1), not re-checked.
- **EMP contact arcs of the ion ring**: not ported (needs a per-contact event model; a partial port would be a stand-in) (G-V56-ASTRABIND-1).
- **Siege rupture** (`siege_rupture_v55`): stays OFF (your Q1 B); impact A replaces it while on.

### Asks
1. CIS and Republic engines in the FX-05 way; every hull without her plume anchors now draws no engine (G-V56-ASTRABIND-R1).
2. DMG-01 damage art for the hulls with none (23 hulls in the list: Subjugator first, then `rep_mandator_ii`, `lucrehulk`, the capitals and so on down to frigates) (G-V56-ASTRABIND-5).
3. Colliders for 8 stations still past the 75 u bar (`cov_outpost_l3` 289 u, `unsc_military_shipyard` 241, `cov_mining_station` 200, `unsc_outpost_l3` 139, `cov_salvage_yard` 130, `cov_outpost_l2` 119, `unsc_civilian_shipyard` 84, `unsc_mining_station` 78).
4. Beam contact and the 1.6x hull heat: how her composite adds heat over a bright hull (sRGB vs linear HDR), final contact composite, quad size and energy.
5. Ion ring: what a contact event should carry for the EMP arcs; a turret package for the ion cannon's I01 and I02 (blocks Approved); a native arc texture; camera and clock for the canopy stills.
6. FX-14: her 3.8 GB import peak is over our 2 GB budget; a far-view hit floor for Part C if wanted; camera and clock for one full-scene beat and one far sprite; a contour for non-canopy hulls; whether the cross-fade goes on the plasma head, comet and Archer glow.
7. No new art needed: the wake can look gappy in a crowd in the threaded game (our key, G-V56-ASTRABIND-7); the performance of her wake, 8A and ring is unmeasured threaded (G-V56-ASTRABIND-8).

## 6. The switch table

All 36 V56 switches ship ON (D-V56-01, undo: one word per switch; OFF = V55_1). "Both" = map and system view.

| Switch | Ships | Does (6-10 words) | Views |
|---|---|---|---|
| `guard_standing_v56` | ON | Guard and screen stay after deselect and fleet moves | sim, both; coarse board gap |
| `guard_spread_v56` | ON | PD ships spread across the fleet's valuable ships | sim, both; coarse board gap |
| `guard_close_v56` | ON | Guard stands close to its ward, off fire lines | sim, both |
| `play_beats_default_v56` | ON | Raider and Hunter fly their play, no default guard | sim, both |
| `raider_picket_v56` | ON | Raider scouts 9,000 u ahead until it finds enemy | sim, both |
| `fleet_pace_v56` | ON | Fleet closes at its slowest member's speed | sim, both |
| `coarse_pace_v56` | ON | Unwatched board closes at the same slow pace | unwatched board |
| `remote_order_v56` | ON | Right-click in another system's view: trip plus exact point | both |
| `map_keys_v56` | ON | Chart answers G, J and Shift+F | chart (G: same system only) |
| `stop_charge_v56` | ON | X cancels a charging jump, ships stay put | both |
| `trip_replace_v56` | ON | A plain move replaces a galaxy trip; Shift appends | both |
| `card_fix_v56` | ON | Bodies card: hover only, lists stations, names body | chart only |
| `map_nav_v56` | ON | Wheel on a fleet marker; no hover stutter; panel closes | chart only |
| `ui_a_v56` | ON | The A interface: ribbon, dock, bars, dropdown, Inspect | both; not planet surface |
| `tests_menu_v56` | ON | The V56 Tests list (102 rows at fold) | main menu |
| `ui_build_v56` | ON | Build flow, M11 yard tray, overview | system view only (GAP-UIBUILD-1) |
| `ui_reports_v56` | ON | Collapsed report and contact bars | both; not planet surface |
| `tune_bench_v56` | ON | Sandbox SHOTS tab, crowding readout, PD Run button | n/a: bench |
| `siege_impact_fx14` | ON | Siege impact A with three 15 s fire zones | system view (map draws no shots) |
| `fire_burn_fx14` | ON | Fire zones burn strike craft, 20% hull a second | sim; coarse step does not run it |
| `far_glows_fx14` | ON | Six far-zoom shot glows, nuke brightest | system view far zoom |
| `plasma_bolt_hit_fx14c` | ON | Part C plasma bolt hit on real contacts | system view |
| `plasma_bolt_orientation_fx14c` | ON | Part C hit angle from the hull surface | system view |
| `wake_n01_v56` | ON | New nuke wake replaces wake 9 | system view |
| `damage_8a_n01_v56` | ON | Brief smoke and fire puffs on fresh hits | system view (10 hulls) |
| `ion_ring_v56` | ON | Astra's FX-12 ion ring art | system view |
| `canopies_n01_v56` | ON | Real shield canopies for Citadel and two platforms | system view |
| `no_flare_v56` | ON | Old pale-blue engine flare retired, nothing instead | system view |
| `colliders_n01_v56` | ON | Three accepted station colliders replace hit outlines | hull data, fine tier |
| `ion_broadside_v56` | ON | Ion-gun ship turns its side to the enemy | sim, both tiers |
| `bench_battle_v56` | ON | Sandbox ships recharge shields as in battle | n/a: bench |
| `citadel_rot_v56` | ON | Placed Citadel keeps the ghost's rotation | n/a: Sandbox placer |
| `beam_reach_v56` | ON | Projector lance held while its round flies | system view draw |
| `archer_pd_v56` | ON | PD can shoot Archers (50 hp, damage x0.5) | sim, fine tier; coarse gap |
| `pulse_pd_v56` | ON | Covenant pulse laser is real point defence | sim, both tiers |
| `draw_min_12_v56` | ON | Weapon art hidden under 12 px | system view draw |

Flipped from V55_1 by ruling (also ON; they are V55_1 switches):
- `subjugator_ion_fx12`: OFF to **ON** (G20, your 1 Nov ruling). Undo: `false` in `data/combat/subjugator_ion_fx12.json`.
- `hull_heat_v551`: OFF to **ON** (G19: it passes Astra's bar). Undo: `false` in `data/fx/contact_heat_v551.json`.

Still OFF: `beam_contact_v551` (no match), `siege_rupture_v55` (your Q1 B). One new order kind, `escort_off`, has no switch (system view through the door; the chart's Off refuses).

## 7. Hash events and the golden re-record
- **Step 0** (every V56 switch off) = V55_1's golden on all ten.
- **E-PULSEPD-V56-1** (the pulse laser is PD): tyrant 7ecb22cd → a1ac34da (attackers 154.7 → 151.0 s).
- **E-GUARD-V56-1** (standing guard, spread, close stations, plays, picket, fleet pace): main 45abc408 → 6be20b0e (attackers 389.6 → 480.5 s); siege c99533bc → ca9c2930 (attackers 477.4 → 439.6 s); tyrant a1ac34da → d89159c5 (attackers 151.0 → 158.0 s); venator f2b8430e → 364e1822 (defenders 176.9 → 157.6 s).
- Nothing else moved: duel, screen, live, traffic, fleets, econ. **No winner flipped.** Archer PD, the ion guns, fire-zone burns, canopies and colliders move no fixture (none carries them); their own gauges prove them.
- `tools/golden.txt` re-recorded **once** after the walk. `tools/golden_owners_on.txt` re-recorded once in B14 (same events; step 0 = V55_1's table).
- After the commit, the ten hashes on the committed tree = golden.

## 8. Reds, in plain words
**Left red after B14:**
- **TIER 4 §15.11** (known): no golden fixture has a jump zone, so retreating ships can't jump out.
- **SPRITE** (known): the Victory's collider disagrees with an independent check on one ray at one seam.
- **RULE6** (known): 20 uses of retired hull ids, mostly the Sandbox's own deny lists (they list the retired ids to keep them out) plus two test fixtures. Your call whether deny lists count.
- **RESOLVE**: red as on V55_1 (escorts hold station on a slow capital, so the watched arrival never reaches contact while the coarse one does). Its fit is now also stale (fit at 18,000 u contact, the game uses 36,000). GUARD's notes §8 has the exact re-aim if you want it. Your call (D-V56-14).

**Fixed or re-aimed in B14:**
- **X7FIXCUI**: a **real bug**. With the A UI on, the Galaxy button in the system view was drawn but couldn't be clicked (the battle panel wiped its click area). Fixed in `hud.gd`; Esc always worked.
- **SHIPPANEL50, DEVPANEL, ORDERKEYS buttons**: checks still driving V55_1's ship panel, which the A UI replaces. Each now tests the old panel with the A UI off AND the A dock with it on (LOCK ON in Orders, Guard/Screen in the Escort dropdown).
- **ORDERKEYS Esc and typing**: the keys were right; the standing guard put the default guard back after the test's "clear". The test now also takes the escort off.
- **SHIELDONHULL**: the shield outline table was stale for the three new N01 canopies; re-derived, no hash moved.
- **TIER 4 (owners on)**: the owners-on table re-recorded (above).
- **TESTSGROUPS**: one Tests card line was too long.
- **CORECMD**: the self-check's stand-in folder pointed at itself; the real `--core` was fine.
- **REPORTFOLD's two controls**: blind (looking for the wrong words); now catch their faults.

**Inherited, not fixed (red with V56's switches off too):** NUKES NUKECOUNT and ARCHER WEAVE (in the fuller sweep, not the lean list).

## 9. Then

### Review questions (each names its clip)
1. **The A UI** (clip 01): does the dock, ribbon and report bar read in all four factions' light? Keep it as the default, or tune first?
2. **Guard / Screen from the dropdown** (clip 02): it reads [pending] then [accepted] and is kept after you deselect. Is the dropdown the right home for it, or do you want the G / I keys back as the main way?
3. **Bodyguard vs Raider** (clip 03): do they look different enough? Note (F3): the Paris bodyguard picked the Halcyon as its ward, not the Epoch. Should "the biggest ship" mean the biggest hull class (Epoch) or the toughest by hull points?
4. **A mixed fleet arriving together** (clip 04): the Venator and Paris arrive together, but here because both made the same micro-jump (F4). Does this match what you meant by fleet pace, or do you want the pace held on plain moves inside a system too?
5. **Order into a system you're looking at** (clip 05): one right-click gives the trip plus the point. Is that the feel you asked for?
6. **X on a charging jump** (clips 06 and 06b): in the system view the charge stops; on the chart you only see the toast and the plan clearing (no charge is drawn there). Is the toast enough on the chart?
7. **The build flow** (clip 07): catalogue, red ghost when blocked, CONFIRM, then the job. Approve, or what's off?
8. **Siege impact A and the three fire zones** (clip 08): size, length (15 s) and look. Approve? (No fighters were filmed burning; place them on the bench yourself.)
9. **Far glows** (clips 09 and 09b): heavy shots stay as glows when zoomed out, nuke brightest. Is that readable, or are they too small or too bright?
10. **The plasma-bolt hit, Part C** (clip 10): weak clip (F7): the hit is a few frames at this zoom. Worth a closer look on the bench (Tests `v56_plasma_hit`) before you judge it.
11. **The nuke wake** (clip 11): weak clip (F8): it shows the blast and smoke, not the flight's wake. Check on the bench (Tests `v56_nuke_wake`).
12. **The Subjugator** (clip 12): no blue engine circles, and the ion ring fires from its side after about 50 s of turning and charging. Is 50 s before the first ion shot OK?
13. **The CIS Citadel upright** (clip 13): is it the right way up on the board now?
14. **The Kerel's projector lances** (clip 14): do the beams now reach the ship they hit?
15. **PD against Archers** (clip 15, weak: the bursts are small at this zoom): PD now shoots Archers, and the Covenant pulse laser now counts as PD. That makes the Kerel and SDV "PD ships" that guard by default (COV-08 tension below). Keep, or should pulse-laser ships not default to guard?
16. **Fewer, heavier shots** (the stats page, F10 → SHOTS; the crowding numbers in §4): this is your tuning session after the build (G32). Your numbers on the bench are not kept unless you say them in chat.


### Gap rows that block Approved (Rule 5; nothing may go to Approved on these)
- **G-V56-ASTRABIND-4:** ion cannon turret art (I01, I02) is the Heavy Ion Battery's `rep_heavy_ion` — a marked relative. Needs an Astra turret package.
- **G-V56-ASTRABIND-1:** ring EMP contact arcs not drawn; nothing stands in.
- **G-V56-ASTRABIND-2:** beam contact does not match; `beam_contact_v551` OFF.
- **G-V56-ASTRABIND-3:** hull heat ON but about 1.6x as bright as hers (sRGB add). Your eye.
- **G-V56-ASTRABIND-5 / -R1:** 10 hulls have DMG-01; every other warship draws no damage marks (Subjugator first). Old flare retired; CIS and Republic hulls without plume anchors draw no engine.
- **G-V56-ASTRABIND-6:** three canopies proved by data, not matched to Astra's native stills.
- **G-V55-HITSHAPE-1, -2, -3, -7 to -14 (carried):** 11 stations still past the 75 u bar (3 Covenant yards we derived, 8 Astra-owned colliders). V56 closed HITSHAPE-4, -5, -6. HITSHAPE-R1 (CCS, ORS, RCS shapes derived from alpha) unchanged.
- **G-V56-FX14-G3:** Part C's contour tangent only for hulls with an X14 canopy; the rest use the contact's own bearing (10 of 174 contacts). A derived stand-in.
- **G-V56-FX14-G4:** no far-view hit floor for Part C (none approved).
- **G-V56-FX14-G7:** FX-14 matches are narrower than "each delivered still": shader quad vs her keyframes, Part C vs her six stills. Full scene and far glows not compared.
- **Burn and zone numbers (guesses):** burn 20% hull a second (G15); her zone numbers are GUESS in her own ledger. You set them in the tuning session.
- **Looks with a weak or missing clip:** weak 4 (pace), 9 (far glows), 10 (Part C), 11 (wake), 13 (Citadel, stand-in), 15 (Archer PD); missing: M11 tray clip, burning fighters. A look with no clip is unseen. You have judged none.
- **Carried V55_1 and V55 blockers, unchanged:** G-V551-FX-G4 (Subjugator centre blast), G-V551-FIXB-R2, FX11PORT-1, ASTRA-FX11-2, V54-SIEGE-G1, G-V54-SHOTFX-G7, G-V55-SIEGEFX-G4 and -G5, plus V53's carried list.
- **Closed by V56:** ASTRA-FX12-1, ASTRA-FX12-4, FX11PORT-2, INHERIT-G1, INHERIT-G2, G-V55-HITSHAPE-4, -5, -6, G-V551-FX-G2, -G3, -G5.

### Every guess used tonight (G-numbers from the guess register; value as shipped; where)

| G | Value used | Where |
|---|---|---|
| G1 | start from `gate/v55_1` head (20a822ba), commit on `gate/v56` | git |
| G2 (ruled) | FX-14 packages installed in `Official Sprites` at B0, sha-checked | Official Sprites |
| G3 | ward ladder super capital 4, capital 3, carrier 2, cruiser 1; ties op_budget then hull points then lower uid; peer fallback only up to tier 2 (D-V56-GUARD-12, guess) | `data/orders/guard_v56.json` |
| G4 | station 1.0 guard length off the hull, reach cap 0.9, turn step 15 degrees, fire-line margin 600 u, recheck 1.0 s | `guard_v56.json` |
| G5 | pace min 2 members, release 1.0 x range; coarse approach efficiency 1.0 (V55_1 0.85), burn 0.98 | `guard_v56.json` |

… 35 guesses in all.

Guesses numbered by work stream (27, all `_guess` in their data files and in `TUNING.md`; none ratified):
- GUARD: G-V56-GUARD-1 `keep_on_fleet_order` list; peer fallback tier 2; the station and gauge tolerances above.
- ORDERS: `card.grace_px_guess` 14; `station_rows_max_guess` 4; `marker_wheel_px_guess` 48 (declared, unread).
- UICORE: `dock.pending_s` 3.0; report slot corner; dock column widths and six actions; `poll_frames` 15; minimum viewport 960 x 540.
- UIBUILD: legacy BUILD button kept; review list shows 8 jobs then "+N more"; card 8 px under the report slot; catalogue column 264 px (84 px cell), compact 190 px (52 px cell).
- UIREPORTS: layout numbers; 6 contacts per view; faint under 0.33, strong from 0.66.
- FX14: match thresholds (diff 3/255, NCC 0.98, black 3); hand-off band 0.5 to 0.35; caps 24 zones and 64 contacts; incidence sign convention; zones draw at every zoom. Her zone numbers: radius 180, growth 0.38, fade 1.2, gain 0.55, travel 0.5 / 0.59 / 0.68, angles -65 / 65 / 182, distances 640 / 680 / 610. Count 3 and life 15 s are ratified.
- ASTRABIND: ring `min_screen_px` 6; broadside reads `face_lead_s` and range; coarse arc weight 1.0 / 0.0.
- COMBATFIX: Archer damage x0.5; pulse laser keeps the hull fallback.
- TUNE: slider step 0.05; crowding window 5 s, sample 1.0 s (was 0.25 until FIXTUNE).

### IDs named

| ID | What it is |
|---|---|
| GUARD, ORDERS, UICORE, UIBUILD, UIREPORTS, FX14, ASTRABIND, COMBATFIX, TUNE, RATES, STILLS | the build's helper work streams, L1 to L10 plus B12 |
| FIXGUARD, FIXASTRA, FIXORDERS, FIXTUNE, FIXB10, FIXB13A, FIXB13B | follow-up fixes after folds and checks |
| B0 to B16 | the kickoff's blocks (B13 = the lean check, B14 = reds) |
| G1 to G35 | the guess register (G2, G20, G23, G35 ruled) |
| G-V56-`<NAME>`-n, GAP-V56-ORDERS-n, GAP-UICORE-n, GAP-UIBUILD-n, GAP-UIREPORTS-n, G-V56-FX14-Gn, F-V56-STILLS-n | V56's own gap rows (112) |
| G-V56-`<NAME>`-Rn | records-pass names for items a note left unnumbered |
| every V55_1 id (GAP-V551-*, G-V551-*, KEYS-GAP-n) | carried: 119 rows, 19 closed |
| D-V56-00 to -15, D-V56-`<NAME>`-nn | decisions (lead and each work stream) in `V56_DECISIONS.md` |
| E-PULSEPD-V56-1, E-GUARD-V56-1 | the two labelled hash events (tyrant; main, siege, tyrant, venator). No winner flipped |
| gauges (GUARD) | GUARDSTAND, GUARDSPREAD2, GUARDCLOSE, PLAYSDIFFER, FLEETPACE |
| gauges (ORDERS) | ANYWHERE2, MAPKEYS, STOPCHARGE, TRIPREPLACE, CARDCLICK, HOVERZOOM, NAVCLOSE |
| gauges (UI) | UIAFACTIONS, UIADOCK, UIASCALE, UIAHASH, TESTSLIST56, BUILDPAY (BUILDFLOW), YARDTRAY, REPORTFOLD |
| gauges (FX14) | FX14BIND, FX14MATCH, FARGLOW, FIREBURN, PARTCMATCH, BOLTCONTACT, FX14LIVE, FX14BENCH |
| gauges (ASTRABIND) | N01BIND, WAKEMATCH, DMG8A, CONTACTMATCH2, CONTACTHEAT, IONRING, IONBROADSIDE, CANOPYN01, HITSHAPE2, NOFLARE |
| gauges (COMBATFIX) | BENCHSHIELD, CITADELROT, BEAMREACH, ARCHERPD, PULSEPD, DRAWSIZE12 |
| gauges (TUNE, RATES) | SHOTSCALE, TUNEUI, NOKEEP2, PDRUN, XRATE, STATSTABLES |
| known or open reds | RESOLVE (D-V551-31, D-V56-14), TIER 4 section 15.11, RULE6 (20 uses), SPRITE |
| R-ZL-1, R5, COV-08 | your 12 px rule; your ion-gun rules; PD mainly for small ships |
| UIA-D01 to D09, M07 to M14 | the A UI handoff's decisions and mockups |
| DMG-01, FX-05, FX-07, FX-11, FX-12, FX-14, N01 | Astra's packages and the 1 Nov open-asks round |
| F5, F7, F3, F4, F9 | open clip findings and map findings |

### Headaches
- **B13 took 2 h 11** against V55_1's 1 h 57: V56 added 48 rows of new gauges to the lean list (170 checks + 182 controls planned). The lean check grows with every build that adds its gauges; the list wants a trim rule.
- **The A UI broke four old checks and one real thing.** The Galaxy button on the A ribbon was drawn but had no click area in the system view (Esc still worked). Fixed in B14 (FIXB13A). The other three were checks still driving V55_1's ship panel: they now test the old panel with the A UI off AND the dock with it on.
- **GUARD's standing tasks re-post the default guard** after a "clear" order. Tests that clear a ship and expect nothing posted were fooled (ORDERKEYS). Watch for this in play: "clear" alone doesn't take a PD ship's guard off; Escort > Off does.
- **One stale data table:** ASTRABIND turned on three new station canopies but didn't re-derive the shield outline table; SHIELDONHULL caught it, re-derived in B14, no hash moved.
- **The dev PERFORMANCE strip** is on by default and, opened, covers the A UI's tray and overview slots (no ship command). Dev view only.
- **FIXB10 ran Godot inside V55_1's folder** while checking an inherited red: it wrote only logs to V55_1's `logs/` (gitignored, no tracked file changed). Rule 1 slip, noted.
- **RATES** got 26 of 40; V56's data changes dropped V55_1's 9 rows, including your Marathon/Hillsborough example. Re-measure that one first.
- **The raw clip AVIs (3.4 GB)** stay on disk (gitignored) until you've reviewed; then delete them (Rule 7).
