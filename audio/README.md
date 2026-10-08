# audio: as-built

last updated: 2026-10-07

this file only records what's actually true of the physical system. for the design and remaining install work, see PLAN.md.

## install progress

all three units installed and operational:

- ATOTOMOVE S8 Ultra head unit (10.1" display, android, wireless carplay/android auto, 6GB/128GB)
- ATOTO AC-FCR04W front-facing camera (1080P, 150° FOV)
- ATOTO AC-RCR04W rear-facing camera (1080P HDR, 145° FOV, IP67), replacing the vehicle's stock rear camera

**known issue (open)**: the rear camera doesn't stay on reliably in reverse — it displays briefly, then drops. See PLAN.md's installation checklist and open questions.

**known issue (open)**: the head unit is currently powered entirely from the factory mirror-area camera/mirror-monitor harness (confirmed switched power, ground, plus an unused trigger wire, 2 assumed-mic leads, and an orphaned video feed) rather than a dedicated source. a separate factory radio-bay harness was found at the head unit's own location (confirmed constant power and ground, speaker wires present) and is the better source — rewiring to it is pending a switched wire still being found there. see PLAN.md's "head unit power source" section.

## existing front speaker system

pre-dates this project, confirmed in place:

- AudioControl LC-5.1300 5-channel amplifier, under the driver seat (verify: nameplate — reference photo is filed as "LE5-1300", likely a typo)
- 2x Focal Access 1 passive crossovers (12dB/octave), one per side, each fed by a single amp channel
- front woofer + tweeter pairs, L and R, off each crossover's outputs

only 2 of the amp's 5 channels are currently used. a possible future upgrade (going "active" — independent amp channels per driver, using the amp's own built-in crossovers instead of the passive ones) is logged as deferred in PLAN.md's open questions; nothing about the current setup needs to change for it to keep working.
