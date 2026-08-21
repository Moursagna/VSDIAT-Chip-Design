# Module 5 – RTL Constructs, Case/If Statements and Synthesis

This module focuses on understanding how different Verilog RTL coding constructs are interpreted during simulation and synthesized into hardware.

The experiments were performed using Verilog HDL, GTKWave for waveform analysis, and Yosys with the SKY130 standard-cell library for synthesis and structural analysis.

---

## Topics Covered

- `if` and `case` based combinational logic
- Incomplete conditional assignments
- Latch inference
- Case-based logic implementation
- MUX and DEMUX implementations
- Generate-based RTL structures
- Partial case assignments
- Ripple Carry Adder (RCA)
- RTL simulation and synthesized hardware comparison

---

## Experiments

### 1. Bad Case

The `bad_case` experiment demonstrates case-based combinational logic and its synthesized hardware representation.

#### Evidence

- RTL simulation using GTKWave
- Yosys synthesis schematic

#### Files

- `bad_case_simulation.png`
- `bad_case_synthesis.png`

---

### 2. Case-Based Combinational Logic

The `comp_case` experiment demonstrates a case-based combinational design and its synthesized implementation.

#### Evidence

- RTL simulation
- Synthesized logic structure

#### Files

- `comp_case_simulation.png`
- `comp_case_synthesis.png`

---

### 3. DEMUX Using Case Logic

The `demux_case` experiment demonstrates a demultiplexer implemented using case-based RTL.

The simulation waveform shows the input being routed to the selected output according to the select signals.

#### Evidence

- GTKWave simulation

#### File

- `demux_case_simulation.png`

---

### 4. DEMUX Using Generate

The `demux_generate` experiment demonstrates a DEMUX implementation using generate-based RTL construction.

The simulation verifies the behavior of the generated output paths for different select values.

#### Evidence

- GTKWave simulation

#### File

- `demux_generate_simulation.png`

---

### 5. Incomplete `if` Assignment and Latch Inference

The `incomp_if` experiment demonstrates the effect of incomplete assignments in combinational RTL.

The synthesis result shows latch inference, illustrating how incomplete combinational assignments can cause storage elements to be inferred.

#### Evidence

- RTL simulation
- Yosys synthesis
- Synthesized latch structure

#### Files

- `incomp_if_simulation.png`
- `incomp_if_synthesis.png`
- `incomp_if_latch_synthesis.png`

---

### 6. Incomplete `if` – Second Case

The `incomp_if2` experiment provides another example of incomplete conditional assignment and its synthesized implementation.

The synthesis evidence shows latch inference resulting from the RTL coding style.

#### Evidence

- RTL simulation
- Synthesized latch structure

#### Files

- `incomp_if2_simulation.png`
- `incomp_if2_latch_synthesis.png`

---

### 7. MUX Using Generate

The `mux_generate` experiment demonstrates a multiplexer implementation using generate-based RTL construction.

The design was simulated and synthesized to observe both functional behavior and the resulting hardware structure.

#### Evidence

- GTKWave simulation
- Yosys synthesis schematic

#### Files

- `mux_generate_simulation.png`
- `mux_generate_synthesis.png`

---

### 8. Partial Case Assignment

The `partial_case_assign` experiment demonstrates the hardware implications of partial assignments in case-based RTL.

The synthesized structure was examined using Yosys to understand the resulting hardware implementation.

#### Evidence

- Yosys synthesis schematic

#### File

- `partial_case_assign_synthesis.png`

---

### 9. Ripple Carry Adder

The Ripple Carry Adder (RCA) experiment demonstrates a multi-bit arithmetic structure constructed from individual full-adder stages.

The generated structural representation, simulation waveform, and synthesized implementation were examined.

#### Evidence

- Generated RTL structure
- Detailed simulation waveform
- Yosys synthesis

#### Files

- `rca_generate_structure.png`
- `rca_simulation_detailed.png`
- `rca_synthesis.png`

---

## Tools Used

- Verilog HDL
- Icarus Verilog
- GTKWave
- Yosys
- SKY130 standard-cell library

---

## Key Learning Outcomes

Through these experiments, I developed a better understanding of how RTL coding style affects synthesized hardware.

### 1. RTL code is hardware description

Different Verilog coding styles can result in different hardware structures after synthesis.

### 2. Incomplete combinational assignments can infer latches

When a combinational output is not assigned for every possible condition, synthesis may infer storage hardware to preserve its previous value.

### 3. Case and if statements describe hardware selection

`case` and `if` constructs can be synthesized into multiplexing and selection logic depending on the RTL structure.

### 4. Generate constructs create repeated hardware structures

Generate constructs are useful for creating scalable and repetitive hardware, such as multi-bit arithmetic structures.

### 5. Simulation and synthesis should both be examined

RTL simulation verifies functional behavior, while synthesis reveals the actual hardware structure inferred from the RTL.

### 6. Coding style matters in ASIC design

Writing synthesizable RTL requires understanding not only Verilog syntax but also the hardware that synthesis tools will infer from that RTL.

---

## Module 5 Summary

Module 5 strengthened my understanding of conditional RTL, case-based logic, latch inference, generate constructs, multiplexers, demultiplexers, and arithmetic hardware.

The experiments also reinforced the connection between:

**Verilog RTL → Simulation → Synthesis → Hardware Structure**

These concepts form an important foundation for writing reliable and synthesis-friendly RTL for ASIC design.
