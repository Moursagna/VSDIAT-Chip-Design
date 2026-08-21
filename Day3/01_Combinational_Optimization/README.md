# Combinational Logic Optimization

## Objective

To understand how synthesis tools optimize combinational RTL and map the optimized logic to standard cells in the target technology library.

---

## Experiments

This section contains the following synthesis experiments:

1. `opt_check`
2. `opt_check2`
3. `opt_check3`
4. `opt_check4`
5. `multiple_module_opt`

---

## 1. `opt_check`

The synthesized design is optimized and mapped to a SKY130 2-input AND standard cell:

`sky130_fd_sc_hd__and2_0`

### Synthesis Observation

The Yosys schematic demonstrates that the logic has been reduced to a simple AND implementation.

---

## 2. `opt_check2`

The synthesized design is mapped to the SKY130 2-input OR standard cell:

`sky130_fd_sc_hd__or2_0`

### Synthesis Observation

The original RTL logic is simplified during synthesis and represented using an appropriate standard-cell implementation.

---

## 3. `opt_check3`

The synthesized design is mapped to a SKY130 3-input AND standard cell:

`sky130_fd_sc_hd__and3_1`

### Synthesis Observation

Yosys recognizes the equivalent Boolean function and maps it directly to a suitable multi-input standard cell.

---

## 4. `opt_check4`

The synthesized design is mapped to a SKY130 2-input XNOR standard cell:

`sky130_fd_sc_hd__xnor2_1`

### Synthesis Observation

Boolean optimization allows the equivalent logic to be represented using an XNOR standard cell.

---

## 5. `multiple_module_opt`

This experiment demonstrates optimization involving logic distributed across multiple RTL modules.

The synthesized design is mapped to a SKY130 compound logic cell:

`sky130_fd_sc_hd__a21o_1`

### Synthesis Observation

The synthesis process can optimize logic relationships across module boundaries and produce a compact standard-cell implementation.

---

## ASIC / VLSI Learning

These experiments demonstrate that synthesis does not simply translate each Verilog statement directly into individual gates.

Instead, synthesis:

1. Analyzes the Boolean functionality.
2. Simplifies equivalent logic.
3. Removes unnecessary logic.
4. Restructures the design where possible.
5. Maps the optimized logic to cells available in the target technology library.

This optimization process is important for achieving efficient **area, timing, and power** characteristics in ASIC designs.

---

## Evidence

The corresponding Yosys synthesized schematics are included in the `Images` directory.
