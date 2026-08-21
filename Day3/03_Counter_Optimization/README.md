# Counter Optimization

## Objective

To understand how synthesis tools optimize counter-based sequential logic based on the functional requirements and observability of the counter outputs.

---

## Experiments

This section contains the following experiments:

1. `counter_opt`
2. `counter_opt2`

The designs were synthesized using Yosys and mapped to the SKY130 standard-cell library.

---

## 1. `counter_opt`

This experiment demonstrates optimization of a counter where only the required portion of the counter state contributes to the observable design behavior.

### Synthesis Observation

The Yosys synthesized schematic shows a reduced sequential implementation containing the required flip-flop and associated combinational logic.

### Key Learning

Synthesis can identify sequential state that does not affect the required output and eliminate the corresponding hardware.

---

## 2. `counter_opt2`

This experiment demonstrates a counter configuration where more of the counter state is required by the design.

### Synthesis Observation

The Yosys synthesized schematic shows multiple flip-flop cells along with the associated combinational logic.

Compared with `counter_opt`, more sequential hardware is retained because the corresponding counter state contributes to the required design behavior.

### Key Learning

The amount of hardware retained after synthesis depends on how the counter state is used by the design.

---

## Comparison

| Experiment | Synthesis Result |
|---|---|
| `counter_opt` | Reduced sequential implementation |
| `counter_opt2` | Multiple sequential elements retained |

This comparison demonstrates how synthesis uses functional requirements and signal observability to optimize sequential hardware.

---

## ASIC / VLSI Perspective

Counter optimization is an important example of how RTL functionality affects ASIC implementation.

A counter may contain several state bits, but synthesis does not necessarily need to retain every state element if some state does not contribute to the required outputs.

Yosys analyzes the RTL, performs optimization, and maps the resulting logic to cells available in the target SKY130 technology library.

The synthesized schematics provide a direct view of the resulting standard-cell implementation.

---

## RTL to Synthesis Flow

```text
Verilog RTL
     ↓
Yosys RTL Processing
     ↓
Logic Optimization
     ↓
Sequential Optimization
     ↓
SKY130 Technology Mapping
     ↓
Synthesized Schematic
```
---
## Key Takeaways

Synthesis analyzes the observability of sequential state.
Unnecessary counter state can be eliminated.
Required counter state must be preserved.
Signal usage affects the amount of hardware synthesized.
Yosys performs optimization before technology mapping.
SKY130 standard cells provide the target implementation cells.

---
## Day 3 Learning

The counter optimization experiments provided practical understanding of how synthesis determines the sequential hardware required by a design and eliminates state that does not contribute to the required functionality.
