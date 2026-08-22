# Day 4 – GLS and Synthesis Simulation Mismatch

## Objective

To understand the differences between RTL simulation and synthesized/gate-level behavior and to study how RTL coding constructs can affect synthesis results.

## Experiments

The experiments covered:

- RTL simulation
- Synthesis analysis
- Gate-level simulation (GLS)
- Blocking assignment behavior
- Ternary operator based multiplexing
- Simulation and synthesis mismatch analysis

## Simulation and Synthesis Evidence

### Bad MUX

![Bad MUX Simulation](bad_mux_tb_sim.png)

![Bad MUX GLS](GLS_tb_bad_mux.v.png)

### Blocking Assignment Caveat

![Blocking Assignment Simulation](blocking_caveat_sim.v.png)

![Blocking Assignment Synthesis](blocking_caveat_synth.png)

![Blocking Assignment GLS](GLS_blocking_caveat.png)

### Ternary Operator MUX

![Ternary Operator Simulation](sim_ternary_operator_mux.png)

![Ternary Operator Synthesis](ternary_operator_mux_synth.png)

![Ternary Operator GLS](GTKWave_ternary_mux_GLS.png)

## Key Learning

- Understanding the purpose of gate-level simulation
- Comparing RTL simulation with synthesized behavior
- Understanding simulation and synthesis mismatches
- Understanding the effect of RTL coding style on synthesis
- Understanding blocking assignment behavior
- Understanding synthesis of ternary-operator based multiplexers
- Inspecting synthesized and gate-level simulation waveforms

## Completion Status

**Day 4 – Completed ✅**
