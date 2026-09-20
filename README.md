# Mini Inverter PCB Design

A compact printed circuit board (PCB) design created in KiCad. This repository contains the complete design package, including schematics, PCB layout, 3D component CAD models, Bill of Materials (BOM), and production-ready Gerber manufacturing files.

---

##  Project Overview

- **Toolchain**: KiCad (Schematic Editor, PCB Editor, 3D Viewer)
- **Layer Count**: 2-Layer PCB (Front Copper `F.Cu`, Bottom Copper `B.Cu`)
- **Key Features**: Integrated ground copper fills, manual 3D STEP component mapping, defined track width/via rules, and exported manufacturing deliverables.

---

##  Step-by-Step Design Workflow

### 1. Schematic Capture & Setup
- **Page & Grid Setup**: Configured project title and grid dimensions. Set up auto-save intervals to preserve progress.
- **Component Placement & Connections**: Placed schematic symbols, power flags, and ground references (`P1 to P5`). Wired components using orthogonal line modes and global labels for net organization.
- **Annotation & Footprint Assignment**: Automatically annotated schematic symbols and mapped components to footprints using preview and 3D verification tools.
- **Bill of Materials (BOM)**: Exported structured BOM data (`.csv`) directly from schematic attributes.

---

### 2. PCB Layout & Board Design
- **Board Outline & Mechanicals**: Defined physical dimensions using the `Edge.Cuts` layer and configured mounting hole placements.
- **3D Model Integration**: Linked custom 3D STEP models (e.g., terminal blocks from GrabCAD) with precise alignment and rotation offsets for 3D Viewer verification.
- **Design Rule Definition**: Established custom trace widths and via parameters for power and signal routing.

---

### 3. Routing & Power Planes
- **Signal & Power Routing**: Routed top (`F.Cu`) and bottom (`B.Cu`) copper layers using single-track routing and layer-switching via placements (`V`).
- **Ground Fills (Pour Zones)**: Created top and bottom ground planes (`GND` net) using copper zones (`B` key rebuild) to optimize return paths instead of drawing thin wires for every return pathand thermal management. Current flows back easily, and the board stays cooler.

---

### 4. Manufacturing & Export Deliverables
- **Gerber & Drill Generation**: Plotted fabrication files (Gerbers) and drill maps into a structured release directory.
- **Archive Package**: Generated a consolidated `.zip` production package containing all Gerber and drill data, ready for PCB manufacturing submission.

---

## 5. Challenges in My Mini Inverter PCB Project

### 1. Net Name Mismatch

While wiring the board, I noticed that one of the ports I wanted to connect turned grey and wouldn't accept a connection. At first I thought KiCad was broken, but the real cause was simple: the two ends didn't share the same net name.

KiCad doesn't connect things by how they look on screen. It connects them by **name**. If one side is called `VIN` and the other is `Vin` or `VIN1`, KiCad treats them as two unrelated connections, and the mismatched port is greyed out.

**Solution:** I standardized the label names, ran the Electrical Rules Check (ERC), and updated the PCB from the schematic (`F8`).

### 2. Aligning Custom 3D Models

Downloaded STEP files (such as the GrabCAD terminal blocks) rarely line up on import. Fixing the position, rotation, and scale by hand takes trial and error to match my PCB design.

**Solution:** I adjusted the offset and rotation values in the footprint's 3D model settings and checked the result in the 3D Viewer until it matched the PCB.

---

##  Project Visuals

| 2D PCB Layout | 3D Board Render |
| :---: | :---: |
| <img src="images/2D PCB Layout.png" alt="2D PCB Layout" width="100%"> | <img src="images/3D Board Render.png" alt="3D Board Render" width="100%"> |

---

##  Repository Structure

```text
├── Mini Inverter/          # Project sub-folder / CAD assets
├── images/                 # Screenshots (2D layout, 3D render)
├── .gitignore              # Files Git should ignore
├── README.md               # Project documentation
├── kicad 1.kicad_pro       # Main KiCad project file
├── kicad 1.kicad_sch       # Schematic source file
├── kicad 1.kicad_pcb       # PCB layout file
├── kicad 1.csv             # Bill of Materials (BOM)
└── kicad 1.zip             # Manufacturing package (Gerbers & drill files)
