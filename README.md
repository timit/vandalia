# vandalia (van build)

last updated: 2026-09-21

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
- now: west marine trip for the busbars, class T block and fuse, tinned wire, the 5123 ANL fuse, and the 5065 holder.
- next: measure every cable run (electrical/measurements.md), get nameplate watts for the load budget, add manuals to reference/, and settle the items in electrical/verify.md.
- decide later: whether to add the 24V-to-12V converter and a third battery selector switch for the 5026 bus (renamed from "battery selector 2" on 2026-09-21 — that switch now belongs to the velit, see below) — driven partly by the fuse/source mismatch on that bus now open in electrical/verify.md (the feed is 13.6V/10A max, but it's fused at 40A).
- later: plumbing.

## layout

- README.md: this file. shared facts for the whole build.
- CLAUDE.md: working rules for claude code. it imports this README.
- reference/: manuals and datasheets, shared across subsystems.
- electrical/: parts.md, wiring.md, diagrams.md, measurements.md, verify.md
- plumbing/: placeholder

## van

- 2021 mercedes-benz sprinter, 144" wheelbase, 4x4, OM642 V6 diesel
- alternator rating: verify (needed for the orion XS input limit)
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

## key electrical decisions

- 24V bank, not 12V.
- keep the existing DJI power 2000 system as a second independent source. manual selector switches choose which system feeds each circuit. no ATS.
- orion XS 1400 is the alternator DC-DC charger (replaced the orion-tr smart 12/24-15, which is being returned).
- class T fuse on the battery main, not ANL or mega (lithium fault current).
- ANL fuses only on the XS input and output. keep those runs short (ANL interrupt rating is 6,000A at 32V).
- no smartshunt. the SOK reports state of charge over CAN.
- the generator plugs into the shore inlet. there is no second inlet.
- switch position convention (2026-09-21): position 1 is always the DJI leg, position 2 is always the victron leg, on every switch split between the two systems — matches the physical layout (DJI driver side/left, victron passenger side/right) to the switch throw direction.
- BAOMAIN 3 routes shore/generator power to the DJI (position 1) or the victron (position 2).
- battery selector 1 shares the DJI charger's installed, 100A-fused van feed between the DJI car charger (position 1) and the orion XS (position 2). only one draws at a time.
- battery selector 2 (2026-09-21) chooses the velit's power source directly on the DC side: position 1 is the DJI-fed meanwell RSP-1000-24, position 2 taps the 24V bus. recovers the inverter+meanwell round-trip conversion loss (about 17%, from the real datasheet efficiency figures) when the velit runs on battery power, without losing the DJI backup path. BAOMAIN 2 is no longer used and is spare — see electrical/wiring.md and electrical/verify.md.
- the blue sea 8077 (30A main) sits before BAOMAIN 3, so one main protects both branches.
- the DJI AC input branch gets its own 15A breaker (DJI AC input max is 15A).
- blue sea 5026 (12V fuse block) stays on the DJI 12V feed for now. a 24V-to-12V converter is a later option.
- one chassis bond, on the negative busbar only. no neutral-ground bond in any panel (the multiplus grounds neutral internally).

## load budget

nameplate watts only. replace TBD with the number from the label or manual, and note where it came from.

| source | capacity | notes |
|---|---|---|
| SOK 24V 150Ah | 3,840Wh; 150A continuous, 800A/10s peak (corrected from an earlier 200A/500A estimate — see reference/SK24V150PH.pdf) | second SOK planned |
| multiplus-ii 24/3000/70 | 3000VA, about 2,400W continuous | 70A charger; input limit 30A shore, about 14A honda, 16A household outlet (20A circuit, 80% continuous-load derate) |
| DJI power 2000 plus expansion battery | 4,096Wh | AC input 15A max; SDC-to-XT60 cable (feeds the 5026 12V bus) is 13.6V default, 10A max — corrected from an earlier 12A figure, see load budget check 4 below |
| honda EU2200i | 1,800W continuous | plugs into the shore inlet |
| shore power | 30A | about 3,600W at 120V |
| orion XS 1400 | 50A at 24V (about 1,200W) | set the input limit, about 60A; alternator rating verify |

| load | system | voltage | watts | notes |
|---|---|---|---|---|
| oven | kitchen circuit (BAOMAIN 1) | 120V AC | TBD | |
| cooktop | kitchen circuit (BAOMAIN 1) | 120V AC | TBD | |
| fridge | kitchen circuit (BAOMAIN 1) | 120V AC | TBD | cycles |
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

1. worst-case AC watts on the victron side (kitchen plus water heater) against the multiplus's 2,400W continuous. the velit no longer counts here on its normal (battery selector 2, position 2) leg — it's a direct 24V DC draw, not an AC load, as of the 2026-09-21 redesign.
2. the same worst case against the honda's 1,800W and the DJI's AC output when running on a backup source — the velit's DJI leg (position 1, via the meanwell) is still AC and still counts here.
2a. the velit's direct-DC leg (33A max) against the 24V bus's actual capacity alongside everything else already drawing from it (XS charging, cerbo, the multiplus itself) — not yet checked.
3. daily energy use in Wh against the SOK's 3,840Wh.
4. the 12V bus load against the DJI SDC-to-XT60 feed: 13.6V default, 10A max per DJI's own cable spec (about 136W) — the USB panels alone can ask for up to 432W, so this is the real ceiling on that bus, not the 40A ANL fuse currently on it (see electrical/verify.md).

## interfaces between subsystems

| item | owner | touches | connection | status |
|---|---|---|---|---|
| shurflo 4008 water pump | plumbing | electrical | circuit and voltage TBD | TBD |
| interior water heater (ecosmart eco mini 4, 120V) | plumbing | electrical | AC circuit source and breaker TBD; switched by a 15A rocker | TBD |
| tank level sender (kus S5U-10) | plumbing | monitoring | ADS1115 ADC on an ESP32 running esphome for home assistant | planned |
| velit 2000R rooftop AC | HVAC | electrical | 24V DC, source chosen by battery selector 2 — direct 24V bus tap, or DJI AC out via meanwell RSP-1000-24 (2026-09-21) | designed |
| kitchen circuit (oven, cooktop, fridge) | kitchen | electrical | source chosen by BAOMAIN 1 | designed |
| autoterm air 2D 24V diesel heater | heating | electrical | 24V feed, fusing, and failover power TBD | not designed |
| starlink mini | networking | electrical | 12-48V input, on the 5026 bus | existing |
| 12V loads (LED pucks, USB panels) | electrical | lighting | blue sea 5026, fed from DJI SDC for now | existing |
| exterior shower (camplux F10 ultra, propane) | plumbing | gas | propane supply TBD | not designed |

when a plumbing or other part draws power, add it to the load budget above and give it a circuit in this table.
