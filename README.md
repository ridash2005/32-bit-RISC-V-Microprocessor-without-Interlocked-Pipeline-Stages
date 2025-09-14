# 32-bit RISC-V Microprocessor without Interlocked Pipeline Stages

## Overview
This repository contains the Verilog implementation of a simplified 32-bit RISC-V microprocessor that omits interlocked pipeline stages. The design targets education and experimentation with basic RISC-V architecture concepts, focusing on a clean, modular CPU design without hardware interlocking for pipeline hazards.

## Features
- 32-bit RISC-V base integer instruction set (RV32I)
- Modular design with separate components for ALU, control, registers, and pipeline stages
- Pipeline implemented without interlocks; software/hardware scheduling needed for hazard management
- Basic ALU supporting arithmetic and logic operations
- Register file with read/write capabilities
- Testbench for simulation of CPU functionality

## Repository Structure and Files

- `alu.v`: Arithmetic Logic Unit performing core operations like add, sub, AND, OR, etc.
- `aluCtrl.v`: ALU control logic decoding operation signals based on instruction types
- `control.v`: Control unit generating control signals for CPU stages and data flow
- `cpu.v`: Top-level CPU module integrating pipeline stages and functional blocks
- `cpu_TB.v`: Testbench for CPU simulation and verification
- `fetch.v`: Instruction fetch stage of the pipeline fetching instructions from memory
- `fullAddSub32.v`: 32-bit adder/subtractor module used in ALU and pipeline
- `fullAdder.v`: Full adder module used to build arithmetic circuits
- `regsFile.v`: Register file module for storing general-purpose registers

### Prerequisites
- Verilog simulation software (e.g. ModelSim, Icarus Verilog, Vivado Simulator)
- Basic familiarity with RISC-V ISA and Verilog for modifications and running simulations

### Simulation
1. Compile all Verilog source files along with the testbench.
2. Run the simulation executable to verify CPU operation.
3. Inspect waveform outputs and console logs for correct execution of instructions.

Example simulation command with Icarus Verilog:
`iverilog -o riscv_cpu.vvp alu.v aluCtrl.v control.v cpu.v cpu_TB.v fetch.v fullAddSub32.v fullAdder.v regsFile.v vvp riscv_cpu.vvp`

## Design Details

### Pipeline and Hazard Handling
- The microprocessor pipeline does not include hardware interlocks to resolve hazards.
- This means instruction scheduling or inserting NOPs is required to avoid data or control hazards.

### ALU and Control
- ALU supports key operations for RV32I instruction set.
- Control logic generates appropriate signals for ALU operation, register writes, and branching.

### Register File
- Implements 32 general-purpose registers.
- Supports simultaneous reading of two registers and writing to one register per cycle.

## License
This project is licensed under the MIT License. See the LICENSE file for details.

## Contact
For questions or feedback, please open an issue on the GitHub repository or contact email: rickaryadas@gmail.com

