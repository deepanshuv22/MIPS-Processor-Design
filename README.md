**5-Stage Pipelined MIPS32 Processor**
Overview:
This repository contains a Register-Transfer Level (RTL) implementation of a 32-bit Pipelined MIPS Processor written in Verilog. The design features a classic 5-stage RISC pipeline architecture (Instruction Fetch, Decode, Execute, Memory Access, and Write-Back) and employs a custom two-phase clocking scheme to ensure robust pipeline synchronization and prevent race conditions.

Key Architectural Features
5-Stage Pipeline: Implements structural hazard mitigation by isolating operations into IF, ID, EX, MEM, and WB stages.

Two-Phase Clocking: Utilizes clk1 and clk2 to separate pipeline stage triggers. clk1 drives the Fetch, Execute, and Write-Back stages, while clk2 handles the Decode and Memory stages.

32-bit Datapath: Includes a 32x32-bit Register File and a 1024x32-bit unified Instruction/Data Memory.

Branch Handling: Features basic control hazard management utilizing a TAKEN_BRANCH flag to disable succeeding instructions and flush the pipeline when a branch is executed.

Supported Instruction Set Architecture (ISA)
The processor supports a curated subset of the MIPS32 ISA, categorized as follows:

R-Type (Register-Register): ADD, SUB, AND, OR, SLT (Set Less Than), MUL

I-Type (Register-Immediate): ADDI, SUBI, SLTI

Memory Operations: LW (Load Word), SW (Store Word)

Control Flow: BEQZ (Branch if Equal to Zero), BNEQZ (Branch if Not Equal to Zero)

System/Halt: HLT (Halts execution and disables write-backs)

Pipeline Stage Breakdown
Instruction Fetch (IF): Fetches the next instruction from memory based on the Program Counter (PC). Updates the PC and handles branch target addresses.

Instruction Decode (ID): Decodes the fetched instruction, extracts opcodes and operands, reads from the Register File, and sign-extends immediate values.

Execute (EX): The ALU performs arithmetic/logical operations, calculates branch conditions, and computes memory addresses for load/store operations.

Memory Access (MEM): Handles data reading from or writing to the synchronous Data Memory.

Write Back (WB): Writes the ALU result or memory load data back into the destination register within the Register File.
