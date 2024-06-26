# MIPS-inspired-Processor-Design

## Overview

This project involves designing and synthesizing a 32-bit RISC-like processor using Verilog. The processor will be implemented with a variety of features and instruction sets as detailed below. The project will proceed in several steps, each focusing on a different aspect of the processor's design and implementation.

## Specifications

### General Features
- **Registers:**
  - Sixteen 32-bit general-purpose registers (R0..R15) with two read ports and one write port.
  - R0 is a special read-only register containing the fixed value 0.
- **Memory:**
  - Byte addressable with a 32-bit memory address.
  - Operations on 32-bit data, with loads and stores occurring from memory addresses that are multiples of 4.
- **Registers:**
  - 32-bit Program Counter (PC).
  - 32-bit Stack Pointer (SP).

### Addressing Modes
1. Register addressing
2. Immediate addressing
3. Base addressing for accessing memory
4. PC relative addressing for branch
5. SP relative addressing

### Instruction Set

#### Arithmetic and Logic Instructions
- **ADD, SUB, AND, OR, XOR, NOT, SLA, SRA, SRL**
- Immediate addressing versions with suffix "I" (e.g., ADDI, SUBI)
- Example uses:
  - `ADDI R3, #25` // R3 <= R3 + 25
  - `ADD R1, R2, R3` // R1 <= R2 + R3
  - `SLA R5, R7` // R5 <= R5 << R7[0]

#### Load and Store Instructions
- **LD, ST, LDSP, STSP** (32-bit loads and stores)
- Register indexed addressing
- Example uses:
  - `LD R2, 10(R6)` // R2 <= Mem[R6 + 10]
  - `ST R2, -2(R11)` // Mem[R11 - 2] <= R2

#### Branch Instructions
- **BR, BMI, BPL, BZ**
- Example uses:
  - `BR #10` // PC <= PC + 10
  - `BMI R5, #-10` // PC <= PC - 10 if (R5 < 0)

#### Stack Instructions
- **PUSH, POP, CALL, RET**
- Example uses:
  - `PUSH R6` // Push R6 onto the stack
  - `CALL #1000` // SP <= SP - 4; Mem[SP] <= PC + 4; PC <= PC + 1000

#### Register Transfer
- **MOVE**
- Example uses:
  - `MOVE R10, R5` // R10 = R5

#### Program Control
- **HALT, NOP**

## Steps of Implementation

### Step 1: ALU Design
- Design the ALU covering all required functions.
- Write a test bench to verify functionality through simulation.
- Test on FPGA kit.
- **Deadline:** 04/10/2023

### Step 2: Instruction Format and Data Path Design
- Design the instruction format.
- Provide overall schematic diagram of the data path.
- Detailed design of the control unit.
- **Deadline:** 11/10/2023

### Step 3: Register Bank Integration
- Implement the register bank and integrate it with the ALU.
- Write a top-level module for testing the modules.
- Test operations like `Rx = Ry op Rz` on FPGA.
- **Deadline:** 18/10/2023

### Step 4: Memory and Processor Completion
- Implement memory as a one-dimensional register array.
- Complete the processor design with the following steps:
  - Implement the data path using structural design methodology.
  - Prepare a table of RTL micro-operations for typical instructions (e.g., ADD, LD, BMI).
  - Implement the control path using behavioral design of the required FSM.
  - Test functionality on FPGA.
  
### Assembler Development
- Developed a Python-based assembler with assembly syntax.
- Facilitates assembly code execution on Nexys FPGA for hardware verification.

## Getting Started

1. Clone the repository:
    ```sh
    git clone https://github.com/Sukhomay/MIPS-inspired-Processor-Design
    cd code
    ```
2. Follow the implementation steps as outlined above.
3. Use the provided test benches to verify each module.
4. Download the design onto an FPGA kit for final testing.


## Contributing

Contributions are welcome! Please fork the repository and create a pull request with your changes.

## License

This project is licensed under the MIT License. See the LICENSE file for details.

---

Happy coding! If you have any questions, feel free to open an issue or contact the project maintainers.
