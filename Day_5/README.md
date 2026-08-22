# Day 5 – RTL Constructs, Case/If Statements and Synthesis

## Overview

Day 5 focused on understanding how different Verilog RTL coding constructs are interpreted during simulation and synthesized into hardware.

The experiments covered:

- `if` and `case` based combinational logic
- Incomplete conditional assignments
- Latch inference
- MUX and DEMUX implementations
- Generate-based RTL structures
- Partial case assignments
- Ripple Carry Adder
- RTL simulation and synthesis analysis

The experiments were performed using Verilog HDL, GTKWave for waveform analysis, and Yosys with the SKY130 standard-cell library for synthesis and structural analysis.

---

## 1. Bad Case

The `bad_case` experiment demonstrates case-based combinational logic and its synthesized hardware representation.

📁 [bad_case](./bad_case/)

---

## 2. Case-Based Combinational Logic

The `comp_case` experiment demonstrates a case-based combinational design and its synthesized implementation.

📁 [comp_case](./comp_case/)

---

## 3. DEMUX Using Case Logic

The `demux_case` experiment demonstrates a demultiplexer implemented using case-based RTL.

📁 [demux_case](./demux_case/)

---

## 4. Incomplete `if` Assignment and Latch Inference

The `incomp_if` experiment demonstrates the effect of incomplete assignments in combinational RTL and the resulting latch inference during synthesis.

📁 [incomp_if](./incomp_if/)

---

## 5. Incomplete `if` – Second Case

The `incomp_if2` experiment provides another example of incomplete conditional assignment and its synthesized implementation.

📁 [incomp_if2](./incomp_if2/)

---

## 6. MUX Using Generate

The `mux_generate` experiment demonstrates a multiplexer implementation using generate-based RTL construction.

📁 [mux_generate](./mux_generate/)

---

## 7. Partial Case Assignment

The `partial_case_assign` experiment demonstrates the hardware implications of partial assignments in case-based RTL.

📁 [partial_case_assign](./partial_case_assign/)

---

## 8. Ripple Carry Adder

The Ripple Carry Adder (RCA) experiment demonstrates a multi-bit arithmetic structure constructed from individual full-adder stages.

The generated structural representation, simulation waveform, and synthesized implementation were examined.

📁 [Ripple_Carry_Adder](./Ripple_Carry_Adder/)

---

## Tools Used

- **Verilog HDL**
- **Icarus Verilog**
- **GTKWave**
- **Yosys**
- **SKY130 standard-cell library**

---

## Key Learning Outcomes

Through these experiments, I learned:

- How `if` and `case` constructs are synthesized into hardware
- How incomplete combinational assignments can infer latches
- How coding style affects synthesized hardware
- How generate constructs can create repeated hardware structures
- How MUX and DEMUX logic can be described using different RTL constructs
- How partial case assignments affect synthesis
- How a Ripple Carry Adder can be constructed from full-adder stages
- How to compare RTL simulation with synthesized hardware structures

---

## Completion Status

**Day 5 – Completed ✅**
