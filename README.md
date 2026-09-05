# 500W-Mono-ClassAB-Amplifier

Initial schematic draft and BOM committed. This repository will contain the KiCad v7
project files, PCB layout, BOM, Gerbers, and assembly drawings for the 500W RMS
Mono Class-AB Amplifier project.

What is in this commit:
- schematic/SCHEMATIC_DRAFT_V1.md : Textual draft of the schematic and block
  diagram (functional blocks, net names, and component mappings).
- BOM/BOM_v1_initial.csv : Initial BOM with key power components and vendor
  suggestions for Indian suppliers.

Next steps (in progress):
1) Produce native KiCad v7 schematic (.kicad_sch) with full symbols and exact
   reference designators.
2) Produce PCB layout (.kicad_pcb) sized 200x100 mm with heavy copper traces.
3) Generate Gerbers, drill files, placement/assembly drawings and a release ZIP.

I will push the native KiCad sources (schematic + PCB) to the repo within the
next 24 hours for your review. If you want changes to the draft (balanced input,
add banana posts, or different terminal choices) tell me now.
