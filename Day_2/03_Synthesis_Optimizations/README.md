# 03 – Synthesis Optimizations

This experiment demonstrates how synthesis tools optimize
arithmetic RTL expressions into simpler hardware structures.

## Experiments

- Multiplication by 2
- Multiplication by 8/9

## Multiplication by 2

Multiplication by a power of two can be implemented using a
binary shift.

For example:

```text
a × 2 = a << 1
