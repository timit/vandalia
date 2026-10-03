# vandalia (van build)

last updated: 2026-10-03

2021 mercedes sprinter 144" 4x4 (OM642 V6 diesel), being converted into a travel and camping van. this repo holds the plan for each subsystem. electrical is first.

## goal

a reliable, serviceable van build with a traditional 24V victron electrical system, water, heat, and cooling that i can install and repair myself, and that works off-grid and in cold weather.

## subsystems

| folder | status |
|---|---|
| electrical/ | active. design settled, parts being bought. |
| plumbing/ | not started. |

add new subsystems (heating, audio, exterior, and so on) as new folders.

## now and next

- done: electrical design settled. most parts ordered, including the DJI branch parts (3131 box and 7210 breaker).
- now (2026-10-03): electrical docs restructured into electrical/README.md (as-built) and electrical/PLAN.md (design, install order, supplies checklists), replacing wiring.md/diagrams.md/parts.md. install actually started: shore inlet, 8077, all 4 BAOMAIN-row switches, both mounted battery selectors, and the multiplus are mounted; no wiring pulled yet. two design additions adopted and parts obtained this session: the negative busbar downsized to a second 4-stud egis 6600-404, and a 24V-to-12V converter (orion-tr smart 24/12-30) plus a third battery selector giving the 5026 12V bus the same DJI/victron redundancy every other circuit has — see electrical/PLAN.md.
- next: measure every cable run (electrical/measurements.md) before cutting, work through electrical/PLAN.md's installation checklists in order, settle the remaining items in electrical/verify.md.
- later: plumbing.

## layout

- README.md: this file. shared facts for the whole build.
- CLAUDE.md: working rules for claude code. it imports this README.
- reference/: manuals and datasheets, shared across subsystems.
- electrical/: README.md (as-built), PLAN.md (design, install order, supplies), measurements.md, verify.md
- plumbing/: placeholder

## van

- 2021 mercedes-benz sprinter, 144" wheelbase, 4x4, OM642 V6 diesel
- alternator rating: 180A or 220A stock, depending on build variant (confirmed by sprinter parts suppliers and OEM listings, 2026-10-03) — the exact figure is printed on the alternator's own back cover, worth a physical check for certainty, but either option clears the XS's 60A draw with comfortable headroom left for the van's other factory 12V loads
- weight budget: TBD (the SOK weighs about 70 lb)

| item | location | notes |
|---|---|---|
| 24V SOK battery bank | under the bed, near the cargo doors | second SOK planned later |
| velit 2000R rooftop AC | existing maxxair roof hole, enlarged to 14 x 14 in | |
| starlink mini | roof box | cable pass-through still being decided |
| fresh water tank | 35-gallon spare-tire-replacement tank | plumbing |
| multiplus, cerbo, class T block, busbars | TBD | see electrical/measurements.md |
| shore inlet | TBD | keep the run to the 8077 short |
| 8077 and 8027 panels | TBD | each back needs protection |

## electrical design and decisions

24V victron system with the existing DJI power 2000 kept as a second independent source, manual switches choosing which system feeds each circuit (no ATS). full design, the switch/selector map, install order, and supplies are in electrical/PLAN.md. what's actually confirmed built is in electrical/README.md.

## load budget

nameplate watts only. replace TBD with the number from the label or manual, and note where it came from.

| source | capacity | notes |
|---|---|---|
| SOK 24V 150Ah | 3,840Wh; 150A continuous, 800A/10s peak (corrected from an earlier 200A/500A estimate — see reference/SK24V150PH.pdf) | second SOK planned |
| multiplus-ii 24/3000/70 | 3000VA, about 2,400W continuous | 70A charger; input limit 30A shore, about 14A honda, 16A household outlet (20A circuit, 80% continuous-load derate) |
| DJI power 2000 plus expansion battery | 4,096Wh | AC input 15A max; AC output 4 ports, 100-120V/25A ≈ 3000W continuous (US variant, confirmed 2026-10-02 at dji.com/power-2000/specs — not in the manual itself); SDC-to-XT60 cable (feeds the 5026 12V bus) is 13.6V default, 10A max — corrected from an earlier 12A figure, see load budget check 4 below |
| honda EU2200i | 1,800W continuous | plugs into the shore inlet |
| shore power | 30A | about 3,600W at 120V |
| orion XS 1400 | 50A at 24V (about 1,200W) | set the input limit, about 60A; alternator rating verify |
| orion-tr smart 24/12-30 isolated (adopted and obtained 2026-10-03, not yet installed) | 30A at 12V, 360W rated | DC-DC step-down for the 5026 bus's victron leg (battery selector 3, position 2); input-side current/fuse sizing not yet verified against its own manual — see electrical/verify.md |

| load | system | voltage | watts | notes |
|---|---|---|---|---|
| oven (typhur CV03 sync oven) | 20A oven/cooktop circuit, BAOMAIN 2 - oven/cooktop AC source switch + BAOMAIN 4 - oven/cooktop AC destination switch | 120V AC | 1750W rated | reference/Typhur_CV03SyncOven.pdf; mechanically interlocked with the cooktop (BAOMAIN 4 - oven/cooktop AC destination switch), never live at the same time |
| cooktop (empava EMPV-12EC07) | 20A oven/cooktop circuit, BAOMAIN 2 - oven/cooktop AC source switch + BAOMAIN 4 - oven/cooktop AC destination switch | 120V AC | 1800W total | reference/EMPV-12EC07_Manual.pdf — its own spec table requires a **minimum 20A breaker**, which is why this circuit is 20A and interlocked rather than sharing a 15A branch with anything else |
| fridge (deaprull D31A) | 15A fridge+USB circuit, BAOMAIN 3 - fridge/receptacle AC source switch | 120V AC (confirmed — dual-voltage unit, DC 12/24V also available but not used) | 35-45W running | cycles; dual-voltage per the manufacturer's other listings and an independent review, not the spec-sheet screenshot on file (reference/DEAPRULL_ D31A.png), which had a wrong-looking "0.4 kWh annual" figure |
| USB charging outlet | 15A fridge+USB circuit, BAOMAIN 3 - fridge/receptacle AC source switch | 120V AC (confirmed — an outlet with built-in USB ports, not a 12V DC adapter) | TBD, likely 30-60W | shares the 15A branch with the fridge |
| velit 2000R | battery selector 2 (direct 24V bus tap, or DJI-fed meanwell RSP-1000-24) | 24V DC | 720W rated (24V variant, 10-33A DC) | reference/Velit_2000R_User_Manual_2609.pdf; meanwell (DJI leg only, 2026-09-21) max 1,000W |
| water heater (ecosmart eco mini 4) | TBD | 120V AC | TBD | |
| autoterm air 2D | 24V (not designed) | 24V DC | TBD | |
| USB panels (4 x 108W) | 12V, blue sea 5026 | 12V DC | up to 432W | rarely all at once |
| LED pucks and strips | 12V, blue sea 5026 | 12V DC | TBD | |
| starlink mini | 12V, blue sea 5026 | 12-48V DC | TBD | continuous |
| water pump (shurflo 4008) | TBD | TBD | TBD | intermittent |
| cerbo GX MK2 | 24V bank | 24V DC | TBD | continuous |
| raspberry pi 5 and home assistant gear | TBD | TBD | TBD | continuous |

checks to run once the watts are filled in:

1. worst-case AC watts on the victron side against the multiplus's 2,400W continuous. **resolved for the kitchen (2026-10-02)**: oven (1750W) and cooktop (1800W) combined would be 3550W, exceeding the multiplus — but BAOMAIN 4 - oven/cooktop AC destination switch mechanically interlocks them, so the real worst case is max(oven, cooktop) + fridge+USB ≈ 1800 + 105 ≈ 1905W, comfortably under 2,400W. water heater watts still TBD and still need adding to this check once known.
2. the same worst case against the honda's 1,800W and the DJI's AC output when running on a backup source. **kitchen note**: oven and cooktop are victron/8027-sourced on their victron leg but can also take the DJI leg via BAOMAIN 2 - oven/cooktop AC source switch — ~1905W worst-case is only marginally over the honda's 1800W (~105W, essentially the fridge+USB draw) if cooking on generator power, a small and likely tolerable overage compared to the ~1795W overage the un-interlocked single-branch design would have had. DJI's AC output (confirmed 2026-10-02: ~3000W continuous) clears this worst case comfortably. the velit's DJI leg (position 1, via the meanwell) is still AC and still counts here too.
2a. the velit's direct-DC leg (33A max) against the 24V bus's actual capacity alongside everything else already drawing from it (XS charging, cerbo, the multiplus itself) — not yet checked.
3. daily energy use in Wh against the SOK's 3,840Wh.
4. the 12V bus load against its source. **adopted 2026-10-03**: the DJI SDC-to-XT60 feed alone (13.6V default, 10A max, about 136W) was a real ceiling against the USB panels' 432W rated draw — resolved by adding battery selector 3 and an orion-tr smart 24/12-30 converter (30A/360W at 12V) as a second, higher-capacity source. real continuous load (LED pucks + starlink, both still TBD) against either leg individually is still worth checking once those watts are known.

## interfaces between subsystems

| item | owner | touches | connection | status |
|---|---|---|---|---|
| shurflo 4008 water pump | plumbing | electrical | circuit and voltage TBD | TBD |
| interior water heater (ecosmart eco mini 4, 120V) | plumbing | electrical | AC circuit source and breaker TBD; switched by a 15A rocker | TBD |
| tank level sender (kus S5U-10) | plumbing | monitoring | ADS1115 ADC on an ESP32 running esphome for home assistant | planned |
| velit 2000R rooftop AC | HVAC | electrical | 24V DC, source chosen by battery selector 2 — direct 24V bus tap, or DJI AC out via meanwell RSP-1000-24 (2026-09-21) | designed |
| kitchen circuit: fridge + USB outlet | kitchen | electrical | 15A branch, source chosen by BAOMAIN 3 - fridge/receptacle AC source switch | designed |
| kitchen circuit: oven + cooktop | kitchen | electrical | 20A branch, source chosen by BAOMAIN 2 - oven/cooktop AC source switch, load (oven vs. cooktop) interlocked by BAOMAIN 4 - oven/cooktop AC destination switch | designed |
| autoterm air 2D 24V diesel heater | heating | electrical | 24V feed, fusing, and failover power TBD | not designed |
| starlink mini | networking | electrical | 12-48V input, on the 5026 bus | existing |
| 12V loads (LED pucks, USB panels) | electrical | lighting | blue sea 5026, source chosen by battery selector 3 — DJI SDC feed, or orion-tr smart 24/12-30 off the 24V bus (adopted 2026-10-03) | designed |
| exterior shower (camplux F10 ultra, propane) | plumbing | gas | propane supply TBD | not designed |

when a plumbing or other part draws power, add it to the load budget above and give it a circuit in this table.
