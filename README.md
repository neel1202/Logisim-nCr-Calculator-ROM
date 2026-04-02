# nCr (Combination) Calculator - 3-Bit Logisim Implementation

A professional Logisim implementation of an **nCr Calculator** using ROM-based lookup tables for high-speed combination calculations. This project supports 3-bit inputs for both $n$ and $r$, covering all possible combinations from $0C0$ up to $7C7$ using the mathematical foundations of Pascal's Triangle.

## 🚀 Overview

This circuit calculates the number of ways to choose $r$ elements from a set of $n$ elements, denoted as:

$$nCr = \binom{n}{r} = \frac{n!}{r!(n-r)!}$$

By utilizing **Read-Only Memory (ROM)**, the circuit avoids complex divisional and factorial arithmetic paths, instead retrieving the pre-calculated results in a single clock cycle.

## 🧠 Logic & Design

### Mathematical Foundation
The calculator is built upon **Pascal's Triangle**. Since the inputs are 3-bit ($n \in [0, 7]$ and $r \in [0, 7]$), we pre-mapped all 64 possible address combinations (where $n < r$ results in 0, as mathematically defined).

### ROM Mapping
The 6-bit address for the ROM is formed by concatenating the 3-bit $n$ and 3-bit $r$ inputs:
- **Address Format:** `[n2 n1 n0 r2 r1 r0]`
- **Capacity:** $2^6 = 64$ memory locations.
- **Data:** Each location stores the corresponding $nCr$ value.

### Key Components
- **Input Pins:** 3-bit binary pins for $n$ and $r$.
- **ROM Chips:** Configured with pre-calculated hexadecimal values representing Pascal's Triangle rows.
- **7-Segment Display System:** Decodes the inputs and results for human-readable output.
- **BCD Decoder (Subcircuit):** A custom-designed `display` subcircuit for driving the 7-segment displays.

## 🛠️ Features

- **Instant Results:** ROM-based lookup provides results without propagation delay from arithmetic units.
- **Visual Feedback:** Integrated 7-segment displays for intuitive monitoring of values.
- **Error Handling:** Mathematically correct output ($0$) for cases where $r > n$.
- **High Range:** Supports up to $7C3$ and $7C4$, which equal $35$ (displayed in hex/binary).

## 📥 How to Use

1. **Prerequisite:** Ensure you have [Logisim (v2.7.x)](http://www.cburch.com/logisim/) installed.
2. **Open File:** Load `ncr2.circ` into Logisim.
3. **Simulate:**
   - Use the **Poke Tool** to toggle the 3-bit input pins for $n$ and $r$.
   - Observe the result on the output pins and the 7-segment displays.
   - Example: Set $n = 5$ (`101`) and $r = 2$ (`010`). The result will be $10$ (`001010` in binary / `A` in hex).

## 👥 Authors
- **24bCE123**
- **24bCE122**

---
*Created for Computer Organization and Architecture Lab - High-performance combinatorial logic using ROM.*
