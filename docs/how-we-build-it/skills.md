# The skills our agents use

A skill is a short, focused set of instructions an agent loads for one kind of task. Each one below says what it's for, why it was made, and how it changed. The skill files themselves stay private. This page describes them.

Collaborative skills, where I'm in the loop at a gate or an approval, end with a **corrective-action clause** (added 8 Oct 2026). When a pass breaks (a rerun, a correction, or "I wish you'd done X"), the skill diagnoses what failed and amends itself once I agree, with a dated entry in its own correction log. Unattended overnight runs only log the break for me to review.

## Art pipeline

### Ship sprites
**For:** taking a ship or strike craft from reference-based concept to a frozen master, with collision polygons, removable armour, break-apart splits and a delivery package.

**Why it was made:** the art workflow first lived in another AI workspace. After the Lucrehulk run on 7 Sep 2026 it was rebuilt as a project-local workflow. On 9 Sep it became the single authority, with the Venator package as the baseline every new ship is measured against.

**How it changed:**
- **9 Sep:** removable armour must sit on the hull's outer edge. Fleet scale is fixed at set multiples of the reference ship.
- **21 Sep:** an approved concept *is* the in-game art until a production package replaces it. This came after a build drew placeholder polygons over sixteen approved civilian concepts.
- **26 Sep:** fleet-review corrections after the Covenant ship roster: reconcile the roster against approvals, review at logical scale, and no separate weapon art on tiny fighters.
- **27 Sep:** a reference-review board became mandatory. Small craft need only a master and a basic outline, after a pass over-produced armour and split pieces nobody would see. Civilian ships get no armour or hardpoints.
- **4 Oct:** collision detail scales with a ship's gameplay size.
- **8 Oct:** gained the corrective-action clause.
- **12 Oct:** every delivery goes into a versioned folder; on approval the old version is archived, never deleted. Cruisers and larger get jagged fracture edges.
- **25 Oct:** new shield, death and armour candidates must be shown beside an approved example at matched physical scale. The first pass had passed its numerical checks but looked wrong.

### Weapon sprites
**For:** separate weapon sprites, mounting bases and firing effects, and fitting them onto ships by measurement.

**Why it was made:** for the first Venator weapon production run, 13 Sep 2026.

**How it changed:**
- **26 Sep:** no separate weapon art for tiny fighters.
- **27 Sep:** the reference-review board is mandatory. Civilian ships carry no weapons.
- **8 Oct:** gained the corrective-action clause.
- **12 Oct:** the versioned delivery-folder rule.

### Ortho to Blender
**For:** turning an approved top-down ship sprite, or an existing 3D model, into a low-poly model for the game's 3D side.

**Why it was made:** 24 Oct 2026, to give the game a path from its 2D art to 3D.

**How it changed:**
- **v1, 24 Oct:** drew four flat views, then extruded them. The first test ship came out a "striped brick", yet every check passed, because the checks only compared the views with each other.
- **24–25 Oct:** the shape is now set in 3D first, from measured references, as a grey blockout I approve before any painting. Likeness checks were added.
- **25 Oct:** a feature kit for engines, turrets and bays, after I said the blockout read as stacked layers.
- **25 Oct:** a second path that works backwards from an existing model, with a surface-deviation check. The 2D-first route still wasn't working.
- **v4.5, 25 Oct:** added the final mapping of which ships take which path.
- **30 Oct:** the skill's files existed only in a chat, so they were rebuilt by replaying that chat. The replay matched the saved v1 byte for byte.
- **Still open:** I ruled the output too blocky on 29 Oct. Refining it is the next round.

### Ship identity (draft)
**For:** each hull's role, feel, counters, why you'd invest in it and its faction flavour, agreed with me before any art, loadout or balance work.

**Why it was made:** 8 Oct 2026, from a voice session. It guards against two traps: tiers that only add bigger numbers instead of new abilities, and a flat unit cost that collapses late games into spamming one ship.

**How it changed:** still a draft, with nothing logged yet.

## Game design and implementation

These five were written for the project on 13 Sep 2026. Each adapts ideas, not text or code, from seven MIT-licensed skill repositories ([GodotPrompter](https://github.com/jame581/GodotPrompter), [jakubkrehel/skills](https://github.com/jakubkrehel/skills), [designer-skills](https://github.com/Owl-Listener/designer-skills), [MengTo/Skills](https://github.com/MengTo/Skills), [tastemaker](https://github.com/codeswithroh/tastemaker), [garden-skills](https://github.com/ConardLi/garden-skills), [emilkowalski/skills](https://github.com/emilkowalski/skills)).

**Why they were made:** to give agents narrow, game-specific guidance in place of general web-design advice. The review stripped out website frameworks, fixed web timing rules and pause-menu recipes. The game world never pauses, so those recipes would fight it.

| Skill | For |
|---|---|
| UI implementation | Native Godot UI, HUD, panels and command interactions, with states that tell the truth |
| Motion and feedback | Purposeful motion and feedback: timing, interruption, effect lifecycle |
| Camera and scale | Framing, semantic zoom, and keeping fleets and planets readable at every scale |
| Environment layout | Moons, asteroids and structures arranged as readable geography, not set dressing |
| Visual QA | Acceptance reviews from real in-game evidence and repeatable player journeys |

**How they changed:** environment layout and motion feedback later gained a pointer to the mandatory reference-review board (27 Sep), for when new art is authorised. As build-time guidance for unattended runs, they don't carry the corrective-action clause.

### UI/UX checklist (third-party)
**For:** a UX checklist and lookup: hover and tap, focus, contrast, feedback, layout. Never used for the game's palette, fonts or style.

**Why it was added:** 27 Sep 2026, to fill a gap. The five skills above had no checklist of common interaction failures. It's a pinned copy of the MIT-licensed [ui-ux-pro-max](https://github.com/nextlevelbuilder/ui-ux-pro-max-skill) with one scope block added, because its style generator, when tested, proposed a landing-page layout and web fonts for a game screen.

## Running the project

### Talking discussion
**For:** turning a voice talk into a numbered, append-only record of rulings, with prepared questions beforehand.

**Why it was made:** for the first talk sessions, on 15 Oct 2026, so decisions made out loud end up as a record a build can be judged against.

**How it changed:** on 21 Oct I asked for research instead of guesses during talks, and that became part of the skill. Fifteen talks by 2 Nov.

### Version plan
**For:** after the rulings lock and before a build starts: plain work blocks with times, the parallel lanes and a Gantt chart for me to trim.

**Why it was made:** 11 Oct 2026. I asked for a plan in blocks with times so I could cut scope before the build, not after.

**How it changed:**
- **12 Oct:** a planned-vs-actual Gantt, so estimates get checked against what happened.
- **Later:** added a rulings table, the guess register and a planned-vs-actual table.
- **Wider use:** applied to experiments and audits as well as builds.

### Art brief
**For:** writing briefs for the art lead (art, effects, sound). It sweeps for prior work first, then writes the brief in a standard format.

**Why it was made:** alongside the art delivery ledger, started 17 Oct 2026, which records every delivery the briefs check against.

**How it changed:** on 19 Oct the art lead's workflow was written up as house rules, including a feedback loop on every rejection.
