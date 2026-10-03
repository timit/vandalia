# diagrams

last updated: 2026-10-03 (resolved stale items)

mermaid diagrams of the electrical plan. they render on github and in most markdown previewers, and claude code can read and edit them as text. solid lines are wiring in the plan. dashed lines are later options.

switch position convention (2026-09-21, see wiring.md): position 1 is always the DJI leg, position 2 is always the victron leg, on every switch that splits between the two systems — matches the physical layout (DJI driver side/left, victron passenger side/right) to the switch throw direction. exception: BAOMAIN 4 - oven/cooktop AC destination switch (added 2026-10-02) selects between two loads (oven/cooktop), not two sources, so this convention doesn't apply to it.

## dc positive and alternator

```mermaid
flowchart LR
  vf["van 12V feed<br/>starter battery +"] -->|"AEP 100A 65VDC fuse, 6 AWG (unlabeled), to OUTPUT terminal"| s1["battery selector 1"]
  s1 -->|"pos 1, terminal 1, 6 AWG (as installed)"| djic["DJI car charger"]
  s1 -->|"pos 2, terminal 2, 6 AWG"| xs["orion XS 1400"]
  djic --> djip["DJI power 2000"]
  xs -->|"60A ANL, 6 AWG"| pbar["+ bar<br/>egis 6600-404"]
  sok["SOK battery +"] -->|"2/0"| ct["class T fuse<br/>300A"]
  ct -->|"2/0"| pbar
  pbar -->|"2/0"| mp["multiplus-ii +"]
  pbar -->|"supplied cable, inline 3.15A fuse, M8 ring (verify fits 3/8in bar stud)"| cerbo["cerbo V+"]
  pbar -->|"pos 2, terminal 2, 6 AWG, 40A ANL, blue sea 5165 (confirmed 2026-10-03)"| s2["battery selector 2<br/>(2026-09-21: velit source)"]
  mw["meanwell RSP-1000-24 +V"] -->|"pos 1, terminal 1, 6 AWG"| s2
  djiout2["DJI power 2000 AC out"] -->|"14 AWG, direct, no switch"| mw
  s2 -->|"OUTPUT, velit's own 6 AWG cable, fused both ends"| velit["velit 2000R"]
```

## dc negative and ground

```mermaid
flowchart TB
  sokn["SOK battery -"] -->|"2/0"| nbar["- bar<br/>egis 6600-404 (swapped from the 8-stud 6600-804, 2026-10-03 — stacked, see wiring.md)"]
  mpn["multiplus-ii -"] -->|"2/0"| nbar
  xsg["orion XS GND"] -->|"6 AWG"| nbar
  cerbon["cerbo -"] -->|"supplied cable, M8 ring"| nbar
  mpg["multiplus exterior grounding point"] -->|"10 AWG min (victron: at least 4mm²), separate from DC- and AC ground"| nbar
  mwn["meanwell RSP-1000-24 -V"] -->|"6 AWG (2026-09-21: permanently bonded here — safe because the meanwell's AC input is galvanically isolated from its DC output)"| nbar
  veln["velit 2000R -"] -->|"velit's own 6 AWG cable, fused at the velit end"| nbar
  nbar -->|"2 AWG, one point only, 6-8ft to factory stud"| chassis["chassis bond"]
```

## ac input

```mermaid
flowchart LR
  inlet["shore inlet<br/>conntek 30A<br/>generator plugs in here"] -->|"10 AWG 3-conductor"| m8077["blue sea 8077<br/>30A double-pole main"]
  m8077 -->|"10 AWG 3-conductor, terminals 2+4/6+8 (jumpered common, 10 AWG jumper)"| b3["BAOMAIN 1 - shore AC destination switch<br/>1-0-2, 2-pole"]
  b3 -->|"pos 1, terminals 1/5, 12 AWG 3-conductor (a second spool obtained 2026-10-03, after the original was reassigned to the kitchen's 20A circuit)"| box["3131 box<br/>7210 15A breaker"]
  b3 -->|"pos 2, terminals 3/7, AC-in, 10 AWG 3-conductor"| mp["multiplus-ii"]
  box -->|"12 AWG 3-conductor, same spool"| rec["receptacle"]
  rec --> djiin["DJI power 2000 AC in"]
  mp -->|"AC-out-1, 10 AWG"| p8027["blue sea 8027<br/>GFCI on outlets"]
```

## ac loads

kitchen redesign (2026-10-02): real nameplate watts (oven 1750W, cooktop 1800W with its own 20A-minimum breaker requirement, fridge 35-45W, confirmed AC 2026-10-03) ruled out one shared "kitchen" branch — oven+cooktop combined (3550W) exceed every AC source in this build. now two independent circuits: BAOMAIN 3 - fridge/receptacle AC source switch is no longer spare-adjacent, it's the 15A fridge+USB circuit's source-selector. BAOMAIN 2 - oven/cooktop AC source switch (freed by the 2026-09-21 velit redesign) is the 20A oven/cooktop circuit's source-selector, feeding BAOMAIN 4 - oven/cooktop AC destination switch (new switch) which mechanically interlocks oven and cooktop so they can never both be live. the 8027's second and third 15A branches remain spare (candidates: water heater, other future circuits). DJI's AC output (confirmed 2026-10-03): 4 ports, 100-120V/25A ≈ 3000W continuous for the US variant — clears the kitchen's worst case comfortably.

```mermaid
flowchart LR
  p8027a["blue sea 8027<br/>existing 15A branch"] -->|"terminals 3/7, 14 AWG"| b1["BAOMAIN 3 - fridge/receptacle AC source switch"]
  djiout1["DJI AC output port (1 of 2)"] -->|"terminals 1/5, iron forge cord"| b1
  b1 -->|"terminals 2+4/6+8 (jumpered common), 14 AWG, 14 AWG jumper"| kfu["fridge + USB outlet<br/>(both confirmed 120VAC, 2026-10-03)"]
  p8027b["blue sea 8027<br/>new 20A breaker"] -->|"terminals 3/7, 12 AWG"| b2["BAOMAIN 2 - oven/cooktop AC source switch"]
  djiout2b["DJI AC output port (2 of 2)"] -->|"terminals 1/5, iron forge cord"| b2
  b2 -->|"terminals 2+4/6+8 (jumpered common), 12 AWG, 12 AWG jumper"| b4["BAOMAIN 4 - oven/cooktop AC destination switch<br/>(new — load interlock, not source)"]
  b4 -->|"terminals 1/5, 12 AWG"| oven["oven<br/>typhur CV03, 1750W"]
  b4 -->|"terminals 3/7, 12 AWG"| cooktop["cooktop<br/>empava EMPV-12EC07, 1800W, 20A min"]
```

## 12V bus (blue sea 5026)

**12V bus redundancy adopted 2026-10-03, parts obtained 2026-10-03** (not yet installed): battery selector 3 (position 1 DJI, position 2 victron, same convention as every other switch) picks between the existing DJI SDC feed (~136W ceiling) and a new orion-tr smart 24/12-30 isolated converter off the 24V bus (30A/360W) — resolves the real gap where the USB panels alone are rated up to 432W. the orion-tr's own wire/fuse figures below are reasoned estimates (no manual on file for this specific part yet) — see wiring.md and verify.md.

```mermaid
flowchart LR
  djisdc["DJI SDC 12V feed<br/>XT60, 13.6V/10A max"] -->|"10-15A ATC/ATO fuse (fixed — was a 40A ANL, wrong format for this cable)"| s3["battery selector 3<br/>(obtained 2026-10-03, not yet installed)"]
  bank["24V bank (+ bar)"] -->|"~20A fuse, ~12 AWG (estimate, verify against the orion-tr's own manual)"| conv["orion-tr smart 24/12-30<br/>isolated, 30A/360W out"]
  conv -->|"10 AWG, 30A-class fuse (estimate)"| s3
  s3 -->|"10 AWG, 30A-class fuse (upsized from 10-15A for the new victron leg)"| fb["blue sea 5026<br/>12V fuse block"]
```

## data cables

```mermaid
flowchart LR
  sok["SOK battery"] -->|"CAN, supplied cable"| cerbo["cerbo GX MK2"]
  mp["multiplus-ii"] -->|"VE.bus RJ45, 0.9m supplied"| cerbo
  xs["orion XS 1400"] -->|"VE.direct, 2.95ft supplied"| cerbo
```
