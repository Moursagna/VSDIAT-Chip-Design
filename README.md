# VSDIAT Chip Design Program

This repository documents my learning journey through the **VSDIAT (VLSI System Design – Anurag Institute Chip Design Program)**.

It contains my RTL design experiments, Verilog simulations, synthesis work, SKY130 technology mapping, gate-level netlists, waveform analysis, ASIC physical-design work, OpenLane experiments, and the ongoing **BabySoC** implementation.

The repository is organized by training days/modules and practical projects.

---

## 👨‍🎓 Student Information

| Field      | Details                                         |
| ---------- | ----------------------------------------------- |
| Name       | Moursagna Rao                                   |
| University | Anurag University                               |
| Program    | B.Tech                                          |
| Branch     | Electronics and Communication Engineering (ECE) |

---

## 🛠 Development Environment

| Tool / Environment | Purpose                            |
| ------------------ | ---------------------------------- |
| Windows 11         | Host Operating System              |
| Ubuntu VSDIAT VDI  | Linux development environment      |
| Oracle VirtualBox  | Virtualization                     |
| Icarus Verilog     | RTL and gate-level simulation      |
| GTKWave            | Waveform analysis                  |
| Yosys              | RTL synthesis                      |
| OpenLane           | RTL-to-GDSII physical-design flow  |
| OpenSTA            | Static Timing Analysis             |
| OpenROAD           | Physical design implementation     |
| Magic              | Physical layout inspection         |
| SKY130 HD          | Standard-cell library / technology |

---

# Repository Structure

```text
VSDIAT-Chip-Design/
│
├── README.md
│
├── Day_1/
│   └── README.md
│
├── Day_2/
│   └── README.md
│
├── Day_3/
│   └── README.md
│
├── Day_4/
│   └── README.md
│
├── Day_5/
│   └── README.md
│
├── Day_6/
│   ├── README.md
│   └── Physical Design / OpenLane learning material
│
├── Day_7/
│   ├── README.md
│   └── images/
│       └── Physical Design theory and practical results
│
└── BabySoc/
    ├── README.md
    ├── rtl/
    ├── testbench/
    ├── synthesis/
    └── results/
```

---

# Course Progress

| Day   | Topic                                                 | Status      |
| ----- | ----------------------------------------------------- | ----------- |
| Day 1 | Introduction to Verilog RTL Design and Synthesis      | ✅ Completed |
| Day 2 | RTL Synthesis and Optimization                        | ✅ Completed |
| Day 3 | Combinational, Sequential and Counter Optimization    | ✅ Completed |
| Day 4 | RTL vs Gate-Level Simulation and Synthesis Behavior   | ✅ Completed |
| Day 5 | Advanced Verilog Constructs and RTL Coding Practices  | ✅ Completed |
| Day 6 | Introduction to Physical Design and OpenLane          | ✅ Completed |
| Day 7 | Floorplanning, Placement and Physical Design Concepts | ✅ Completed |

---

# Day 1 – Verilog RTL Design and Synthesis

Day 1 introduced the basic RTL-to-synthesis workflow using a simple **2:1 multiplexer**.

### Topics Covered

* Verilog RTL design
* Testbench development
* Functional simulation
* GTKWave waveform analysis
* Yosys synthesis
* Gate-level netlist generation
* SKY130 standard-cell mapping

The practical work established the basic relationship between:

```text
RTL
 ↓
Simulation
 ↓
Synthesis
 ↓
Gate-Level Netlist
 ↓
Technology Mapping
```

---

# Day 2 – RTL Synthesis and Optimization

Day 2 focused on how different RTL coding styles affect synthesis and the resulting hardware.

### Topics Covered

* Hierarchical vs flat synthesis
* Flip-flop coding styles
* Asynchronous and synchronous reset behavior
* Arithmetic optimization
* Boolean logic optimization
* Yosys synthesis
* SKY130 technology mapping

The day provided an understanding of how RTL descriptions are transformed and optimized before technology mapping.

---

# Day 3 – RTL Optimization and Sequential Logic

Day 3 continued the study of synthesis optimization and sequential logic.

### Topics Covered

* Combinational logic optimization
* Sequential logic optimization
* Flip-flop optimization
* Counter optimization
* Yosys synthesis analysis
* Gate-level netlist inspection
* Waveform analysis

The practical work helped connect RTL coding decisions with the hardware structures produced by synthesis.

---

# Day 4 – RTL vs Gate-Level Simulation

Day 4 focused on understanding the relationship between RTL simulation and gate-level simulation.

### Topics Covered

* RTL vs Gate-Level Simulation (GLS)
* Synthesis-simulation mismatch
* Blocking assignments
* Ternary operators
* MUX synthesis
* Gate-level behavior
* Waveform comparison

The main objective was to understand whether the synthesized implementation preserves the intended RTL functionality and how synthesis can affect observed behavior.

---

# Day 5 – Verilog RTL Coding and Hardware Inference

Day 5 focused on Verilog constructs that directly influence synthesized hardware.

### Topics Covered

* `if` statements
* `case` statements
* Incomplete assignments
* Latch inference
* MUX and DEMUX structures
* Generate constructs
* Partial assignments
* Ripple Carry Adder
* RTL hardware inference

The emphasis was on understanding how Verilog coding style translates into actual hardware structures.

---

# Day 6 – Introduction to Physical Design and OpenLane

Day 6 marked the transition from **RTL design and synthesis to ASIC Physical Design**.

### Topics Covered

* ASIC design flow
* RTL-to-GDSII flow
* SKY130 PDK
* OpenLane
* Yosys
* OpenSTA
* OpenROAD
* Magic
* Synthesis
* Floorplanning
* Placement
* Clock Tree Synthesis
* Routing
* Parasitic extraction
* Physical verification
* GDSII generation

### Practical Work

The practical work included:

* Synthesis
* Synthesis statistics analysis
* Floorplanning
* Placement
* Physical layout inspection using Magic

The complete Day 6 documentation is available in [`Day_6/`](Day_6/).

---

# Day 7 – Physical Design: Floorplanning and Placement

Day 7 continued the Physical Design training with a deeper focus on the early physical implementation stages.

### Topics Covered

* Core and Die
* Floorplanning
* Aspect Ratio
* Core Utilization
* Standard-cell placement
* Standard-cell design flow
* Cell characterization
* Timing characterization
* Timing thresholds
* Input and output slew
* Static Timing Analysis fundamentals
* Power Distribution Network
* IR Drop
* Decoupling capacitors
* LEF and DEF
* Physical layout inspection using Magic

### Practical Work

The practical work focused on:

```text
Synthesized Netlist
        ↓
   Floorplanning
        ↓
     Placement
        ↓
Magic Layout Inspection
```

Timing characterization and cell characterization were introduced as theory. The numerical values shown in the training material are example values and are not project measurements.

The complete Day 7 documentation and screenshots are available in [`Day_7/`](Day_7/).

---

# BabySoC Project

The **BabySoC** project is the main practical SoC implementation work in this repository.

It connects the concepts learned throughout the VSDIAT training and applies them to a larger design.

## BabySoC Architecture

The BabySoC contains three major blocks:

```text
                    ┌──────────────┐
 ENb_CP ───────────►│              │
 ENb_VCO ──────────►│   AVSDPLL    │
 REF ──────────────►│     PLL      │─── CLK ───┐
 VCO_IN ───────────►│              │            │
                    └──────────────┘            ▼
                                           ┌──────────┐
                                    reset ─►│  RVMyth  │
                                           │   CPU    │
                                           └────┬─────┘
                                                │
                                           RV_TO_DAC[9:0]
                                                │
                                                ▼
                                           ┌──────────┐
                                    VREFH ─►│ AVSDDAC  │
                                           │   DAC    │
                                           └────┬─────┘
                                                │
                                                ▼
                                               OUT
```

### Main Blocks

* **RVMyth** – RISC-V based digital processor core
* **AVSDPLL** – PLL block used for clock generation
* **AVSDDAC** – DAC block used for converting the processor's digital output

The top-level module is:

```text
vsdbabysoc
```

---

## BabySoC ASIC Flow

The BabySoC is being taken through the following stages:

```text
RTL Design
    ↓
Pre-Synthesis Simulation
    ↓
Logic Synthesis
    ↓
SKY130 Technology Mapping
    ↓
Gate-Level Netlist
    ↓
Post-Synthesis Simulation
    ↓
Static Timing Analysis
    ↓
Physical Design
    ↓
GDSII
```

### Current BabySoC Progress

| Stage                     | Status      |
| ------------------------- | ----------- |
| BabySoC RTL               | ✅ Completed |
| Pre-Synthesis Simulation  | ✅ Completed |
| Yosys Synthesis           | ✅ Completed |
| SKY130 Technology Mapping | ✅ Completed |
| Gate-Level Netlist        | ✅ Completed |
| Post-Synthesis Simulation | ✅ Completed |
| Static Timing Analysis    | 🔄 Upcoming |
| Floorplanning             | ⏳ Upcoming  |
| Placement                 | ⏳ Upcoming  |
| Clock Tree Synthesis      | ⏳ Upcoming  |
| Routing                   | ⏳ Upcoming  |
| GDSII                     | ⏳ Upcoming  |

---

# Learning Objectives

The overall objective of this repository is to build a strong foundation in the complete digital ASIC design flow.

### RTL and Digital Design

* Verilog HDL
* RTL design methodology
* Testbench development
* Functional simulation
* Digital hardware inference

### Synthesis

* Yosys
* RTL synthesis
* Logic optimization
* Technology mapping
* Standard-cell libraries
* Gate-level netlists

### Physical Design

* ASIC physical-design flow
* OpenLane
* SKY130 PDK
* Floorplanning
* Placement
* Clock Tree Synthesis
* Routing
* Parasitic extraction
* Static Timing Analysis
* Physical verification
* GDSII generation

### Practical Engineering

* Linux command-line workflow
* EDA tool usage
* Simulation and waveform analysis
* Netlist inspection
* Physical layout inspection
* Git and GitHub based project documentation

---

# Overall Learning Progress

```text
Digital Design
      ↓
Verilog RTL
      ↓
Simulation
      ↓
Synthesis
      ↓
Optimization
      ↓
Technology Mapping
      ↓
Gate-Level Simulation
      ↓
ASIC Design Flow
      ↓
Floorplanning
      ↓
Placement
      ↓
        ┌───────────────────────────────┐
        │ Upcoming Physical Design Work │
        │                               │
        │ CTS                           │
        │ Routing                       │
        │ Parasitic Extraction          │
        │ STA                            │
        │ Physical Verification         │
        │ GDSII                         │
        └───────────────────────────────┘
```

---

# Author

**Moursagna Rao**

B.Tech – Electronics and Communication Engineering
Anurag University

---

## Repository

[GitHub Repository](https://github.com/Moursagna/VSDIAT-Chip-Design)
