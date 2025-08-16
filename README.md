# DC-DC Buck Regulator
I will show how to implement a KiCad project for a 5V @ 1A DC-DC Buck Regulator using the TPS561208DDCR step-down converter.
This repo demonstrates:

Importing real-world components into KiCad (from Mouser via SamacSys Library Loader)

Creating a schematic with TPS561208DDCR, SPM3015T-4R7M, and 282834-2 connector

Laying out a PCB with low-EMI routing techniques

Generating a 3D model of the finished board

Understanding trace widths vs. current capacity

# Components Used
TPS561208DDCR – Synchronous step-down buck regulator

SPM3015T-4R7M – Power inductor (4.7 µH)

282834-2 – 2-pin connector for I/O

Passives (resistors & capacitors for feedback and filtering)

# 1) Importing Real Components from Mouser into KiCad
1. Download and install the SamacSys Library Loader, following the instructions:
 https://www.samacsys.com/kicad/

2. Configure the Library Loader to point to your KiCad library directory.

3. Search and download the following components from Mouser/SamacSys:

   282834-2 → Connector (TE Connectivity)
   TPS561208DDCR → Buck Regulator IC (Texas Instruments)
   SPM3015T-4R7M → Inductor (TDK)

4. The loader will automatically import schematic symbols, PCB footprints, and 3D models into KiCad.

# 2) Add Components in Schematic Editor 
1. Open KiCad → Schematic Editor.

2. Place components:

Add the 282834-2 connector at the input.
Place TPS561208DDCR as the main controller.
Add the SPM3015T-4R7M inductor to the regulator output stage.

3. Wire up supporting components (capacitors, resistors) per the datasheet reference design.

4. Run Electrical Rules Check (ERC) to confirm no missing connections.

# 3) Create PCB Layout in PCB Editor
1. Import the netlist into PCB Editor.

2. Place components close together (minimize high-current loop areas).

3. Route nets:

   Use wide traces for VIN, SW, OUT, and GND.
   Place GND fills/planes to reduce EMI.
   Use short traces for feedback and sensitive signals.

4. If traces must cross:

   Use a via (V key) to switch layers.
   Keep power traces thick, signal traces short.

5. Run DRC (Design Rule Check).

# 4) View the 3D Model
1. In PCB Editor, go to View → 3D Viewer.

2. Rotate and inspect the board:
Confirm imported models for 282834-2, TPS561208DDCR, and SPM3015T-4R7M are aligned properly.
Check component clearances.

3. Export STEP files for mechanical integration.
