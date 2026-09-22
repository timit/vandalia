# diagrams

last updated: 2026-09-21

mermaid diagrams of the electrical plan. they render on github and in most markdown previewers, and claude code can read and edit them as text. solid lines are wiring in the plan. dashed lines are later options.

switch position convention (2026-09-21, see wiring.md): position 1 is always the DJI leg, position 2 is always the victron leg, on every switch that splits between the two systems — matches the physical layout (DJI driver side/left, victron passenger side/right) to the switch throw direction.

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
  pbar -->|"pos 2, terminal 2, 6 AWG, 40A ANL (verify part number)"| s2["battery selector 2<br/>(2026-09-21: velit source)"]
  mw["meanwell RSP-1000-24 +V"] -->|"pos 1, terminal 1, 6 AWG"| s2
  djiout2["DJI power 2000 AC out"] -->|"14 AWG, direct, no switch"| mw
  s2 -->|"OUTPUT, velit's own 6 AWG cable, fused both ends"| velit["velit 2000R"]
```

## dc negative and ground

```mermaid
flowchart TB
  sokn["SOK battery -"] -->|"2/0"| nbar["- bar<br/>egis 6600-804"]
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
  m8077 -->|"10 AWG 3-conductor, terminals 2+4/6+8 (jumpered common, 10 AWG jumper)"| b3["BAOMAIN 3<br/>1-0-2, 2-pole"]
  b3 -->|"pos 1, terminals 1/5, 12 AWG 3-conductor"| box["3131 box<br/>7210 15A breaker"]
  b3 -->|"pos 2, terminals 3/7, AC-in, 10 AWG 3-conductor"| mp["multiplus-ii"]
  box -->|"12 AWG 3-conductor"| rec["receptacle"]
  rec --> djiin["DJI power 2000 AC in"]
  mp -->|"AC-out-1, 10 AWG"| p8027["blue sea 8027<br/>GFCI on outlets"]
```

## ac loads

BAOMAIN 2 is spare as of the 2026-09-21 velit redesign (see the dc positive diagram for the velit's new circuit — battery selector 2, not an AC transfer switch). the 8027's second 15A branch, previously wired toward BAOMAIN 2, is unconnected — a candidate for the water heater (TBD).

```mermaid
flowchart LR
  p8027["blue sea 8027"] -->|"8027 15A branch, terminals 3/7, gauge TBD (pending kitchen watts)"| b1["BAOMAIN 1"]
  djiout["DJI power 2000 AC out"] -->|"terminals 1/5"| b1
  b1 -->|"terminals 2+4/6+8 (jumpered common), gauge TBD, jumper gauge TBD to match"| kitchen["kitchen circuit<br/>oven, cooktop, fridge"]
```

## 12V bus (blue sea 5026)

solid is how it works now. dashed is the later option that adds a 24V-to-12V converter and a third battery selector (2026-09-21: renamed from "battery selector 2" to "battery selector 3" — selector 2 is now assigned to the velit, see the dc positive diagram. this option would need a new switch, not a repurposed one).

```mermaid
flowchart LR
  djisdc["DJI SDC 12V feed<br/>XT60, 13.6V/10A max"] -->|"10-15A ATC/ATO fuse (fixed — was a 40A ANL, wrong format for this cable)"| fb["blue sea 5026<br/>12V fuse block"]
  bank["24V bank"] -.->|"about 25A fuse, gauge TBD, verify"| conv["orion-tr smart 24/12-30"]
  conv -.->|"gauge TBD"| s3["battery selector 3<br/>(not yet owned)"]
  djisdc -.->|"gauge TBD"| s3
  s3 -.->|"gauge TBD"| fb
```

## data cables

```mermaid
flowchart LR
  sok["SOK battery"] -->|"CAN, supplied cable"| cerbo["cerbo GX MK2"]
  mp["multiplus-ii"] -->|"VE.bus RJ45, 0.9m supplied"| cerbo
  xs["orion XS 1400"] -->|"VE.direct, 2.95ft supplied"| cerbo
```
