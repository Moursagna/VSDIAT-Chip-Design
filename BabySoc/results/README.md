# BabySoC Results

This directory contains the key results and visual evidence from the BabySoC RTL-to-post-synthesis flow.

## Results Included

### 1. BabySoC Architecture

The architecture diagram shows the main blocks of the BabySoC and their interconnections.

**File:** `architecture.png`

### 2. Pre-Synthesis Simulation

The waveform shows the functional behavior of the BabySoC RTL before synthesis.

**File:** `pre_synthesis_waveform.png`

The main signals observed include:

- `CLK`
- `REF`
- `reset`
- `VCO_IN`
- `VREFH`
- `RV_TO_DAC[9:0]`
- `OUT`

### 3. Synthesis Results

The synthesis statistics show the standard-cell implementation generated after Yosys synthesis and SKY130 technology mapping.

**File:** `synthesis_statistics.png`

### 4. Post-Synthesis Simulation

The waveform shows the functional behavior of the synthesized gate-level BabySoC implementation.

**File:** `post_synthesis_waveform.png`

The post-synthesis simulation uses SKY130 standard-cell Verilog models and verifies the functional behavior of the synthesized implementation.

---

## Flow Represented

```text
RTL
  |
  v
Pre-Synthesis Simulation
  |
  v
Yosys Synthesis
  |
  v
SKY130 Technology Mapping
  |
  v
Gate-Level Netlist
  |
  v
Post-Synthesis Simulation
