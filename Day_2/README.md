# Day 2 – RTL Synthesis and Optimization

## Overview

Day 2 focused on RTL synthesis, module hierarchy, flip-flop coding
styles, and synthesis optimization using Yosys and the SKY130
standard-cell library.

## Topics Covered

- Hierarchical vs. flat synthesis
- Module hierarchy and flattening
- SKY130 technology mapping
- Asynchronous reset DFF
- Asynchronous set DFF
- Synchronous reset DFF
- RTL simulation using Icarus Verilog
- Waveform analysis using GTKWave
- Arithmetic synthesis optimization
- Conditional logic optimization

## 1. Hierarchical vs. Flat Synthesis

Design hierarchy:

```text
multiple_modules
├── sub_module1
└── sub_module2
Files:

multiple_modules.v – Original RTL
multiple_modules_hier.v – Hierarchical synthesized netlist
multiple_modules_flat.v – Flattened synthesized netlist

The hierarchical netlist preserves module boundaries, while
flattening removes those boundaries and allows optimization across
the complete design.

## 2. Flip-Flop Coding Styles

Implemented and analyzed:

Asynchronous reset
Asynchronous set
Synchronous reset

Files include the corresponding RTL and testbenches.

Simulation was performed using Icarus Verilog and waveforms were
analyzed using GTKWave.

Key Learning
Asynchronous reset → independent of clock edge
Synchronous reset  → evaluated at clock edge

## 3. Synthesis Optimization
### Multiplication by 2

RTL:

assign y = a * 2;

Yosys optimized the operation to:

assign y = {a, 1'b0};

demonstrating that multiplication by a power of two can be
implemented as a shift.

### Multiplication by 9
assign y = a * 9;

The current Yosys 0.47+121 output retained the multiplication
expression in its generated Verilog representation.

### Conditional Logic
assign y = a ? b : 0;

This represents the same Boolean functionality as:

assign y = a & b;
## Key Takeaways
RTL code describes functionality, not necessarily the final gates.
Synthesis can optimize arithmetic and Boolean expressions.
Hierarchy and flattening affect the synthesized structure.
Coding style affects inferred sequential hardware.
Technology mapping converts generic logic into SKY130 standard cells.
## Tools
Yosys
Icarus Verilog
GTKWave
SKY130 HD
GVim/Vim
Git/GitHub

## Status

Day 2 – Completed
