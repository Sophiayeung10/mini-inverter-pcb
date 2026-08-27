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
- **Ground Fills (Pour Zones)**: Created top and bottom ground planes (`GND` net) using copper zones (`B` key rebuild) to optimize return paths and thermal management.
- **Silkscreen & Labeling**: Added text annotations and component references on silkscreen layers (`F.Silkscreen` / `B.Silkscreen`).

---

### 4. Manufacturing & Export Deliverables
- **Gerber & Drill Generation**: Plotted fabrication files (Gerbers) and drill maps into a structured release directory.
- **Archive Package**: Generated a consolidated `.zip` production package containing all Gerber and drill data, ready for PCB manufacturing submission.

---

##  Repository Structure

```text
├── .history/               # Local backup and revision history
├── Mini Inverter/          # Project sub-folder / CAD assets
├── kicad 1.kicad_pro       # Main KiCad 10 Project File
├── kicad 1.kicad_sch       # Schematic Source File
├── kicad 1.kicad_pcb       # PCB Layout File
├── kicad 1.csv             # Bill of Materials (BOM)
└── kicad 1.zip             # Manufacturing Package (Gerbers & Drill Files)

## Project Visuals

| 2D PCB Layout | 3D Board Render |
| :---: | :---: |
| ![2D PCB Layout](./images/2D%20PCB%20Layout.png) | ![3D Board Render](./images/3D%20Board%20Render.png) |

