# Day 6 – Introduction to Physical Design and OpenLane

## Overview

This module introduces the physical design stage of the ASIC design flow and the open-source tools used to transform a synthesized RTL design into a physical chip layout.

The training covers the SKY130 PDK, OpenLane, the RTL-to-GDSII flow, synthesis, static timing analysis, floorplanning, placement, clock tree synthesis, routing, parasitic extraction, physical verification and GDSII generation.

---

## ASIC Design Flow

The overall RTL-to-GDSII flow can be summarized as:

```text
RTL Design
    ↓
RTL Synthesis
    ↓
Gate-Level Netlist
    ↓
Static Timing Analysis
    ↓
Floorplanning
    ↓
Placement
    ↓
Clock Tree Synthesis
    ↓
Routing
    ↓
Parasitic Extraction
    ↓
Post-Route STA
    ↓
Physical Verification
    ↓
GDSII

Each stage transforms or analyzes the design while considering increasingly realistic physical implementation constraints.
```

## Open-Source ASIC Design Flow

The physical design flow studied in this module uses open-source tools and the **SKY130 Process Design Kit (PDK)**.

### Major Components

- **OpenLane** – RTL-to-GDSII implementation flow
- **Yosys** – RTL synthesis
- **OpenSTA** – Static Timing Analysis
- **OpenROAD** – Physical design implementation
- **Magic** – Layout viewing and physical verification
- **SKY130** – Open-source 130 nm technology PDK

---

## SKY130 PDK

A **Process Design Kit (PDK)** provides the technology-specific information required by EDA tools to design and verify an integrated circuit.

The SKY130 PDK provides information such as:

- Standard-cell libraries
- Technology rules
- Design rules
- Device information
- Physical layer definitions
- Timing and power models
- Layout information

The PDK therefore forms the technology interface between the design tools and the semiconductor manufacturing process.

---

## OpenLane

**OpenLane** is an automated RTL-to-GDSII implementation flow that integrates several open-source EDA tools.

A simplified OpenLane flow is:

```text
RTL
 ↓
Synthesis
 ↓
Floorplanning
 ↓
Placement
 ↓
CTS
 ↓
Routing
 ↓
Parasitic Extraction
 ↓
STA
 ↓
Physical Verification
 ↓
GDSII

```
The flow performs multiple stages of optimization and verification to obtain a manufacturable physical implementation.

## Physical Design

Physical design converts the synthesized logical representation of a circuit into a physical arrangement of cells and interconnects.

The major physical design stages include:

### 1. Floorplanning

Defines the physical boundaries of the design, including the core and die dimensions.

### 2. Placement

Determines the physical locations of standard cells within the core while considering wirelength, timing, congestion, and density.

### 3. Clock Tree Synthesis

Builds a clock distribution network to deliver the clock signal to sequential elements while controlling clock skew and insertion delay.

### 4. Routing

Creates physical interconnections between the placed cells.

### 5. Parasitic Extraction

Extracts the resistance and capacitance introduced by physical interconnects.

### 6. Physical Verification

Checks the physical implementation against manufacturing and connectivity requirements.

## Practical Work

The following physical design stages were performed during the training:

- Synthesis
- Floorplanning
- Placement
- Layout inspection using Magic

The corresponding results are documented in the following sections.

## Learning Outcomes

After completing this module, I gained an understanding of:

- The transition from RTL to physical implementation
- The role of a PDK in ASIC design
- The OpenLane RTL-to-GDSII flow
- The purpose of floorplanning
- The purpose of placement
- The relationship between logical synthesis and physical implementation
- The role of open-source EDA tools in ASIC design

## Status

| Stage | Status |
|---|---|
| RTL Design | ✅ Completed |
| Synthesis | ✅ Completed |
| Floorplanning | ✅ Completed |
| Placement | ✅ Completed |
| Clock Tree Synthesis | ⏳ To be covered |
| Routing | ⏳ To be covered |
| Parasitic Extraction | ⏳ To be covered |
| Post-Route STA | ⏳ To be covered |
| Physical Verification | ⏳ To be covered |
| GDSII Generation | ⏳ To be covered |
