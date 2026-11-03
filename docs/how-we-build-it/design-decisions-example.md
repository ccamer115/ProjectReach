# Talk rulings, 30 Oct 2026 (a voice session)

*A real project document, lightly edited for privacy. Internal file names and IDs are left in to show the record-keeping; the files themselves aren't public.*

The fourteenth talk. Everything here is fiction (a video game).

## 1. What happened, in one breath
- You hadn't played V54 or watched its clips yet.
- You answered Astra's INT-01 questions 7–9, S3D-01 question 4 and GAP-53 questions 6, 8 and 9. GAP-53 question 7 is parked.
- You ruled on eight of the nine calls V54 left for you; the Subjugator blast is parked.
- You set a new testing rule: tuning is not a pass/fail gate.
- Then we worked through ship roles: tiers instead of black and white, Hammer retired, Bodyguard and Screen become orders, one Line and one Hunter destroyer per faction.

## 2. Rulings

### Interiors (INT-01, answers to Astra's questions 7–9)
| ID | Ruling | Your words |
|---|---|---|
| R-T14-1 | **Q7 A: the detailed panelled look (Modular SciFi) leads the existing-kit side** of the research. Research direction only; nothing is bought. | "Yeah, A sounds good" |
| R-T14-2 | **Q8: corridors sit at true scale, in their real positions inside the hull, but they don't fill it.** Most of the hull's volume is empty or off-limits; the routes thread through it. A MAC hole still lines up exactly. This is Astra's A (registered at real positions), with the two additions below. | "imagine you had the volume of the Halcyon … if you were to see an X-ray of all of our corridors, it's just not going to take up all the usable space … we don't need to use up all of that space" |
| R-T14-3 | **The giants get a wide, drivable central space** like the big central hangar in the Infinity mission: the Spirit of Fire, Infinity, Subjugator, and the Lucrehulk as one ring corridor. Ground vehicles staged for an invasion can be taken over, or a Pelican drops in a couple of Warthogs. | "this long, massive, wide chunk of the corridor that is open and we have vehicles in it" · "the Lucrehulk … one circular corridor … ground vehicles that are getting ready … a Pelican dropship drop in a couple of warthogs" |
| R-T14-4 | **Smaller ships only span the parts that matter**: the hangar, a route to the reactor, the bridge. Systems are placed so the walk is reasonable (the reactor isn't all the way at the back), with extra ways round such as maintenance lifts and moving platforms. | "those smaller ships, we don't need to make the map go from end to end … the reactors aren't all the way in the back … movable platforms … for the maintenance crew" |
| R-T14-5 | **Q9 A: mag boots hold you to the surviving floor**, so the breach can't pull you out, but you can still step off the edge on purpose and die. | "Yes, agreed." |

### 3D exteriors (S3D-01, question 4)
| ID | Ruling | Your words |
|---|---|---|
| R-T14-6 | **Q4 A: use Claude's existing modelling toolkit; don't rebuild it.** See §4.4 for where it is. | "if you have those, no need to rebuild them" |

### Art gaps (GAP-53, questions 6, 8, 9)
| ID | Ruling | Your words |
|---|---|---|
| R-T14-7 | **Q6 A: the v6 pirate platforms and the Citadel reuse the approved STN-01 station death sequence and fitted CIS shield canopies, with no structural breakup.** Only Q6: your "A for all of those" meant only the question we'd talked about (R-T14-10). | "A … is fine" (then: "I just meant the one … we didn't talk about") |
| R-T14-8 | **Q8 A: the Covenant salvage yard keeps its existing centre dock spot and starboard drop-off**, with the clearance checks kept. | "Sure." |
| R-T14-9 | **Q9 B: include one Republic station death pilot in the next review**, not deferred. | "No, don't defer. Let's do it." |

### How the talks run
| ID | Ruling | Your words |
|---|---|---|
| R-T14-10 | **You can only agree to things Claude has actually described.** A blanket "A for all" covers only the items already spoken about. | "I shouldn't be able to agree to things that you haven't explicitly spoken about yet." |

### V54's open calls
| ID | Ruling | Your words |
|---|---|---|
| R-T14-11 | **The CIS rapid laser becomes real point defence** (`cis_pd_v54` ON). | "it should definitely be a PD gun. We need the PD as a weapon." |
| R-T14-12 | **MAC rule, restated: the Light MAC on small ships may be outranged by capital guns. The Heavy and Super-heavy MACs must outrange every capital gun.** A frigate shouldn't outrange a capital. Checked in text (§4.2): it holds today. | "it'd be weird if a frigate was able to outrange a capital ship … you want … the heavy mac and the super heavy macs to be able to outrange the capital guns" · "that looks good for me" |
| R-T14-13 | **Shields recharge at two rates: ×0.1 in battle, the normal pre-V54 rate out of battle.** A ship goes into battle mode the moment it's shot at, and **drops out 60 seconds after its last hit.** This replaces the flat ×0.1 and fixes the ~10 % attack-jump landing (§4.1). | "the one tenth should be … in battle … out of battle, it should stay that higher 10x amount" · "Let's go a minute." |
| R-T14-14 | **The attack jump counts carriers' strike craft** in the enemy's reach. | "Yeah." |
| R-T14-15 | **No faction lock on the Siege Plasma Cannon.** No refitting in the game is enough of a lock; keep things open so future ship customisation isn't blocked. **Standing: no double locks.** | "we don't need a double lock … I would like to keep things open … no refitting inside of the game is enough of a lock" |
| R-T14-16 | **The Covenant outposts' placement distances stay as they are** (not doubled with the guns). | "No, that's fine. I think we can leave it as is." |
| R-T14-17 | **Getting shot puts a ship in battle, whatever the range.** So the ion guns' 52 km reach against the 36,000 contact radius isn't a problem by itself. | "I thought we said if you're getting shot at, you're in a fight. It doesn't matter the range." |
| R-T14-18 | **The jump circle shows the real jump area, but that area must be small**: about big enough for the largest ship, and only the ship's centre has to be inside it. Today's 40,000 is wrong (§4.6). | "it's supposed to be like not a large jump area … the center of the ship has to be somewhere in that circle" · "it shouldn't be a massive circle" |

### Testing and balance
| ID | Ruling | Your words |
|---|---|---|
| R-T14-19 | **Tuning results stop being pass/fail gates, and the golden hashes don't hold tuning hostage.** Tests that catch broken code stay: symmetry (the rotate-30° check), determinism, things breaking. "This fight ends in time" or "raiders win 70 %" become tuning you do in the Sandbox. **The SDV left-side bias is a real bug to chase.** | "it's going to be impossible for me to … keep track of not changing the golden hashes when we're doing all this tuning … rotating the ship 30 degrees … that's an amazing use of a test because that's telling you … there's something wrong with the underlying code" |
| R-T14-20 | **Once you're happy with the balance, balance checks come back as anchors** that lock it in. | "we'll come to a point where, all right, I'm happy with the balance, and then we can bring some of this stuff back in as grounding checks" |
| R-T14-21 | **Balance talk is about tendencies, not percentages.** Numbers belong on the bench where you can see a fight. | "20% is kind of just useless to me … we should go towards tendencies" |
| R-T14-22 | **The Covenant leans on shields at every size, frigates included, and is glass once they drop.** Per-ship tuning later. | "let's have that hold … not all covenant ships are built the same. So we'll have to do some tuning there" |
| R-T14-23 | **Counters come in tiers, never black and white: hard counter, favoured, even, each with a note on what can flip it.** This also settles the spec's bands question; the percentages are for the bench. | "It should never be black and white" · "we should have tiers to it" · "Yes, I like this." |
| R-T14-24 | **The role matchups in §3** (Artillery, Carrier, Brawler, Raider, Bodyguard). | per row in §3 |
| R-T14-25 | **Hammer is retired and folded into Brawler. The Halcyon becomes a Brawler.** | "we should retire the use of hammer … the hammer and bruiser are the same thing" · on "Brawler, is that right?": "Right." (the transcript heard "Robert") |
| R-T14-26 | **Bodyguard and Screen are two orders, not two ship types.** Any PD ship can guard one ship or screen the fleet, and neither is better at it. | "You should be able to toggle them … defend this guy, or take up the screen maneuver … It should not be one is better at the other" |
| R-T14-27 | **Every faction has one Line destroyer and one Hunter destroyer.** The Hillsborough becomes the UNSC's Line destroyer ("fine for now"), and the UNSC's PD job moves to a frigate. The Paris already is that frigate (§4.5). | "each faction should have a line destroyer, and a hunter destroyer, the PD for the UNSC should be for … one of the frigates" · "Yeah, that's fine for now." |

## 3. The role matchups (R-T14-24)
Claude proposed each row; you agreed or reshaped it. Tiers per R-T14-23. Your own example is marked.

| Role | Against | Tier | What flips it | Your answer |
|---|---|---|---|---|
| Artillery (Epoch, Infinity, RCS, ORS, Hierophant, Munificent) | Anvil | Artillery favoured | the Anvil reaches it before it's worn down | "Yes." |
| Artillery | Brawler | Brawler favoured | | "Yes." |
| Artillery | Raiders, alone | Raiders favoured | big guns track too slowly | "Yes." |
| **PD frigates (MAC + PD)** | **Carrier** | **Hard counter, PD wins ("no diff")** | | **your example**: they shred the fighters, then the carrier has almost no guns |
| Carrier (Spirit of Fire, Kerel, Lucrehulk) | Artillery | Carrier favoured, medium-to-high | **an Artillery first strike before the fighters arrive can flip it** (yours) | "a medium difficulty to high difficulty win for the carrier" |
| Carrier | Raiders, unescorted | **Depends on the raider** | | "Depends on the raiders" |
| Brawler (Providence, Subjugator, now Halcyon) | Artillery | Brawler favoured | | "Yeah, I like that." |
| Brawler | Anvil | Even | positioning | "Yeah, I like that." |
| Brawler | Carrier | Brawler favoured if it reaches the carrier | the carrier's range control | "Yeah, I like that." |
| **PD frigates** | **Brawler capital** | **Brawler wins** | frigates can't get close | **your example** |
| Raider (Stalwart, SCC, Diamond) | Hunter (Halberd, SDV, Geonosian) | Hard counter, Hunter wins | | "Yeah, I like that" |
| Raider | Lone Artillery | Raider favoured | the Artillery spotting them early | "Yeah, I like that" |
| Raider | Escorted carrier | Escorts win | | "Yeah, I like that" |
| Bodyguard / PD frigate (Paris, Makar, Hardcell) | Strike craft | Hard counter | | "Agreed." |
| Bodyguard | Raiders chasing its charge | Bodyguard favoured while it stays close | pulled away, it loses | "Agreed." |
| Bodyguard | Any real warship, alone | Loses badly | | "Agreed." |

**Not ruled:** Claude's Line matchups (even against Line; beats Bodyguards and Raiders that stand and fight; loses to Brawlers and Artillery). You stopped that row to cut back the number of roles. The Screen matchups were superseded by R-T14-26.

**What the plays now look like** (from `data/combat/playbook_v54.json`, with today's changes):
- **Frigates:** Bodyguard, Raider.
- **Destroyers:** Line, Hunter. Screen becomes an order.
- **Cruisers:** Anvil, Artillery, Brawler (new to cruisers; Hammer gone).
- **Capitals and super capitals:** Carrier, Artillery, Brawler.

## 4. Checked in text afterwards (what I said I'd look up)

**4.1 The attack jump's ~10 % shields (correction).** In the car I first said the jump drains the shields, then that I wasn't sure. The real cause: the attack jump picks its landing distance so the fleet's shields have time to refill before contact (your 26 Oct rule). At ×0.1 a full refill takes about 1,193 s instead of 119 s, so the same stand-off only buys about 10 %. FIXA's stopgap (`attack_land_v54`) sizes the landing at the old refill time. R-T14-13 fixes the cause: a fleet that has just landed isn't being shot, so it refills at the normal rate.

**4.2 The MAC rule holds.** After V54's ×2, the longest non-MAC guns are the mass driver at 26,000, then the projector and Siege Plasma Cannon at 22,000 and the heavy turbolaser at 19,000. The Heavy MAC (28,000), the Infinity MAC (34,000) and the Super MAC (40,000) beat them all. Two things sit outside the rule:
- The **railgun** (23,000) is mounted on no hull.
- **The FX-12 ion guns, at 52,224, would outrange the Super MAC once they're switched on.** They're the Subjugator's special weapon, OFF until Astra's Stage 2. **Open: is that the one allowed exception?**

The MACLONGEST check gets rewritten to your rule (Heavy and Super-heavy MAC beat every capital gun).

**4.3 The contact radius (36,000).** It's the distance at which the game counts a hostile as "near". Inside it, a hull drops out of fast travel, a fleet counts as in contact, the AI starts its approach, a jump aborts, and the coarse resolver stops the disengagement. It's proximity only. R-T14-13/17 add a second trigger: being hit, at any range. Source: `sim/operational/hull/ship.gd` §12.3, §11.46.

**4.4 The 3D toolkit (S3D-01 Q4). Done by Claude after the talk, at your request.** The toolkit's files only existed in an earlier chat, and none were saved to the PC. Claude rebuilt the toolkit by replaying every file write and edit in that chat, in order. As a check, the replay stopped at the 24 Oct v1 point is byte-identical to the saved v1 copy. It's now back in the project's skills folder, and both self-tests pass; every Path R script imports. Two old example specs can't be recovered; Path R doesn't use them.

**4.5 The roles in the data.**
- The Paris is already the UNSC Bodyguard: Light MAC plus three PD guns, your carrier-killer frigate.
- **The Hillsborough was never a PD ship.** I called it "mostly point defence" in the car, from my own spec table. Its real loadout is a Light MAC, two coilguns and one PD. You ruled it a Screen on 27 Oct, but Line fits what it carries.
- The other destroyers are Hunters (Halberd, SDV, Geonosian) and Line (CPV, Recusant), as I said.

**4.6 The jump circle (correction).** 40,000 is the circle's **radius** (`warp_radius_u` in `data/traffic/traffic.json`), so it's 80,000 across. I said "40,000 across" in the car. It's an unratified number from the X6 fleet link. The small jump point used elsewhere is 2,600 radius (`JumpPoint.RADIUS`).

**4.7 Sections vs modules (GAP-53 Q7).** You were right. Since V36 the game runs `damage_model: "panels"` (`data/combat/model.json`): hits go to armour panels over modules (engineering, flight control and so on), and **guns are never lost**. The old section system (chop the hull into parts, a dead part takes its guns offline) is switched off as a damage model. Sections still exist in the data, for breakup layouts and binding mounts, but nothing goes dark when one "dies". So Astra's question 7 ("which guns go dark with which section") rests on a model the game doesn't use.

**4.8 The Subjugator's centre blast.** Your theory is half right. The blast is tied to one split, the S03–S05 seam, **and** it only fires when all five pieces separate singly (all eight seams open). In 13 real deaths, one to four seams always held, so it never fired. Your fix ("move the blast to the split that does happen") is close to SHOTFX's option (a). It's a sim change and a hash event. Source: `data/deaths/pr_b5_subjugator_center.json`.

**4.9 FX-11.** Re-read this evening: `APPROVAL_STATUS.json` still says `exact_archive_approved: false`, unchanged since 9:19 pm on 29 Oct. If you accepted it in Astra's chat, it wasn't written down.

## 5. Open
| # | Question | Note |
|---|---|---|
| T14-O1 | **GAP-53 Q7:** tell Astra sections aren't a live damage system, keep the Citadel's two sections as data and skip the fitting work? | §4.7; Claude's suggestion, not your ruling |
| T14-O2 | **Subjugator centre blast:** release it on whichever main split actually happens? | §4.8; your theory, parked |
| T14-O3 | **The FX-12 ion guns outrange the Super MAC.** The one allowed exception? | §4.2 |
| T14-O4 | **The jump area's size:** a number for "about big enough for the largest ship" (2,600 radius as on the campaign boards?) | §4.6 |
| T14-O5 | Line matchups; Screen and Bodyguard as orders, and how the player gives them | §3 |
| T14-O6 | Balance spec Q4 (what "equal cost" means) and Q5 (which pairings the bench proves first) | not reached |
| T14-O7 | V55: when, and what goes in beyond the full gate | not reached |
| T14-O8 | Out of battle: does a hostile inside the contact radius also count as "in battle", or only hits? | R-T14-13; Claude's question |

## 6. Claude's readings to strike
- T14-G1: "drops out 60 s after its last hit" also means 60 s after it last *lands* a hit? (You only said "shot at".)
- T14-G2: R-T14-13's "normal rate" is V53's per-hull recharge, the bench-edited recharge untouched (D-V54-WEAPONS-03).
- T14-G3: R-T14-26 Bodyguard/Screen orders live on any PD ship, which today is the Paris, Makar and Hardcell (frigates). Destroyers lose the Screen play.
- T14-G4: Under R-T14-19, MACLONGEST, PLAYBEHAVE's outcome bars, the duel-ends checks and the counter rows become printed reports, not reds. SYMMETRY/DETERMINISM/OLDMODEL-style checks stay gates.

## IDs
| ID | What it is |
|---|---|
| R-T14-1 … 27 | Today's rulings |
| T14-O1 … O8 | Open questions |
| T14-G1 … G4 | Claude's readings to strike |
| INT-01, S3D-01, GAP-53, FX-11, FX-12 | Astra tasks |
| V54, V55 | The last build (committed 4e359b0d) and the next (the full gate) |
