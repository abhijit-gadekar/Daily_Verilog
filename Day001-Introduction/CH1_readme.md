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

## 📝 1.4: Use of CAD Tools

- They are based on Hardware Description Languages. HDLs provide formats for representing outputs of various design steps.
- A CAD Tool transforms its HDL input into a HDL output that contains more detailed information about the hardware
  - Behavioral Level to Register Transfer Level
  - Register Transfer Level to Gate Level
  - Gate Level to Transistor Level
  - Transistor Level to Layout Level
- E.g. of HDLs: Verilog, VHDL, SystemC, SystemVerilog, etc.

## 📝 1.5: Steps of the Design Flow

<div align="center">
  <img src="https://github.com/user-attachments/assets/16a98ade-4090-4339-9a38-032efcc8eb36" width="300">
</div>

1) Behavioral Design:
   * Can be pseudo code in a hardware description language or a flow graph notation
   * Specifies functionality of design in terms of its behavior using Boolean Expressions, Truth Table, FSM (Finite State Machine) Behavior, and high level algorithm
   * Needs to be synthesized into more detailed specifications for hardwaee realization.

2) Data Path Design:
   * It generates a netlist of register transfer level components like registers, adders, multipliers, multiplexers, decoders, etc.
   * A netlist is a directed graph where vertices indicate components and edges indicate interconnections. A netlist specification is also referred as structural design.
   * Netlist may be specified at various levels where components may be functional modules, gates or transistors. It is systematically transformed from one level to the next.

3) Logic Design
   * Generates a netlist of gates, flip-flops, or standard cells
   * A standard cell is pre-designed circuit module (like gates, flip-flops, multiplexers, etc) at layout level
   * Various logic optimization techniques are used to obtain a cost effective design
   * There may be conflicting requirements during optimization:
     * Minimize number of gates
     * Minimize number of gate levels (delays)
     * Minimize signal transition activites (i.e. dynamic power)

4) Physical Design and Manufacturing
   * Generate the final layout that can be sent for fabrication
   * The layout contains a large number of regular geometric shapes corresponding to different fabrication layers

### Other steps in Design Flow

1) Simulation for Verification:
   - At various levels: logic level, switch level, circuit level
2) Formal Verification:
   - Used to verify the designs through formal techniques
3) Testability analysis and Test Pattern Generation
   - Required for testing the manufactured devices
  
## 📝 1.6: Design Representation

- A design can be represented at various levels from three different points of view.
  1) Behavioral - Programs, Specifications, Truth Table
  2) Structural - Gates, Adders, Registers
  3) Physical - Transistors/Layouts, Cells, Chips/Boards
- Can be conveniently expressed by Y Diagram

<div align="center">
  <img src="https://github.com/user-attachments/assets/9edac829-2c7f-4bb5-968a-801c5ba6ae82" width="200">
</div>

1) Behavioral Representation:
   - Specifies how a particular design should respond to a given set of inputs
   - May be specified by:
     - Boolean Equations
     - Tables of input and output values
     - Algorithms written in standard HLL like C
     - Algorithms written in special HDL like Verilog or VHDL
   - Example: Full Adder
     - Two operand inputs A and B
     - A carry input C
     - A carry output Cy
     - A sum output S

<div align="center">
  <img src="https://github.com/user-attachments/assets/cfcf9f61-be41-4a5a-8c64-35e24df08ffe" width="100">
</div>
Boolean Expression:

     S = AB′C′ + A′B′C + A′BC′ + ABC = A ⨁ B ⨁ C
     Cy = AB + AC + BC

2) Structural Representation
   * Specifies how components are interconnected
   * In general, the description is a list of modules and their interconnections is called netlist. It can be specified at various levels.
   * At the structural level, the levels of abstraction are: Functional level, Gate level, Transistor level, Any combination of these.
   * In each successive level more detail is revealed about the implementation.
   * Example: A 4-bit Ripple Carry Adder
     - Consist of four full adders
     - Each full adder consists of a sum circuit and a carry circuit.
     - We instantiate carry and sum circuit to create a full adder. Then we instantiate four full adders to create the 4-bit adder.

<div align="center">
  <img src="https://github.com/user-attachments/assets/ebf7f57b-27ac-46b2-8906-e2be896a8c54" width="300">
</div>
     
3) Physical Representation
   * Lowest level of physical specification
   * Photo mask information required by various processing steps in fabrication process
   * At module level, the physical layout for 4 bit adder may be defined by a rectangle/polygon, and collection of ports
   * At layout level, there can be large no. of rectangles or polygons.

## 📝 1.7: Digital IC Design Flow

<div align="center">
  <img src="https://github.com/user-attachments/assets/664eeddc-4396-4fd2-8307-5ea5803cd263" width="400">
</div>

---





  
  
