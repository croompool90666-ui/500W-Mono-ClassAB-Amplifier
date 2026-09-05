KICAD SCHEMATIC DRAFT - 500W Mono Class-AB Amplifier (KiCad v7)

This file is an initial textual draft of the KiCad schematic. A full native
.kicad_sch file and PCB layout will be produced next. This draft lists the
functional blocks, reference designators, and net names used for the first
schematic revision and maps components to footprints that will be created in
KiCad v7.

Project: 500W-Mono-ClassAB-Amplifier
KiCad target: v7
Board size: 200 mm x 100 mm, 2-layer, 1.6 mm FR4, 2 oz copper (wide traces for
power rails)
Transistor mounting: TO-3P insulated footprints (collector insulated from
heatsink)
Output pairs: 5 x (2SC5200 NPN) + 5 x (2SA1943 PNP)
Integrated PSU: AC screw terminals -> KBPC3510 footprint or 4x IN5408 diodes
Filter caps: space for 2x 4700uF/80V in parallel or 1x 10000uF/80V
Protection: speaker relay, DC-detect, soft-start (NTC or inrush relay),
thermal cutout footprint, fuses.

Functional Blocks and key nets:
- INPUT_STAGE: differential input (optional single-ended), input jack / screw
  terminal J_IN (3-pin: IN+, GND, - not used for SE)
- PREAMP: voltage gain stage (Q1/Q2 - matched small signal transistors),
  input R/C network, input coupling cap C_IN
- DRIVER_STAGE: driver transistors (Qd1..Qd4) BD139/BD140 or TTC5200/TTA1943
  depending on BOM. Driver emitter resistors and local bypasses.
- OUTPUT_STAGE: power transistors Qp1..Qp5 (2SA1943 PNP) and Qn1..Qn5
  (2SC5200 NPN). Emitter resistors Re1..Re10 (0.22R / 5W), emitter bus to
  speaker output.
- BIAS_NETWORK: Vbe multiplier (Vbe/diode string + pot) for idle bias control,
  thermistor pad footprints near heatsink for thermal tracking.
- POWER_SUPPLY: AC_IN_L / AC_IN_N screw terminals -> fuse -> KBPC3510 or 4x
  IN5408 diode option -> V+ and V- rails -> main filter caps -> smoothing and
  pre-amp rails (+15V or regulated supply) using zener 15V and series resistor
- PROTECTION: DC detect circuit -> speaker-relay (SPKR_REL) controlled by
  DC detect and soft-start; mute/soft-start relay for turn on delay; thermistor
  footprints for thermal shutdown.

Reference Designator mapping (initial):
- Q1, Q2: preamp differential transistors (C1815/A1015 or BC546/BC556)
- Q3..Q6: driver transistors (BD139/BD140) or TTC5200/TTA1943
- QP1..QP5: 2SC5200 NPN output transistors (labelled on silkscreen as QP1..QP5)
- QN1..QN5: 2SA1943 PNP output transistors (labelled QN1..QN5)
- R1..R20: signal resistors (1/4W metal film)
- Re1..Re10: emitter resistors 0.22R 5W (one per power transistor)
- C1..C10: input/decoupling caps (10uF/50V, 100uF/63V, 0.1uF bypass)
- C_PSU1..C_PSU4: main filter capacitors (4700uF/80V or 10000uF/80V footprint)
- D_BRIDGE: KBPC3510 footprint OR D1..D4 IN5408 footprints
- Z1: 15V zener for preamp regulator
- J_ACC: AC input screw terminal (2 pins) - footprints for 7.62mm terminal
- J_SPK: Speaker output screw terminal (2 pins) - 7.62mm pitch
- J_IN: Audio input 3-pin screw terminal / JST (5.08mm footprint)
- RELAY1: speaker protection relay footprint (12V coil, 30A contact)
- F1: AC fuse holder footprint

Silkscreen requirements implemented in final layout:
- Clear reference + component values printed next to every component.
- Polarity markers (+/-) for electrolytic capacitors, diodes, and bridge.
- Pin labels (B / C / E) under all driver & power transistors.
- Terminal labels: IN+, GND, SPK+, SPK-, V+, V-, 0V (GND)

Footprint notes:
- Power transistors: TO-3P insulated mounting footprint with M4 mounting
  hole and clearance for insulating bush / washer.
- Emitter resistors: ceramic block 5W footprints with large solder pads for
  Kelvin connection.
- Main electrolytics: 35x50mm radial or 50x60mm (as required), multiple
  4700uF footprints in parallel.
- Bridge rectifier: KBPC3510 footprint with 35A handling (large pads + vias)

Next steps (in progress):
1) Produce native KiCad v7 schematic (.kicad_sch) with all component symbols
   and electrical connections based on the above mapping.
2) Produce PCB layout (.kicad_pcb) with heavy copper traces, top silkscreen,
   terminal footprints, and footprints for protection circuits.
3) Generate BOM CSV, Gerbers, and push to GitHub release.

Notes:
- This draft is intended for review. After your review I will convert this
  into a complete KiCad schematic file and push the native KiCad sources.

Contact: Repository: https://github.com/croompool90666-ui/500W-Mono-ClassAB-Amplifier
