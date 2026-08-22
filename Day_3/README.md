# Day 3 – Combinational, Sequential & Counter Optimization

## Overview

Day 3 focused on understanding how RTL coding style affects synthesized hardware and how synthesis tools optimize RTL descriptions.

The experiments covered:
- Combinational logic optimization
- Sequential logic optimization
- Counter optimization
- Constant propagation
- Logic simplification
- Multiple-module optimization
- Mapping optimized RTL to SKY130 standard cells

The designs were simulated where applicable and synthesized using Yosys with the SKY130 standard-cell library.

---

## 1. Combinational Optimization

This section demonstrates how synthesis tools optimize combinational RTL by simplifying Boolean expressions, propagating constants, removing redundant logic, and optimizing multiple-module designs.

### Experiments

| Experiment | Focus |
|---|---|
| `opt_check` | Combinational optimization |
| `opt_check2` | Logic simplification |
| `opt_check3` | Constant propagation / optimization |
| `opt_check4` | Further combinational optimization |
| `multiple_module_opt` | Optimization across module hierarchy |

📁 [01_Combinational_Optimization](./01_Combinational_Optimization/)

---

## 2. Sequential Optimization

This section explores synthesis optimization of sequential logic, including constant-driven flip-flops and cases where sequential logic can be simplified or removed.

### Experiments

The experiments demonstrate different DFF configurations and their resulting synthesized structures.

📁 [02_Sequential_Optimization](./02_Sequential_Optimization/)

---

## 3. Counter Optimization

This section examines how synthesis tools optimize counter-based RTL and map the resulting logic to standard cells.

### Experiments

The counter experiments demonstrate optimization and SKY130 standard-cell mapping of counter logic.

📁 [03_Counter_Optimization](./03_Counter_Optimization/)

---

## Synthesis Technology

The designs were synthesized using:

- **Yosys** – RTL synthesis
- **SKY130** – open-source standard-cell technology
- **GTKWave** – waveform analysis where applicable
- **Graphviz / Yosys netlist visualization** – synthesized logic inspection

---

## Key Learning Outcomes

Through these experiments, I learned:

- How synthesis optimizes RTL descriptions
- How constant propagation simplifies logic
- How redundant logic can be removed
- How combinational logic is transformed into standard cells
- How sequential logic is optimized
- How counters are represented after synthesis
- How RTL coding style influences synthesized hardware
- How to inspect synthesized netlists using Yosys

---

## Completion Status

**Day 3 – Completed ✅**

The experiments and synthesis evidence have been documented in the corresponding sections.
