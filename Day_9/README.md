# DAY 9 — SKY130 Module 4: Timing Analysis, CTS and Post-CTS STA

## Overview

Day 9 focuses on the timing-aware stage of the SKY130 ASIC physical design flow. The work connects **standard-cell timing models**, **setup/hold timing**, **clock tree synthesis (CTS)**, **placement**, **clock skew**, and **static timing analysis (STA)**.

The objective is to understand how a synthesized digital design is analyzed and optimized for timing after physical implementation, and how clock distribution affects the timing of sequential logic.

---

## Day 9 Learning Flow

```text
Standard-Cell Timing Models
          ↓
Delay Tables
          ↓
Setup / Hold Timing
          ↓
Clock Tree Synthesis (CTS)
          ↓
Clock Distribution
          ↓
Placement / Physical Implementation
          ↓
Post-CTS Timing
          ↓
Clock Skew / Glitch Analysis
          ↓
Static Timing Analysis (STA)
          ↓
WNS / TNS and Timing Violations
```

---

# 1. Timing Modeling and Delay Tables

Timing analysis begins with accurate cell timing information. Standard-cell libraries contain characterized delay and transition information for different combinations of:

- Input slew
- Output load capacitance
- Cell type
- Input/output pin transitions

Delay tables allow the STA engine to estimate the propagation delay of a standard cell under a particular electrical condition.

### Important concepts

- **Input slew** — transition time of the input signal.
- **Output load** — capacitive load driven by the cell.
- **Cell delay** — propagation delay through the standard cell.
- **Buffer delay** — delay introduced by clock/data buffering.
- **Slew degradation** — change in transition quality as a signal propagates through logic.

### Delay Table — Buffering Level 1

![Delay Table Buffering Level 1](./images/Delay_Table_Buffering_1.png)

### Delay Table — Buffering Level 2

![Delay Table Buffering Level 2](./images/Delay_Table_Buffering_2.png)

### Delay Components

![Delta Delay](./images/Delta_delay.png)

The delay observed on a physical path is not determined only by the logic-cell delay. Interconnect resistance, capacitance, buffering, and physical wire length also contribute to the total delay.

---

# 2. Setup and Hold Timing Analysis

Sequential timing analysis verifies whether data reaches a flip-flop within the required timing window relative to the clock edge.

## 2.1 Setup Timing

Setup analysis checks whether data arrives sufficiently **before the active clock edge**.

Conceptually:

```text
Launch FF ─── Combinational Logic ─── Capture FF
    │                                  │
 Launch Clock                      Capture Clock
```

If data arrives too late, a **setup violation** occurs.

### Setup Analysis with Ideal Clock

![Setup Analysis — Ideal Clock](./images/Setup_analysis_ideal_clk.png)

### Setup Analysis with Real Clock

![Setup Analysis — Real Clock](./images/Setup_Analysis_real_clk.png)

### Setup Timing Concept

![Setup Time](./images/Setup_time.png)

---

## 2.2 Hold Timing

Hold analysis checks whether the data remains stable for the required interval **after the active clock edge**.

If new data reaches the capture flip-flop too early, a **hold violation** can occur.

### Hold Analysis with Ideal Clock

![Hold Analysis — Ideal Clock](./images/hold_analysis_ideal_clk.png)

### Hold Analysis with Real Clock

![Hold Analysis — Real Clock](./images/Hold_Analysis_real_clk.png)

### Hold Timing Concept

![Hold Time](./images/Hold_time.png)

---

## 2.3 Ideal Clock vs Real Clock

An ideal clock assumes an idealized clock arrival relationship without physical clock-network effects.

After CTS, the clock is distributed through an actual network containing:

- Clock buffers
- Interconnect
- Wire resistance
- Wire capacitance
- Different path lengths

Therefore, real-clock analysis includes clock insertion delay and clock skew.

---

# 3. Clock Tree Synthesis (CTS)

Clock Tree Synthesis creates a physical clock distribution network from the clock source to the sequential elements in the design.

The primary objectives of CTS include:

- Delivering the clock to all required sequential elements.
- Controlling clock latency.
- Reducing clock skew.
- Maintaining acceptable transition characteristics.
- Building a physically realizable clock network.

---

## 3.1 H-Tree Clock Distribution

An H-tree is a symmetric clock-distribution structure intended to provide similar path lengths to different branches.

![CTS H-Tree](./images/CTS_H-Tree.png)

---

## 3.2 Clock Buffers

Clock buffers are inserted to drive the capacitive load of the clock network and maintain acceptable signal transition characteristics.

![CTS Buffer](./images/CTS_Buffer.png)

---

## 3.3 Clock Net Shielding

Clock nets are sensitive to coupling and noise. Shielding can be used to reduce unwanted capacitive coupling from neighboring signal wires.

![CTS Net Shielding](./images/CTS_Net_shielding.png)

---

## 3.4 CTS Terminal / Clock Network

The resulting clock network connects the clock source to the required sequential elements through the synthesized clock distribution structure.

![CTS Terminal](./images/CTS_Terminal.png)

---

# 4. Physical Implementation and Placement

Timing is strongly affected by physical implementation because interconnect delay depends on the actual geometry of the design.

The physical design stage therefore considers:

- Floorplan
- Placement
- Cell locations
- Routing resources
- Interconnect length
- Parasitic effects

### Floorplan / Terminal View

![Floorplan Terminal](./images/floorplan_terminal.png)

### Layout Grid

![Layout Grid](./images/Layout_grid.png)

### Placement

![Placement](./images/placement.png)

### Placement — Additional View

![Placement 1](./images/placement_1.png)

### Expanded Placement View

![Placement Expanded](./images/placement_expand.png)

### Placement Terminal View

![Placement Terminal](./images/placement_terminal.png)

---

# 5. Post-CTS Timing Effects

After CTS, timing analysis becomes more realistic because the clock network is physically implemented.

Important effects include:

- Clock insertion delay
- Clock skew
- Clock uncertainty
- Clock-buffer delay
- Interconnect RC delay
- Crosstalk / coupling effects
- Clock waveform degradation

---

## 5.1 Clock Skew

Clock skew is the difference in clock arrival time between two relevant sequential elements.

For two clock paths:

```text
Skew = |Δ1 - Δ2|
```

where the clock arrival times are affected by the physical clock network and its associated delays.

![Clock Skew](./images/Skew.png)

---

## 5.2 Glitch Analysis

Clock and signal integrity must also be considered during physical implementation. Unwanted transitions or glitches can affect timing and functional behavior depending on where they occur.

![Glitch Analysis](./images/Glitch.png)

---

# 6. Static Timing Analysis (STA)

Static Timing Analysis verifies timing behavior without requiring exhaustive functional simulation of every possible input sequence.

STA analyzes timing paths and determines whether the design satisfies its timing constraints.

Important quantities include:

### Data Arrival Time

The time at which data reaches the capture point.

### Data Required Time

The latest time by which data must arrive to satisfy the timing constraint.

### Slack

Slack represents the timing margin.

For setup analysis:

```text
Slack = Data Required Time - Data Arrival Time
```

A negative setup slack indicates that the analyzed path does not meet the corresponding setup requirement.

---

## STA Output

![STA Report](./images/STA.png)

![STA Report — Additional](./images/STA_1.png)

The terminal reports contain timing-path information such as cell delays, net delays, clock information, data arrival time, data required time, and slack.

---

# 7. WNS and TNS

Two important summary metrics used during timing analysis are:

## Worst Negative Slack (WNS)

WNS represents the most negative slack among the analyzed violating paths.

```text
WNS = minimum slack
```

For a timing-clean group of paths, the corresponding worst slack is non-negative.

## Total Negative Slack (TNS)

TNS represents the accumulated negative slack across violating paths.

```text
TNS = sum of negative slacks
```

WNS identifies the worst individual timing margin, while TNS indicates the aggregate magnitude of timing violations.

---

# 8. Key Engineering Relationships

The major relationships studied in Day 9 can be summarized as follows:

```text
Cell Characterization
        │
        ├── Input Slew
        ├── Output Load
        └── Cell Delay
                │
                ▼
        Timing Analysis
                │
        ┌───────┴────────┐
        ▼                ▼
      Setup             Hold
        │                │
        └───────┬────────┘
                ▼
               CTS
                │
        ┌───────┼────────┐
        ▼       ▼        ▼
      Buffers  Skew    Clock RC
                │
                ▼
        Post-CTS STA
                │
        ┌───────┴────────┐
        ▼                ▼
       WNS              TNS
```

---

# 9. Practical VLSI Significance

Day 9 connects timing theory with actual ASIC implementation.

A design may be logically correct at RTL and still fail timing after synthesis or physical implementation because:

- Logic paths have finite propagation delay.
- Standard cells have different delay characteristics.
- Interconnect contributes resistance and capacitance.
- Clock paths have insertion delay.
- Different clock paths can have different arrival times.
- Setup and hold constraints must both be satisfied.

Therefore, timing closure is an iterative process involving RTL, synthesis, cell selection, buffering, placement, CTS, routing, parasitic extraction, and STA.

---

# 10. Day 9 Key Learnings

By completing this module, the following concepts were studied:

- Standard-cell timing characterization
- Input slew and output load
- Delay tables
- Cell and buffer delay
- Setup timing
- Hold timing
- Ideal-clock timing analysis
- Real-clock timing analysis
- Clock Tree Synthesis
- H-tree clock distribution
- Clock buffering
- Clock net shielding
- Placement and physical implementation
- Clock insertion delay
- Clock skew
- Glitch analysis
- Static Timing Analysis
- Data arrival time
- Data required time
- Slack
- WNS
- TNS
- Timing violations and timing closure

---

# 11. Day 9 Completion Checklist

- [x] Studied timing-model concepts
- [x] Studied delay tables and buffering
- [x] Studied setup timing
- [x] Studied hold timing
- [x] Compared ideal and real clock behavior
- [x] Studied Clock Tree Synthesis
- [x] Studied H-tree clock distribution
- [x] Studied clock buffering
- [x] Studied clock net shielding
- [x] Reviewed physical placement
- [x] Studied clock skew
- [x] Studied glitch behavior
- [x] Reviewed STA reports
- [x] Studied WNS and TNS
- [x] Connected timing analysis with physical implementation

---

## Conclusion

Day 9 establishes the connection between **timing models, clock distribution, physical implementation, and STA** in the SKY130 ASIC flow.

The central idea is:

> **Physical implementation changes timing, and STA is used to measure whether the implemented design satisfies its timing constraints.**

This forms the foundation for understanding timing closure in a complete ASIC design flow.
