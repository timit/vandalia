# audio: as-built

last updated: 2026-10-12

this file only records what's actually true of the physical system. for the design and remaining install work, see PLAN.md.

## install progress

all three units installed and operational:

- ATOTOMOVE S8 Ultra head unit (10.1" display, android, wireless carplay/android auto, 6GB/128GB)
- ATOTO AC-FCR04W front-facing camera (1080P, 150° FOV)
- ATOTO AC-RCR04W rear-facing camera (1080P HDR, 145° FOV, IP67), replacing the vehicle's stock rear camera

**known issue (open)**: the rear camera doesn't activate when the vehicle is put in reverse, though it works fine when viewed manually (power, ground, and video all confirmed good). per the camera's real manual, this points to wire A1 ("to the back-up lamp (+12V)") — separate from the A2 trigger wire already correctly connected — likely not (re)connected to the vehicle's reverse-light circuit during the recent power rewiring. see PLAN.md's "camera wiring" section.

**resolved**: the head unit and both cameras are now powered from the radio-bay harness (constant, fuse #41) plus a new accessory-switched tap sourced from an unassigned position in the driver-seat-base fuse box (position 32) — replacing the original factory mirror-area harness, which was undersized for a full head unit. see PLAN.md's "head unit power source" section.

## existing front speaker system

pre-dates this project, confirmed in place:

- AudioControl LC-5.1300 5-channel amplifier, under the driver seat — model confirmed directly from the box found in the glove box (clearly printed "LC-5.1300"), resolving the earlier "LE5-1300" filename typo concern. see PLAN.md's front speakers and amplifier section for full specs
- 2x Focal Access 1 passive crossovers (12dB/octave), one per side, each fed by a single amp channel
- front woofer + tweeter pairs, L and R, off each crossover's outputs

only 2 of the amp's 5 channels are currently used. a possible future upgrade (going "active" — independent amp channels per driver, using the amp's own built-in crossovers instead of the passive ones) is logged as deferred in PLAN.md's open questions; nothing about the current setup needs to change for it to keep working.
