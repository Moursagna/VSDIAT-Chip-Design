# Day 3 – Combinational, Sequential & Counter Optimization

## Overview

Day 3 focused on understanding how different RTL descriptions are optimized during synthesis and how the resulting logic is mapped to SKY130 standard cells.

The work was divided into three major areas:

- Combinational logic optimization
- Sequential logic optimization
- Counter optimization

The synthesized designs were analyzed using Yosys and the resulting logic structures were inspected using synthesis evidence and netlist visualization.

---

## 1. Combinational Optimization

This section explores how synthesis tools simplify and optimize combinational RTL descriptions.

The experiments include individual optimization cases as well as optimization across multiple modules.

### Experiments

- `opt_check`
- `opt_check2`
- `opt_check3`
- `opt_check4`
- `multiple_module_opt_check`

The corresponding synthesis evidence is documented inside the module folder.

📁 [01_Combinational_Optimization](./01_Combinational_Optimization/)

---

## 2. Sequential Optimization

This section explores optimization of sequential RTL using DFF-based designs.

The experiments examine different constant-driven DFF configurations and their resulting synthesized structures.

### Experiments

- DFF Constant 1
- DFF Constant 2
- DFF Constant 3
- DFF Constant 4
- DFF Constant 5

The corresponding synthesis and simulation evidence is documented inside the module folder.

📁 [02_Sequential_Optimization](./02_Sequential_Optimization/)

---

## 3. Counter Optimization

This section explores how synthesis tools optimize counter-based RTL and map the resulting logic to SKY130 standard cells.

The experiments demonstrate different counter optimization cases and their resulting synthesized structures.

📁 [03_Counter_Optimization](./03_Counter_Optimization/)

---

## Tools & Technology

The Day 3 experiments used:

- **Yosys** – RTL synthesis and optimization
- **SKY130** – standard-cell library
- **GTKWave** – waveform inspection
- **Graphviz / Yosys Netlist Visualization** – synthesized logic inspection

---

## Key Learning Outcomes

Through Day 3, I learned:

- How synthesis tools optimize RTL descriptions
- How combinational logic can be simplified during synthesis
- How constant values influence synthesized logic
- How sequential RTL is optimized
- How counter-based RTL is synthesized
- How optimized RTL is mapped to SKY130 standard cells
- How to inspect synthesized netlists using Yosys

---

## Completion Status

**Day 3 – Completed ✅**

The three optimization areas and their corresponding synthesis evidence have been organized into separate module folders.
