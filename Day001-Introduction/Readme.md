# 📘 Chapter 1: Introduction
---

## 📝 1.1: VLSI Design Process

- Design complexity of VLSI circuits is increasing rapidly due to increased size (billions of transistors on chip), improved fabrication technology), efficient CAD Tools.
- There are conflicting requirements like area, speed and energy consumption.
- Present trend is to standardize the design flow with emphasis on low-power design with increased performance.

## 📝 1.2: Moore's Law

- It says that every 18 months, the number of transistors in a chip single chip will get doubled.
- Technologies following Moore's Law are: CMOS (up to 22nm), FinFet (14 nm)
- Future Trend: Quantum Technologies

## 📝 1.3: VLSI Design Flow

- It is a standardized set of design procedure which encompasses many steps starting from design idea to actual implementation:
- Design Specification -> Synthesis & Simulation -> Layout -> Testability Analysis..... many more
- ASIC DESIGN FLOW:

  1) Specification:
     * The first step of any design process is to lay down the specifications of the system.
     * The factors to be considered in this process include: performance, functionality, and physical dimensions (size of the die (chip)).
     * The fabrication technology and design techniques are also considered.

  2) Architecture design:-
     * The architecture is like a block diagram (details which are using in the design(like processors,memories) and how the are connected.)

  3) RTL design:-
     * Register transfer level(RTL): Constructing a digital design using combinational and sequential circuit in hardware description language like verilog or VHDL.
     * The above architecture is converted into verilog or VHDL code.This code describes how data is transformed as it is passed from register to register

  4) RTL verification:-
     * It is a functional verification of RTL design. After the RTL design by applying test cases we verify the design in verification stage.
     * The verification stage will take nearly 60% of the total time.
     * Performing this verification at this stage is most advantageous because correcting the faults at routing stage is difficult and takes more time.

  5) Synthesis:-
     * It is a process of converting the RTL code into gate level netlist.

  6) DFT:-
     * Design for testability(DFT) is a technique which facilitates a design to become testable after production.
     * In this stage we put extra logic along with the design logic during implementation process which helps post production process.
     * The DFT will make the testing easy at post production process.At this stage an ATPG(automatic test pattern generator) file will generated.

  7) Floorplan:-
     * The floorplan is the process of determining the macro placement,power grid, generation and i/o placement
  
  8) Placement:-
     * Placement is the process of automatically assigning correct position to standard cells on the chip with no overlapping
  
  9) CTS (clock tree synthesis):-
      * In this stage we built the clock tree by using inverters and buffers.
      * It is the process of balancing the clock skew and minimizing insertion delay in order to meet timing and power.

  10) Routing:-
      * Before the routing stage the connection between the macros,standard cells,clock,i/o port are logical connections.
      * In this stage we connect all the cells physically with the metal straps.

  11) Signoff:-
      * After the routing the physical layout of chip is completed.In signoff stage all the tests are done to check the quality and performance of the layout before tapeout.
      * After this the design is converted into GDS II file.

  12) Fabrication:-
      * By the GDS II file information we fabricate the chip.The total design is converted into chip by the manufacturing process.

  13) Packaging and testing:-
      * After the fabrication process we test the chip.If there is any fault in the design then we modify the design by repeating the above steps.
      * If there are no faults then chip will go to packaging.
  
