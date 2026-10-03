# parts: have and need

last updated: 2026-10-03

one item per line, checklist style: `[x]` purchased/in hand, `[ ]` still needed. categories mirror wiring.md/diagrams.md's own sections (dc positive and alternator, dc negative and ground, ac input, ac loads, 12V bus, data cables), plus lugs and tools/supplies since those cut across circuits. for the reasoning behind a choice, the full history, or open questions, see wiring.md and verify.md.

## dc positive and alternator

- [x] SOK SK24V150PH, 24V 150Ah, 3.84kWh — main battery bank
- [x] victron orion XS 1400, 1-50A adjustable — alternator DC-DC charger
- [x] battery selector switch, 300A off-1-2 — selector 1, van feed to XS/DJI charger
- [x] battery selector switch, 300A off-1-2 — selector 2, velit source
- [x] egis powerbar 6600-404, 4-stud — positive busbar. [west marine](https://www.westmarine.com/egis-mobile-electric-powerbar---four-m103-8inch-studs-4-circuits-8---600-amp-21976824.html)
- [x] egis mobile electric 3912B class T fuse block, M8 studs — battery main fuse holder. [west marine](https://www.westmarine.com/egis-mobile-electric-class-t-fuse-block-225---400-a-sealed-21481650.html)
- [x] eaton/bussmann JJN-300 limitron class T fuse, 300A — battery main fuse. [west marine](https://www.westmarine.com/eaton-limitron-fast-acting-class-t-fuse-22185755.html)
- [x] 2x blue sea 5005 ANL fuse block, 5/16" studs — XS output fuse, velit direct-DC tap fuse
- [ ] blue sea 5123, 60A ANL fuse — XS output
- [ ] blue sea 5165, 40A ANL fuse — velit direct-DC tap
- [x] pacer marine tinned copper battery cable, 15ft #6 red — selector/XS/busbar positive runs
- [x] pacer marine tinned copper battery cable, 8ft #2/0 red — positive 2/0 runs
- [x] meanwell RSP-1000-24 — AC-to-24VDC supply for the velit, DJI leg
- [x] velit 2000R rooftop AC, 24V DC, 720W — rooftop air conditioner
- [ ] molded-plug 12-14 AWG appliance cord — DJI AC output to meanwell
- [x] DJI power 2000 + expansion battery 2000 — secondary AC/DC power system
- [x] DJI super fast charger (DYS_DC1000) — alternator-to-DJI charger

## dc negative and ground

- [x] egis powerbar 6600-404 — negative busbar, replaces the 6600-804
- [ ] return egis powerbar 6600-804 — superseded by the 6600-404 above
- [x] pacer marine tinned copper battery cable, 15ft #6 black — negative-side runs
- [x] pacer marine tinned copper battery cable, 10ft #2 black — chassis bond
- [x] pacer marine tinned copper battery cable, 8ft #2/0 black — negative 2/0 runs
- [ ] 2 AWG lug, 1/4" hole, x1-2 — chassis bond
- [ ] 10 AWG single-conductor cable — multiplus exterior grounding point to negative bar

## ac input

- [x] victron multiplus-ii 24/3000/70, 120V, 3000VA — main inverter/charger
- [x] blue sea 8077, 30A double-pole main — shore/generator main breaker
- [x] conntek 30A 125V stainless shore inlet
- [x] carlon E987N-3-HD enclosure, 4x4x4in — houses the 8077. [home depot](https://www.homedepot.com/p/Carlon-4-in-x-4-in-x-4-in-Gray-Electrical-PVC-Junction-Box-E987N-3-HD-E987N-3-HD/100404095)
- [x] southwire 10 AWG 3-conductor SOOW cord, 15ft — shore inlet to 8077. [lowe's](https://www.lowes.com/pd/Southwire-10-AWG-3-Black-Power-Cord-By-the-Foot/50148254)
- [x] BAOMAIN 32A cam changeover switch, SZW26-32/D202.2D — BAOMAIN 1, shore AC destination
- [x] blue sea 3131 circuit breaker enclosure — DJI AC-input branch
- [x] blue sea 7210, 15A toggle breaker — DJI AC-input branch
- [x] 12 AWG 12/3 triplex marine wire, 20ft — DJI AC-input branch
- [ ] 10 AWG 3-conductor cable — 3 interior AC runs
- [ ] surface-mount outlet box w/ 15A/20A receptacle — DJI AC-input branch
- [x] honda EU2200i generator, 1,800W — backup/shore AC source

## ac loads

- [x] blue sea 8027, main + 6, 30A main — AC branch panel
- [x] carlon E989N-CAR enclosure, 8x8x4in — houses the 8027. [home depot](https://www.homedepot.com/p/Carlon-8-in-x-8-in-x-4-in-Gray-Electrical-PVC-Junction-Box-E989N-CAR-E989N-CAR/100404099)
- [x] BAOMAIN 32A cam changeover switch — BAOMAIN 3, fridge/receptacle AC source. [amazon](https://www.amazon.com/Baomain-Universal-Changeover-SZW26-32-D202-2D/dp/B09MMQPQQH)
- [x] BAOMAIN 32A cam changeover switch — BAOMAIN 2, oven/cooktop AC source
- [x] BAOMAIN 32A cam changeover switch — BAOMAIN 4, oven/cooktop AC destination
- [x] 2x blue sea 7214, 20A toggle breaker — oven/cooktop circuit (1 spare)
- [x] 12 AWG 12/3 triplex marine wire, 20ft — oven/cooktop circuit
- [x] 14 AWG 14/3 triplex marine wire, 20ft — fridge+USB circuit
- [x] iron forge 12/3 SJTW molded-plug cord, 15ft — DJI AC-output tap, fridge/USB leg
- [x] iron forge 12/3 SJTW molded-plug cord, 6ft — DJI AC-output tap, oven/cooktop leg
- [x] typhur CV03 sync oven, 1750W — kitchen oven
- [x] empava EMPV-12EC07 induction cooktop, 1800W — kitchen cooktop, hardwired
- [x] deaprull D31A fridge, 35-45W, 120VAC — kitchen fridge
- [ ] USB charging outlet, 120VAC w/ USB-A/USB-C — kitchen, specific product TBD
- [ ] receptacles x3 — fridge, USB outlet, oven
- [ ] GFCI breaker, blue sea 309x/310x series — 8027 AC-out-1

## 12V bus

- [x] blue sea 5026, 12-circuit fuse block — 12V bus (LED pucks, USB panels, starlink)
- [x] victron orion-tr smart 24/12-30 isolated, 30A/360W — 5026 bus's victron-leg converter. [amazon](https://www.amazon.com/dp/B086R9ZVK5)
- [x] battery selector switch, 300A off-1-2 — selector 3, 5026 bus source
- [ ] blue sea 5065 holder + 10-15A ATC fuse — DJI SDC to 5026 feed
- [ ] blue sea 5026 branch fuses, 4x 10A ATC — USB panels
- [ ] 10 AWG lug, 3/8" hole, x3 — selector 3 connections

## data cables

- [x] victron cerbo GX MK2 (PN BPP900450110) — system monitor, CAN/DVCC hub
- [x] victron VE.direct cable, 2.95ft — orion XS to cerbo
- [x] victron RJ45 UTP cable, 0.9m — multiplus to cerbo

## lugs

- [x] seafit "#6-3/8" lug 5-pack — busbar and selector 6 AWG ends
- [x] seafit "#6-5/16" lug 5-pack — ANL block 6 AWG ends
- [ ] seafit "#6-3/8" lug 5-pack, x4 more — busbar and selector 6 AWG ends (only have 1 of 5 needed)
- [ ] return: 2x seafit "#2/0-5/16" lug 5-pack — wrong size, no use in this build
- [ ] 2/0 lug, M8 hole, x6 — SOK, class T block, multiplus
- [ ] 2/0 lug, 3/8" hole, x4 — busbar ends

## tools and other supplies

- [x] DxCRIMP hex ferrule crimper, AWG 24-4
- [x] ferrule set, 166pc, AWG 1/0-12
- [x] pro'skit 902-160 crimpro crimper, AWG 2-4-6 — for 6/4/2 AWG screw terminals
- [x] [IWISS battery cable lug crimping tool kit](https://www.amazon.com/IWISS-Battery-Crimping-Terminals-Stripper/dp/B09PYH9B4Q), AWG 8-4/0 — for the 2/0 ring lugs
- [ ] adhesive heat shrink
- [ ] cable cutter
- [ ] inch-pound torque wrench
- [ ] multimeter
- [ ] 1-1/8" hole saw
- [ ] 8x short jumper wires — BAOMAIN switch commons (10 AWG for BAOMAIN 1, 14 AWG for BAOMAIN 3, 12 AWG for BAOMAIN 2 and 4)
