# 📘 Chapter 2: Getting Started with Verilog
---

## 📝 2.1: Hardware Description Language (HDL)

- Classical designs uses manual methods to design the digital circuits. Using manual methods to design ICs containing several million gates is difficult.
- HDL describes the hardware of digital systems in textual form and a working circuit can be easily synthesized automatically from HDL.
- HDL acts as platform for several tools: Design Entry, Design Verification, Test Generation, Synthesis, Timing and Fault Analysis.
- Two HDLs which are more popular - Verilog and VHDL

<div align="center">
  <img src="https://github.com/user-attachments/assets/72fa8ac1-7647-4c0b-a7c9-0a993f7ad209" width="500">
</div>

## 📝 2.2: What is Verilog?

- Verilog is a hardware description language (HDL) that is used to describe digital systems and circuits in the form of code.
- It was developed by Gateway Design Automation in 1985 and later acquired by Cadence Design Systems.
- Used for both Designing & Verification and supports different level of abstractions
- The language is used to describe digital circuits hierarchically, starting with the most basic elements such as logic gates/flip-flops and building up to more complex functional blocks and systems.
- It describes a digital system as set of modules
  * Each of the module will have an interface to other modules, in addition to its description
  * The modules are interconnected using nets, which allow them to work with each other.
  * Two ways to specify a module:
    1) By specifying its internal logical structure (called structural representation)
    2) By describing its behavior in a program like manner (called behavior representation)

## 📝 2.3: What was used before Verilog?

- Before the development of Verilog, the primary HDL used for digital circuit design and verification was VHDL (VHSIC Hardware Description Language).
- VHDL was designed to be more descriptive and flexible than earlier HDLs, such as ABEL (Advanced Boolean Expression 
Language), ISP (Integrated System Synthesis Procedure), and CUPL (Compiler for Universal Programmable Logic). 
- Today, both Verilog and VHDL are widely used in digital circuit design and verification.

## 📝 2.4: Verilog vs Other Languages

- Simpler Syntax than VHDL
- Better support for describing the behavior and functionality of digital designs
- Provides a higher level of abstraction (Use of modules and ports to describe digital circuits)
- Better tool support

<div align="center">
  <img src="https://github.com/user-attachments/assets/64606569-c929-4435-998f-78032e380797" width="500">
</div>

## 📝 2.5: Simulation and Synthesis

- After specifying system in Verilog, we can do:
  1) Simulate and verify the operation
     - Requires test bench/ test harness that specifies input that are to be applied and the way outputs are to be displayed.
     - Simulation can be done using testbench to verify functionality of design coded in Verilog (DUT-Design under Test) comprising of
       - Set of stimulus for DUT
       - A monitor which captures/analyses outputs for DUT on a condition:
          - Inputs and Outputs of DUT are connected to testbench

<div align="center">
  <img src="https://github.com/user-attachments/assets/4d63f9af-b418-480f-8b9f-6235422dc4d9" width="300">
</div>

  2) Synthesis
     - Converts it to a netlist of low-level primitives.
     - The hardware can be ASIC or FPGA
     - If designed is mapped to hardware, no test bench is needed because we can actually apply the voltage signals and see the output.

<div align="center">
  <img src="https://github.com/user-attachments/assets/4afd6efb-4e21-4a21-ab8b-8ed8a86d931a" width="300">
</div>

- Some software tools for simulation: Icarus Verilog, GTKWave, Xilinx ISE, Xilinx Vivado, Modelsim
- Some software tools for synthesis: Cadence XCelium, Xilinx Vivado, ModelSim, Xilinx ISE, Synopsys Tool Suite

## 📝 2.6: Various Design Styles

1. Programmable Logic Devices
   - FPGA
   - Gate Array
2. Standard cell (Semi-custom design)
3. Full-custom Design

- Which Design style to use?
  - Tradeoff between several design parameters:
      - Hardware cost
      - Circuit delay
      - Time required
  - Optimizing these paramters is often conflicting

<div align="center">
  <img src="https://github.com/user-attachments/assets/830326ed-72a2-4318-8b09-0e278818038f" width="500">
</div>


- ASIC vs FPGA
<div align="center">
  <img src="https://github.com/user-attachments/assets/6aafbaee-5581-4d78-902e-06db2d37829d" width="600">
</div>

## 📝 2.7: VLSI Design Cycle

- Since there are large number of devices, there are optimization requirements for high performance for time to market competition and cost competition.
- Manual designs are out of question today, as we have VLSI automated CAD tools.
- Steps:
  1. System Specification
  2. Functional design
  3. Logic design
  4. Circuit design
  5. Physical design: Converts a circuit description into a geometric description. Basic steps:
     1. Partitioning, Floorplanning, Placement
     2. Routing
     3. Static Timing Analysis
     4. Signal Integrity and Crosstalk analysis
     5. Physical verification and signoff
  6. Design Verification
  7. Fabrication
  8. Packaging, Testing and Debugging
     
