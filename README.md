
# Nand2Tetris: Project Solutions
### Hardware Architecture & Machine Language Implementation

This repository contains a complete set of validated solutions for the first six modules of the Nand2Tetris curriculum. The project culminates in the implementation of the **Hack Computer**, a 16-bit hardware platform built entirely from Nand gates.

## 🛠 Technical Specifications
The implementations within this repository adhere to the following architectural constraints:
* **Instruction Set:** 16-bit fixed length (A-instructions and C-instructions).
* **ALU Operations:** 18 functions including addition, subtraction, and bitwise logic, controlled by 6 control bits.
* **Memory Architecture:** Harvard architecture with separate address spaces for Instruction Memory (ROM) and Data Memory (RAM).
* **Clock Synchronization:** Sequential logic implemented using Data Flip-Flops (DFF) to manage state across clock cycles.

## 📂 Implementation Index

| Module | Component Category | Primary Deliverables |
| :--- | :--- | :--- |
| **01** | Elementary Logic | `And`, `Or`, `Xor`, `Mux`, `DMux`, `Mux16`, `Mux8Way16` |
| **02** | Combinational Logic | `HalfAdder`, `FullAdder`, `Add16`, `Inc16`, `ALU` |
| **03** | Sequential Logic | `Bit`, `Register`, `RAM8` through `RAM16K`, `PC` |
| **04** | Low-Level Software | `Mult.asm` (Algorithm), `Fill.asm` (I/O Handling) |
| **05** | Computer System | `Memory.hdl`, `CPU.hdl`, `Computer.hdl` |
| **06** | Assembler | Binary translation tool (Symbolic ASM to Machine Code) |

## ⚙️ Verification Protocol
Each `.hdl` solution has been verified against the official Nand2Tetris hardware simulator using the provided `.tst` and `.cmp` files.

To replicate the verification:
1.  Initialize the **Nand2Tetris Hardware Simulator**.
2.  Load the target `.hdl` file.
3.  Execute the corresponding `.tst` script.
4.  Confirm the output matches the comparison file (`Comparison ended successfully`).
