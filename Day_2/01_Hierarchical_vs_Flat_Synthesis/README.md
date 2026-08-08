# 01 – Hierarchical vs Flat Synthesis

This experiment demonstrates the difference between hierarchical
RTL synthesis and flattened synthesis using Yosys and the SKY130
HD standard-cell library.

## Concepts Covered

- RTL module hierarchy
- Submodule instantiation
- Hierarchical synthesis
- Submodule-level synthesis
- Flattening
- Technology mapping
- SKY130 standard-cell representation

## Design Structure

The design consists of a top-level module:

`multiple_modules`

which instantiates:

- `sub_module1`
- `sub_module2`

The hierarchical implementation preserves these module boundaries.

The `flatten` command removes the hierarchy and combines the logic
into the top-level implementation.

## Synthesis Flow

```text
Verilog RTL
    ↓
Yosys
    ↓
Hierarchy analysis
    ↓
Logic synthesis
    ↓
ABC technology mapping
    ↓
SKY130 standard cells
    ↓
Hierarchical / flattened netlist
