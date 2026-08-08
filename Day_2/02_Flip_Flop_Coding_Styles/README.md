# 02 – Flip-Flop Coding Styles

This experiment demonstrates different Verilog coding styles for
flip-flops and examines how synthesis maps them to SKY130 standard
cells.

## Coding Styles Covered

- Asynchronous reset
- Asynchronous set
- Synchronous reset

## Asynchronous Reset

An asynchronous reset can change the flip-flop output without
waiting for a clock edge.

The synthesized implementation uses a dedicated reset input of
the flip-flop.

## Asynchronous Set

An asynchronous set can force the flip-flop output to the set state
independently of the clock.

## Synchronous Reset

A synchronous reset is evaluated only at the active clock edge.

The reset logic is therefore synthesized as combinational logic
feeding the D input of the flip-flop rather than directly controlling
an asynchronous reset pin.

## Technology Mapping

Yosys maps inferred flip-flops to compatible SKY130 standard cells
using the target standard-cell library.

## Verification

The designs were simulated using Icarus Verilog and examined using
GTKWave. Synthesized implementations were visualized using Yosys.
