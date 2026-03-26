# Project 01 – Boolean Logic

## Overview

This project is the first hands-on assignment in the [Nand to Tetris](https://www.nand2tetris.org/) course (*The Elements of Computing Systems* by Nisan and Schocken, MIT Press).

The goal is to build a family of elementary logic gates starting from a single primitive gate — **NAND** — using Hardware Description Language (HDL).

---

## Background

Every digital device is built from elementary logic gates. In this project, all gates are implemented in HDL and verified with the supplied hardware simulator and test scripts.

The one primitive gate provided is **NAND**:

| a | b | NAND(a, b) |
|---|---|-----------|
| 0 | 0 | 1 |
| 0 | 1 | 1 |
| 1 | 0 | 1 |
| 1 | 1 | 0 |

All other gates in this project are built on top of NAND (or gates derived from it).

---

## Chips Implemented

### Elementary Gates

| Chip | Inputs | Outputs | Description |
|------|--------|---------|-------------|
| `Not` | `in` | `out` | Bitwise NOT |
| `And` | `a, b` | `out` | Bitwise AND |
| `Or` | `a, b` | `out` | Bitwise OR |
| `Xor` | `a, b` | `out` | Exclusive OR |
| `Mux` | `a, b, sel` | `out` | Multiplexor: outputs `a` if `sel=0`, else `b` |
| `DMux` | `in, sel` | `a, b` | Demultiplexor: routes `in` to `a` if `sel=0`, else to `b` |

### 16-bit Variants

| Chip | Inputs | Outputs | Description |
|------|--------|---------|-------------|
| `Not16` | `in[16]` | `out[16]` | 16-bit NOT |
| `And16` | `a[16], b[16]` | `out[16]` | 16-bit AND |
| `Or16` | `a[16], b[16]` | `out[16]` | 16-bit OR |
| `Mux16` | `a[16], b[16], sel` | `out[16]` | 16-bit Multiplexor |

### Multi-Way / Multi-Bit Gates

| Chip | Inputs | Outputs | Description |
|------|--------|---------|-------------|
| `Or8Way` | `in[8]` | `out` | OR of all 8 input bits |
| `Mux4Way16` | `a[16], b[16], c[16], d[16], sel[2]` | `out[16]` | 4-way 16-bit Multiplexor |
| `Mux8Way16` | `a..h[16], sel[3]` | `out[16]` | 8-way 16-bit Multiplexor |
| `DMux4Way` | `in, sel[2]` | `a, b, c, d` | 4-way Demultiplexor |
| `DMux8Way` | `in, sel[3]` | `a, b, c, d, e, f, g, h` | 8-way Demultiplexor |

---

## Implementation Highlights

- **Not** — Built by feeding the same input into both ports of a NAND gate.
- **And** — NAND followed by NOT.
- **Or** — De Morgan's Law: `Or(a,b) = Nand(Not(a), Not(b))`.
- **Xor** — Combined using `Nand` and `Or`, then `And`.
- **Mux** — Uses `Not`, `And`, and `Or` to select between two inputs based on `sel`.
- **DMux** — Uses `Not` and `And` to route a single input to one of two outputs.
- **Multi-way gates** — Built hierarchically from their simpler counterparts (e.g., `Mux4Way16` uses two `Mux16` calls, `Mux8Way16` uses two `Mux4Way16` calls).

---

## Files

| File | Description |
|------|-------------|
| `*.hdl` | Hardware Description Language implementation |
| `*.tst` | Test script for the hardware simulator |
| `*.cmp` | Expected output (compare file) |
| `*.out` | Actual output produced by the simulator |

---

## How to Test

1. Download the [Nand2Tetris Software Suite](https://www.nand2tetris.org/software).
2. Launch the **Hardware Simulator**.
3. Load a `.tst` file (e.g., `And.tst`).
4. Click **Run** to execute the tests.
5. A success message means the `.out` file matches the `.cmp` file.

---

## Concepts Covered

- Boolean algebra and truth tables
- Hardware Description Language (HDL)
- Gate-level hardware design
- Composing complex chips from simpler building blocks
- Multiplexors and demultiplexors as fundamental hardware routing elements
