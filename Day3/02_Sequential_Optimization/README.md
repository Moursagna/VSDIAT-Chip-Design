# Sequential Logic Optimization

## Objective

To understand how synthesis tools optimize sequential RTL containing flip-flops, constant values, reset conditions, and related sequential logic, and how the optimized designs are mapped to SKY130 standard cells.

---

## Experiments

This section contains the following experiments:

1. `dff_const1`
2. `dff_const2`
3. `dff_const3`
4. `dff_const4`
5. `dff_const5`

The designs were simulated using GTKWave and synthesized using Yosys.

---

## 1. `dff_const1`

This experiment demonstrates sequential logic with a flip-flop whose data input is driven by a constant value.

### RTL Simulation

The GTKWave waveform shows the clock, reset, and output signals.

### Synthesis Observation

The Yosys synthesized schematic shows the flip-flop mapped to a SKY130 standard-cell implementation with reset functionality.

### Key Learning

Constant-driven sequential logic can be recognized and optimized by synthesis while maintaining the required sequential behavior.

---

## 2. `dff_const2`

This experiment demonstrates a flip-flop with constant data and reset control.

### RTL Simulation

The GTKWave waveform shows the clock, reset, and output behavior of the design.

### Synthesis Observation

The synthesized schematic demonstrates the optimized sequential implementation produced by Yosys.

### Key Learning

Synthesis analyzes constant values in sequential logic and determines the appropriate hardware implementation.

---

## 3. `dff_const3`

This experiment demonstrates sequential logic involving constant-driven behavior and reset control.

### RTL Simulation

The GTKWave waveform shows the clock, reset, and output transitions.

### Synthesis Observation

The Yosys schematic shows the synthesized sequential implementation using SKY130 standard cells.

### Key Learning

Sequential elements that are required for the observable behavior of the design are preserved during synthesis.

---

## 4. `dff_const4`

This experiment demonstrates sequential optimization involving constant values and multiple sequential signals.

### RTL Simulation

The GTKWave waveform contains the clock, reset, `q1`, and `q` signals.

### Synthesis Observation

The Yosys synthesized schematic shows the resulting sequential implementation and the logic associated with the outputs.

### Key Learning

Synthesis evaluates the functional relationships between sequential signals and optimizes the resulting hardware.

---

## 5. `dff_const5`

This experiment further demonstrates sequential optimization involving multiple flip-flop outputs.

### RTL Simulation

The GTKWave waveform shows the clock, reset, `q1`, and `q` signals and their transitions.

### Synthesis Observation

The Yosys schematic shows the resulting SKY130 standard-cell implementation containing the required sequential elements and associated logic.

### Key Learning

The synthesized hardware depends on the functional relationship between sequential elements and their observable outputs.

---

## RTL to Synthesis Flow

```text
Verilog RTL
     ↓
RTL Simulation
     ↓
GTKWave Waveform Analysis
     ↓
Yosys Optimization
     ↓
Technology Mapping
     ↓
SKY130 Standard Cells
```

---

## ASIC / VLSI Perspective

These experiments demonstrate how synthesis handles sequential RTL containing constant values, reset conditions, and related sequential signals.

The experiments illustrate important synthesis concepts such as:

Constant propagation
Sequential logic optimization
Flip-flop optimization
Reset handling
Logic simplification
Technology mapping

The synthesized schematics show how the optimized RTL is implemented using cells from the SKY130 standard-cell library.
---

## Key Takeaways
Constant values can influence synthesized sequential hardware.
Synthesis can optimize unnecessary sequential logic.
Required flip-flops are preserved to maintain functionality.
Reset behavior affects the synthesized implementation.
Yosys can map optimized sequential logic to SKY130 standard cells.
RTL coding style directly influences the resulting hardware.

---

## Day 3 Learning

The sequential optimization experiments provided practical understanding of how synthesis transforms flip-flop-based RTL into an optimized ASIC-oriented implementation and maps it to SKY130 standard cells.
