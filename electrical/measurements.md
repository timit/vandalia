# measurements

last updated: 2026-10-03 (cargo layout update)

fill in the length column with a tape measure along the actual route, then add about 20% slack. keep the runs short: voltage drop and heat matter at these currents.

## cable runs

| run | gauge | length measured | length + 20% | lug ends |
|---|---|---|---|---|
| SOK+ to class T block | 2/0 red (pacer, 8ft reel — shared across all 2/0 red runs below, 2026-10-02) | | | M8 / M8 |
| class T block to + bar | 2/0 red (same 8ft reel) | | | M8 / 3/8" |
| + bar to multiplus+ | 2/0 red (same 8ft reel — the long unknown leg; measure before cutting, see PLAN.md) | | | 3/8" / M8 |
| SOK- to - bar | 2/0 black (pacer, 8ft reel — shared across both 2/0 black runs, 2026-10-02) | | | M8 / 3/8" |
| - bar to multiplus- | 2/0 black (same 8ft reel — the long unknown leg; measure before cutting, see PLAN.md) | | | 3/8" / M8 |
| starter battery to selector 1 (installed with DJI charger, AEP 100A/65VDC fuse at battery) | 6 AWG (confirmed marked on the wire, 2026-10-03) | under 15ft (stated) | | 5/16" |
| selector 1 to XS input | 6 AWG red (changed from 4 AWG — matches the rest of this circuit; pacer, 15ft reel shared across all 4 red 6 AWG runs below, 2026-10-02) | under 6ft (stated — under-bed run) | | XS terminal, verify |
| selector 1 to DJI charger | 6 AWG (as installed, same cable) | | | per charger kit |
| XS output to + bar (60A ANL near the bar) | 6 AWG red (same 15ft reel) | under 6ft (stated — under-bed run) | | 5/16" / 3/8" |
| XS GND to - bar | 6 AWG black (changed from 4 AWG — matches XS output, same current and run length; pacer, 15ft reel shared across both black 6 AWG runs, 2026-10-02) | under 6ft (stated — under-bed run) | | 3/8" |
| + bar to velit selector 2 pos 2 (direct DC tap, 40A ANL near the bar) | 6 AWG red (same 15ft reel as selector 1/XS) | short — selector 2 is directly above the SOK/busbars (confirmed 2026-10-03), just the ~2ft height of the space | | 3/8" bar, 5/16" ANL block, M10 selector |
| meanwell +V to velit selector 2 pos 1 | 6 AWG red (same 15ft reel) | **longer than assumed** — the meanwell is driver-side near the DJI, selector 2 is passenger-side above the SOK (confirmed 2026-10-03); realistically crosses most of the 5.5ft front wall plus the height change, likely 6-9ft, not under 6ft | | meanwell terminal (no lug) / M10 selector |
| meanwell -V to - bar | 6 AWG black (same 15ft reel as XS GND) | **longer than assumed**, same driver-to-passenger crossing as the row above — likely 6-9ft, not under 6ft | | 3/8" |
| - bar to chassis | 2 AWG black (pacer, 10ft reel, 2026-10-02 — comfortable slack) | 6-8ft (stated) | | 3/8" |
| shore inlet to 8077 | 10 AWG 3-conductor SOOW (southwire, 15ft ordered/on hand — not yet tape-measured as-installed) | 10ft max (see below) | | per panel |
| 8077 to BAOMAIN 1 - shore AC destination switch to multiplus AC-in | 10 AWG 3-conductor | | | per panel |
| BAOMAIN 1 - shore AC destination switch pos 1 to 3131 to DJI receptacle | 12 AWG 3-conductor (on hand, 20ft) | | | #10 rings |
| multiplus AC-out-1 to 8027 | 10 AWG 3-conductor | | | per panel |

## cargo area layout (under the bed, 2026-10-03)

the DC/AC electrical cluster is built into the cargo area under the bed — 3 walls plus the open rear doors. driver-side and passenger-side walls are 3ft deep (front-to-back), the front wall (opposite the rear opening) is 5.5ft wide, all 2ft tall (floor to the underside of the bed).

| component | location |
|---|---|
| shore inlet | driver-side wall, rear/top |
| DJI power 2000 | floor, driver side, rear |
| meanwell RSP-1000-24 | driver-side wall, near the DJI (confirmed 2026-10-03 — makes the DJI→meanwell AC output tap a short run) |
| multiplus-ii | passenger-side wall, rear |
| SOK battery | floor, parallel with the front wall, passenger-side corner — closest to the multiplus (confirmed 2026-10-03). a planned second SOK would extend along the front wall toward the driver side |
| switch row (front wall, top, driver-side to passenger-side) | 8077 (shore main breaker) → BAOMAIN 1 - shore AC destination switch → BAOMAIN 3 - fridge/receptacle AC source switch → BAOMAIN 2 - oven/cooktop AC source switch (order among the three BAOMAINs not yet confirmed) → battery selector 1 → battery selector 2 (open question: does selector 2 actually mount here with selector 1, or separately near the SOK/busbars at floor level — see verify.md) |
| BAOMAIN 4 - oven/cooktop AC destination switch | kitchen cabinet, ~4ft forward of the cargo area's front wall (outside the cargo area) |

battery selector 2's mounting spot is resolved (2026-10-03): both aramox selectors are in the main switch row, at the far passenger end, directly above the SOK. that makes the direct bus tap short (good), but means the **two meanwell-side 6 AWG runs (meanwell+V→selector 2, meanwell−V→−bar) now cross the full driver-to-passenger width of the front wall**, not a short cargo-area hop — see the two rows above, flagged accordingly. the class T block and +/- busbars aren't physically mounted yet (confirmed 2026-10-03) — unlike the SOK, this is still an open placement decision. **recommendation: mount them near the SOK (passenger corner), not moved toward the driver side** — the high-current 2/0 connections (class T block, multiplus, SOK) benefit far more from staying short than the meanwell's 6 AWG leg does from being shortened (its voltage drop is under 1% even at 9ft — see verify.md for the math). exact placement still TBD within "near the SOK."

estimated (not tape-measured) DJI-to-switch-row distance, using the geometry above: DJI sits at the driver-side/rear/floor corner; the switch row is along the front wall at the top, roughly evenly spaced across 5.5ft. a realistic routed distance (up the wall, across to the switch, not a straight line) to a middle-of-the-row switch (where BAOMAIN 3 - fridge/receptacle AC source switch or BAOMAIN 2 - oven/cooktop AC source switch likely land) works out to roughly **8-10ft**, not the under-6ft assumed everywhere else in this cargo space — this specific DJI-to-switch-row path crosses the full depth (3ft) and height (2ft) of the space, plus lateral distance along the row. **this means the 6ft iron forge cord is likely too short for either kitchen DJI tap** — the 15ft one has real margin, but with 3 taps needed (BAOMAIN 3 - fridge/receptacle AC source switch, BAOMAIN 2 - oven/cooktop AC source switch, and the meanwell) and only 2 cords on hand, the third (still unsourced) cord should probably match the 15ft length rather than risk another shortfall. tape-measure the actual routes before cutting or committing a specific cord to a specific tap.

## distances and limits

| item | limit | measured |
|---|---|---|
| cerbo to multiplus | about 2.5 ft (0.9 m cable) | |
| cerbo to XS | about 2.5 ft (2.95 ft cable) | |
| class T block to SOK | as close as practical | |
| 100A fuse (DJI charger kit) to starter battery + | as installed | |
| shore inlet to 8077 | 10 ft max — if longer, blue sea requires an additional fuse/breaker within 10 ft of the inlet itself, per the 8027-family manual (bluesea8027-instructions.pdf). the 8077's own instructions aren't in hand yet — this is applied by analogy, not confirmed for the 8077 specifically. | |
| enclosure space for 3131 box and receptacle | | |
| under-seat cavity: shared with an existing audiocontrol LE5-1300 amplifier | route new DC cables clear of its wiring | |
