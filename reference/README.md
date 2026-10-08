# reference documents

manuals and datasheets for the whole build, shared across subsystems (not split by folder like electrical/ and plumbing/ are). drop them here as PDFs. claude code can read them to settle open questions in the relevant subsystem's PLAN.md (electrical/PLAN.md today). when one settles an item, cite the file name there.

have:
- DJI_Power_1kW_Super_Fast_Car_Charger_Multi.pdf (does not list a fuse rating — that spec came from the owner directly, not this manual)
- Velit_2000R_User_Manual_2609.pdf (note: the manual contradicts itself on refrigerant charge for the 24V variant — see electrical/PLAN.md's open questions)
- 124067-Orion_XS_DC-DC_battery_charger-pdf-en.pdf, plus ORI242417040-support.heic and ORI242417040-photo.heic
- 32424-MultiPlus-II___Quattro-II-pdf-en.pdf, plus PHP242305102-support.heic and PHP242305102-photo.heic
- SK24V150PH.pdf and SK24V150PH-photo.heic
- DJI_Power_2000_um_en.pdf, DJI_Power_2000_Release_Notes_en.pdf, DJI_Power_Expansion_Battery_2000_User_Guide_Multi.pdf, DJI_Power_Energy_Optimization_User_Manual_v1.0_en.pdf (release notes and energy optimization guide not yet read in detail — energy optimization covers grid-tied ESS mode, not used in this build, so low priority)
- baomain-operating-intructions.pdf — the real SZW26-series manual from the EU importer/manufacturer (CET Product Service), photographed from the box. the manuals.plus reproduction that had it wrong (30A vs the confirmed 32A) has been deleted. also have baomain-exterior-photo.heic (installed unit) and baomain-interior-photo.heic (nameplate, confirms Ith:32A).
- RSP-1000-SPEC.pdf (meanwell RSP-1000-24 datasheet), plus meanwell-exterior-photo.heic (nameplate and DC output wiring, confirms the datasheet and the velit cable's fuse placement)
- aramox-exterior-photo.heic and aramox-interior-photo.heic (the two 300A battery selector switches). no separate datasheet exists — "aramox" is a private-label reseller of a generic OEM switch (also sold as spartan power, seaflo, etc.); the printed label photographed here is the only documentation.
- bluesea8027-instructions.pdf, plus bluesea8027-exterior-photo.heic and bluesea8027-interior-photo.heic
- 5026.pdf (spec sheet) and Wiring-Diagram-5026_5031.pdf, plus bluesea5026-interior-photo.heic and bluesea5026-exterior-photo.heic
- 140558-Ekrano_GX__Venus_GX__Cerbo_GX__Cerbo-S_GX_Manual-pdf-en.pdf (cerbo GX MK2, PN BPP900450110), plus BPP900450110-photo.heic and BPP900450110-support.heic
- Typhur_CV03SyncOven.pdf (kitchen oven user manual — 1750W, 120VAC, confirms the manufacturer's rated power used in README's load budget)
- EMPV-12EC07_Manual.pdf (kitchen cooktop use and care guide — 1800W total, 120VAC, and the source of the "minimum circuit breaker amperage: 20" requirement that drove the 2026-10-02 kitchen circuit redesign)
- DEAPRULL_ D31A.png (kitchen fridge spec-sheet screenshot — partly unreliable; the dual-voltage/35-45W figures actually used came from a web search, not this file)
- audiocontrol-LE5-1300-UM11225.heic (AudioControl amp manual photo — filename says "LE5-1300," likely a typo; everything findable points to LC-5.1300, see audio/PLAN.md)
- IMG_1711.jpeg, IMG_1712.jpeg, IMG_1713.jpeg (salvaged OEM relay for the rear camera's reverse trigger — pin diagram face, housing back/part number, and socket wiring, respectively; see audio/PLAN.md's camera wiring section)
- IMG_1714.jpeg (the 2x Focal Access 1 passive crossovers for the front speakers; see audio/PLAN.md's front speakers and amplifier section)
- IMG_1715.jpeg (the factory mirror-area connector — matches the documented Mercedes FR7/cargo-van rearview-camera-to-mirror-monitor prewire harness; see audio/PLAN.md's head unit power source section)

note: the BAOMAIN transfer-switch terminal wiring (jumper 2-4 and 6-8, common vs position legs) isn't spelled out in the real manual either, but it's consistent with that manual's own truth table (page 3). the specific transfer-switch application came from a web search — a wiring tutorial and RV/van forum threads for this switch family. it's in electrical/PLAN.md, not here, since it's not a PDF to file.

wanted (electrical):
- blue sea instructions: 8077, 3131, 7210, 5005, 5502 (or egis class T block)
- egis powerbar 6600-404 spec sheet (both busbars are now this model, 2026-10-03 — the 6600-804 spec sheet is no longer needed)
- victron orion-tr smart 24/12-30 isolated manual — not bought yet (12V bus redundancy, adopted 2026-10-03); its own wire/fuse sizing in electrical/PLAN.md is a reasoned estimate until this is on hand

wanted (plumbing): none yet.

## helpful links

external tutorials and resources worth revisiting, not tied to a specific part or verify item.

- [DIY Sprinter Camper Van Electrical Install - Full Tutorial](https://www.youtube.com/watch?v=01F4QDVJUq0) — nate at explorist.life, a start-to-finish electrical install for a 2021 sprinter. explorist.life is also where the victron lynx distribution-center question came from (2026-10-03, see electrical/PLAN.md's "decided" section) — this build stuck with generic marine busbars/ANL blocks instead, already owned and functionally equivalent.
