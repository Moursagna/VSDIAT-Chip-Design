# Day 4 – Gate Level Simulation and Synthesis-Simulation Mismatch


## Overview


Day 4 focused on **Gate Level Simulation (GLS)** and understanding situations where RTL simulation results can differ from the behavior of the synthesized design.


The experiments were performed using **Icarus Verilog, GTKWave, Yosys and SKY130 standard-cell libraries**.


---


## Topics Covered


- Gate Level Simulation (GLS)
- RTL simulation vs synthesized netlist simulation
- Synthesis-simulation mismatch
- Missing sensitivity list
- Blocking vs non-blocking assignments
- Blocking assignment caveat
- Ternary operator implementation of a MUX


---


## 1. Gate Level Simulation


Gate Level Simulation verifies the behavior of the synthesized netlist using a testbench.


The synthesized netlist contains technology-specific standard-cell instances from the SKY130 library.


The general flow is:


```text
RTL Design
    ↓
RTL Simulation
    ↓
Yosys Synthesis
    ↓
Technology Mapping
    ↓
Gate-Level Netlist
    ↓
Gate Level Simulation
    ↓
Compare with RTL Simulation

GLS is useful for checking whether the synthesized implementation preserves the intended functionality of the RTL design.

```
---

## 2. Ternary Operator MUX

A 2:1 MUX can be described using the Verilog ternary operator:

assign y = sel ? i1 : i0;

The synthesized design was mapped to a SKY130 standard-cell MUX:

sky130_fd_sc_hd__mux2_1

### Evidence
#### RTL Simulation

#### Synthesized Logic

#### Gate Level Simulation

The RTL simulation and GLS waveforms show consistent MUX functionality.

## 3. Missing Sensitivity List – Bad MUX

The bad_mux experiment demonstrates a synthesis-simulation mismatch caused by an incomplete sensitivity list.

The RTL simulation does not respond correctly to all input changes because the always block is sensitive only to the select signal.

However, synthesis analyzes the intended combinational logic and implements the MUX structure.

This can result in different behavior between RTL simulation and the synthesized netlist.

RTL Simulation

Gate Level Simulation

### Key Learning

For combinational logic, the sensitivity list must include all signals that affect the output.

Using:

always @(*)

allows the simulator to evaluate the block whenever any relevant input changes.

### 4. Blocking Assignment Caveat

The blocking_caveat experiment demonstrates how the ordering of blocking assignments can produce different RTL simulation behavior compared with synthesized hardware.

Blocking assignments use:

=

and are executed sequentially in the order in which they appear.

For combinational logic, incorrect ordering can cause the simulator to use an old value of an intermediate signal.

RTL Simulation

Synthesized Logic

Gate Level Simulation

The synthesized implementation represents the combinational logic directly, while RTL simulation can exhibit different behavior because of procedural evaluation order.

## 5. Blocking vs Non-Blocking Assignments
```
Blocking Assignment
=
Statements execute sequentially.
The next statement sees the updated value.
Commonly used for combinational logic.
Non-Blocking Assignment
<=
Updates are scheduled without immediately changing the left-hand side.
Commonly used for sequential logic.
General RTL Guideline
Combinational Logic  →  Blocking (=)
Sequential Logic     →  Non-Blocking (<=)
```

### Key Takeaways
GLS verifies the synthesized gate-level implementation against the intended RTL behavior.
RTL simulation and synthesized-netlist simulation can differ because of RTL coding issues.
Missing sensitivity lists can cause synthesis-simulation mismatches.
Blocking assignments execute in procedural order.
Incorrect ordering of blocking assignments can cause unexpected RTL simulation behavior.
Ternary operators provide a concise way to describe MUX logic.
SKY130 standard-cell mapping converts RTL constructs into technology-specific cells.

---
### Tools Used
'''
Icarus Verilog
GTKWave
Yosys
SKY130 standard-cell library
Linux / VSDIAT workshop environment
'''
---
