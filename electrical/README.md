# electrical: as-built

last updated: 2026-10-03

this file only records what's actually true of the physical system — confirmed installed, or a permanent fact about a part already in hand (nameplate/datasheet specs, which don't change based on install status). it grows as PLAN.md's checklists get checked off. for the design and the plan to get there, see PLAN.md. for open questions, see verify.md.

## install progress

mounted: the shore inlet, blue sea 8077, BAOMAIN 1, BAOMAIN 3, BAOMAIN 2, battery selector 1, battery selector 2, and the multiplus. that's the mounting half of ac input's first install step — none of the actual wiring has been pulled yet, and nothing is energized.

separately, the van feed's 6 AWG wire has been run from the starter battery (under the driver seat) to the rear, with its AEP 100A fuse inline — not yet landed on anything. this is ahead of sequence (it's a dc positive and alternator step) but doesn't need rework; it just waits for the DC backbone to be wired first.

not yet mounted: the busbars (placement still open — see measurements.md), the orion XS, the class T fuse block, BAOMAIN 4, and battery selector 3.

## confirmed part specs

facts below are from the part's own manual, nameplate, or a photo of the actual unit — not estimates. organized to match PLAN.md's sections.

**dc positive and alternator**
- orion XS 1400: screw terminals (IN/GND/OUT), no lug, max 4 AWG cable. torque: 4 AWG 50 in-lb, 6-10 AWG 40 in-lb, 8-12 AWG 25 in-lb. victron recommends a dedicated 60-70A external fuse for this unit specifically.
- battery selectors (all 3, aramox 300A off-1-2): M10 studs, terminals labeled "OUTPUT" (common), "1", "2". printed rating 300A continuous, 500A for 5 min, 900A for 30 sec.
- egis powerbar 6600-404 (both bars): M10/3/8" studs, 1-1/4" stud length (confirmed — clears stacking 3 ring lugs), 600A continuous, 70-80VDC max. torque 120-140 in-lb.
- egis 3912B class T fuse block: M8 studs (not 3/8" as originally assumed), 225-400A, 80VDC max, torque 190 in-lb max.
- eaton/bussmann JJN-300 class T fuse: 300A, 300VAC, 200kA AIC interrupt rating.
- SOK SK24V150PH: 3.84kWh nominal, 150A continuous discharge, 170A@60s/800A@10s peak. terminal torque 9-11 N·m. max 150A per terminal/cable pair. charge voltage 28V, float 27.6V.
- meanwell RSP-1000-24: 40A rated output, 960W rated power (not 1000W — that's the series name), 20-26.4V adjustable output, 88% typical efficiency. draws up to 12A at 115VAC full load, 25A inrush. AC input terminal torque 18 kgf-cm; DC output torque 10 kgf-cm. ships with remote-on/off pins shorted (always on when AC present). +V output has a built-in inline fuse; -V does not.
- velit 2000R (24V variant): 720W rated, 10-33A operating current. ships with its own 6 AWG DC cable, fused both ends at the velit, positive only at the source end.
- DJI power 2000: AC output auto-shuts-off after 30min with no load, shuts down fully after 60min with no input/output. expansion battery port 40.0-58.4V DC, max 60A/3000W.
- DJI super fast charger (DYS_DC1000): not water or dust resistant. 12-45V DC in, max 70A/1000W. ships with a 100A fuse. default charging power 500W.

**dc negative and ground**
- chassis bond lands on an existing factory grounding stud, driver side near the ceiling, 1/4-20 thread (smaller than every other stud in this build).

**ac input**
- multiplus-ii 24/3000/70: 3000VA, ~2,400W continuous. 2 AC outputs — AC-out-1 (uninterruptible, 50A rated), AC-out-2 (32A, not used in this build). AC-in/AC-out are screw terminal blocks (N/PE/L), torque 2 Nm. victron's own chart calls for 6 AWG minimum at this unit's full 50A rating.
- blue sea 8077: on LED and reverse-polarity LED, panel footprint about 2.63 x 3.75in.
- BAOMAIN cam switch (all 4 units): Ith 32A confirmed on the nameplate, 660V rating. M4 terminal screw, accepts 2.5-6.0mm² wire, torque 1.2 N·m.
- blue sea 7210: terminal torque 14 in-lb, mounting-screw torque 6 in-lb.

**ac loads**
- blue sea 8027: main + 6, 30A main, three 15A branches pre-installed, three positions open. neutral bus and ground bus physically separate inside the panel (confirmed via blue sea's own wiring diagram).
- typhur CV03 sync oven: 1750W, 120VAC/60Hz, 26L, 24lb, plug-in.
- empava EMPV-12EC07 cooktop: 1800W total, 120VAC/60Hz. manufacturer-stated minimum circuit breaker amperage: 20A. requires hardwiring by a qualified technician — no plug.
- deaprull D31A fridge: dual-voltage (AC 120/240V or DC 12/24V), 35-45W running, as low as 35W in eco-mode. running on AC in this build.

**12V bus**
- blue sea 5026: 12-circuit fuse block with negative bus, mounts with #8 or M4 screws at 2.5in spacing, terminal screws #8-32. upstream feed fuse capped at 125A max by blue sea's own spec.
- DJI SDC-to-XT60 cable (feeds the 5026): 13.6V default, 10A max — not 12A as originally assumed.

**data cables**
- cerbo GX MK2 (PN BPP900450110): 2 fully configurable VE.Can ports (not a fixed BMS-Can port like the original Cerbo GX). ships with power cable (inline 3.15A slow-blow fuse, M8 ring eyes already attached), terminal blocks, and 2x VE.Can terminators.
