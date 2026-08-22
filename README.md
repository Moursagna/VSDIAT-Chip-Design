# VSDIAT Chip Design Program

This repository documents my learning journey through the **VSDIAT (VLSI System Design – Anurag Institute Chip Design Program)**.

It contains RTL design experiments, simulation results, synthesis evidence, generated netlists, waveform analysis, and personal notes completed throughout the workshop.

---

## 👨‍🎓 Student Information

- **Name:** Moursagna Rao
- **University:** Anurag University
- **Program:** B.Tech
- **Branch:** Electronics and Communication Engineering (ECE)

---

## 🛠 Development Environment

| Tool | Description |
|------|-------------|
| Operating System | Windows 11 |
| Virtual Machine | Ubuntu (VSDIAT VDI) |
| Virtualization | Oracle VirtualBox |
| RTL Simulator | Icarus Verilog |
| Waveform Viewer | GTKWave |
| Synthesis Tool | Yosys |
| Standard Cell Library | SKY130 HD |

---

# 📁 Repository Structure

```text
VSDIAT-Chip-Design/
│
├── README.md
│
├── Day_1/
│
├── Day_2/
│   ├── 01_Hierarchical_vs_Flat_Synthesis/
│   ├── 02_Flip_Flop_Coding_Styles/
│   └── 03_Synthesis_Optimizations/
│
├── Day_3/
│   ├── README.md
│   ├── 01_Combinational_Optimization/
│   ├── 02_Sequential_Optimization/
│   └── 03_Counter_Optimization/
│
├── Day_4/
│   ├── README.md
│   ├── bad_mux_tb_sim.png
│   ├── blocking_caveat_sim.v.png
│   ├── blocking_caveat_synth.png
│   ├── GLS_blocking_caveat.png
│   ├── GLS_tb_bad_mux.v.png
│   ├── GTKWave_ternary_mux_GLS.png
│   ├── sim_ternary_operator_mux.png
│   └── ternary_operator_mux_synth.png
│
└── Day_5/
    ├── README.md
    ├── Ripple_Carry_Adder/
    ├── bad_case/
    ├── comp_case/
    ├── demux_case/
    ├── incomp_if/
    ├── incomp_if2/
    ├── mux_generate/
    └── partial_case_assign/
```
---
## 📚 Course Progress

| Day | Focus Area | Status |
|-----|------------|--------|
| **Day 1** | Verilog RTL Design & Synthesis | ✅ Completed |
| **Day 2** | RTL Synthesis & Optimization | ✅ Completed |
| **Day 3** | Combinational, Sequential & Counter Optimization | ✅ Completed |
| **Day 4** | Gate-Level Simulation & Synthesis-Simulation Mismatch | ✅ Completed |
| **Day 5** | RTL Constructs, Case/If & Synthesis | ✅ Completed |

---

# 📘 Day 1 – RTL Design and Synthesis

Day 1 established the fundamentals of **Verilog RTL design, simulation, and synthesis**.

### Topics Covered

- Verilog RTL design
- Testbench development
- RTL simulation
- Waveform analysis
- Basic synthesis concepts
- Synthesized hardware inspection

🔗 [Explore Day 1 →](./Day_1/)

---

# ⚙️ Day 2 – RTL Synthesis and Optimization

Day 2 focused on understanding how RTL descriptions are converted into hardware and optimized during synthesis.

### Topics Covered

- Hierarchical vs. flat synthesis
- Flip-flop coding styles
- Asynchronous and synchronous reset behavior
- RTL synthesis using Yosys
- SKY130 standard-cell mapping
- Synthesis optimization
- Synthesized netlist analysis

🔗 [Explore Day 2 →](./Day_2/)

---

# 🔬 Day 3 – Combinational, Sequential & Counter Optimization

Day 3 focused on how synthesis tools optimize **combinational and sequential RTL** and map the resulting logic to standard cells.

### Combinational Optimization

- Logic simplification
- Constant propagation
- Redundant logic optimization
- Multiple-module optimization
- SKY130 standard-cell mapping

### Sequential Optimization

- DFF-based RTL
- Constant-driven sequential logic
- Sequential optimization
- Synthesized sequential structures

### Counter Optimization

- Counter RTL synthesis
- Counter optimization
- Standard-cell mapping
- Synthesized counter structures

🔗 [Explore Day 3 →](./Day_3/)

---

# 🧪 Day 4 – Gate-Level Simulation & Synthesis-Simulation Mismatch

Day 4 introduced **Gate-Level Simulation (GLS)** and explored how RTL coding constructs can affect simulation and synthesized behavior.

### Topics Covered

- RTL simulation
- Synthesis analysis
- Gate-level simulation (GLS)
- Synthesis-simulation mismatch
- Blocking assignment behavior
- Ternary-operator based multiplexers
- Synthesized logic inspection
- GLS waveform analysis

### Main Learning

The experiments demonstrated the importance of writing RTL that produces consistent and predictable behavior through simulation and synthesis.

🔗 [Explore Day 4 →](./Day_4/)

---

# 🧩 Day 5 – RTL Constructs, Case/If & Synthesis

Day 5 focused on different **Verilog RTL constructs** and their effect on synthesized hardware.

### Topics Covered

- `if` and `case` constructs
- Incomplete conditional assignments
- Latch inference
- Case-based combinational logic
- MUX and DEMUX implementations
- Generate-based RTL structures
- Partial case assignments
- Ripple Carry Adder
- RTL simulation and synthesis analysis

### Main Learning

The experiments demonstrated how RTL coding style influences the hardware inferred by synthesis and how incomplete assignments can result in unintended storage elements such as latches.

🔗 [Explore Day 5 →](./Day_5/)

---

# 🎯 Learning Objectives

The VSDIAT training is helping build a strong foundation in:

- **Verilog HDL**
- **RTL design methodology**
- **Functional simulation**
- **Waveform analysis**
- **RTL synthesis**
- **Logic optimization**
- **Gate-level netlist generation**
- **Standard-cell mapping**
- **SKY130 technology**
- **ASIC design concepts**

---

# 🔄 RTL-to-Hardware Flow

The experiments progressively connect RTL descriptions to synthesized hardware:

```text
        Verilog RTL
             │
             ▼
      RTL Simulation
             │
             ▼
     Waveform Analysis
             │
             ▼
       Yosys Synthesis
             │
             ▼
     Logic Optimization
             │
             ▼
  SKY130 Standard-Cell Mapping
             │
             ▼
  Synthesized Hardware Structure
             │
             ▼
   Gate-Level Simulation
```
---

# 📌 Key Learning

The workshop demonstrates an important ASIC design principle:

> **RTL coding style directly influences the hardware inferred by synthesis.**

Through the experiments, I have learned how:

- RTL descriptions are converted into hardware
- Synthesis optimizes combinational and sequential logic
- Constants can be propagated during synthesis
- Redundant logic can be removed
- Sequential logic can be optimized
- Incomplete combinational assignments can lead to latch inference
- `if` and `case` constructs describe selection logic
- Generate constructs can create repeated hardware structures
- RTL designs can be mapped to SKY130 standard cells
- Synthesized structures can be inspected using Yosys
- Gate-level simulation can be used to analyze synthesized behavior

---

# 🧰 Core Tools

| Tool | Purpose |
|------|---------|
| **Icarus Verilog** | RTL simulation and functional verification |
| **GTKWave** | Waveform visualization and analysis |
| **Yosys** | RTL synthesis, optimization, and synthesized netlist inspection |
| **SKY130 HD** | Target standard-cell technology for synthesis and technology mapping |

---

# 🚀 Progress

**VSDIAT Modules 1–5 completed ✅**

This repository will continue to be updated as I progress through additional ASIC/VLSI design concepts and practical experiments.

---

# 👤 Author

**Moursagna Rao**

B.Tech – Electronics and Communication Engineering  
**Anurag University**
