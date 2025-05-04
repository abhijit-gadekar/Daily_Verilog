# 📘 Chapter 3: Basics of Verilog
---

## 📝 3.1: Design Methodologies in Verilog

- Two basic types:
  1. Top-down methodology:
     - Here, we define the top-level block and identify the sub-blocks necessary to build the top-level block.
     - We further subdivide the sub-blocks until we come to leaf cells, which are the cells that cannot further be divided.
     - The Top-down approach is also termed as breaking a bigger problem into smaller problems
     - The focus is on breaking the bigger problem into smaller one and then repeat the process with each problem.
     - Top-Down Model is followed by structural programming languages like C, FORTRAN etc.
     - Also called Decomposition approach
       
<div align="center">
  <img src="https://github.com/user-attachments/assets/d71fa8d2-ee2f-4b6b-8f42-6b7d61a56c12" width="500">
</div>

  2. Bottom-Up methodology:
     - The bottom-up model is one in which the different parts of a system are designed and developed and then all these parts are connected together as a single unit.
     - The advantage of Bottom-Up Model is in making decisions at very low level and deciding the re-usability of components.
     - In Bottom-Up Model, the focus is on identifying and resolving smallest problems and then integrating them together to solve the bigger problem.
     - Bottom-Up Model is mainly used by object oriented programming languages like Java, C++ etc.
     - Also called Composition approach
       
<div align="center">
  <img src="https://github.com/user-attachments/assets/c7dba5d2-b4e7-4594-b96f-bed17d4d4cbe" width="500">
</div>

## 📝 3.2: Modules

- A module is the basic building block in Verilog.
- A module can be an element or a collection of lower-level design blocks.
- A module provides the necessary functionality to the higher-level block through its port interface (inputs and outputs), but hides the internal implementation.
- It allows the designer to modify module internals without affecting the rest of the design.

- Properties:
  1. A module cannot contain definition of other modules. (Module definitions cannot be nested.)
  2. A module can be instantiated within another module.
  3. Instantiation allows creation of heirarchy in Verilog description.
  4. Everything you write in Verilog must be inside a module, expect: compiler directives.
  5. The module behaves identically with the external environment irrespective of the level of abstraction at which the module is described.
  6. The internals of the module are hidden from the environment. Thus, the level of abstraction to describe a module can be changed without any change in the environment. 

- Module Declaration in Verilog:
  - A module is enclosed between module and endmodule keywords.
  - Any additional specifications can be inserted into the code using `include compiler directive.
  - Each module must have a module_name, which is the identifier for the module, and a module_terminal_list/list of ports, which describes the input and output terminals of the module. 

        module module_name (terminal list/list_of_ports) ; 
        ...
          module internals 
        ... 
        ... 
        endmodule 

- E.g. of a 2-input AND gate Module

      module and_gate (
          input a,
          input b,
          output y
      );
          assign y = a & b;
      endmodule
    
- Here,
  - module and_gate starts the module definition with the name and_gate
  - input a, b declares the input ports.
  - output y declares the output port.
  - assign y = a & b; implements the AND logic.
  - endmodule ends the module.

## 📝 3.3: Levels of Abstraction in Module

-  Internals of each module can be defined at four levels of abstraction, depending on the needs of the design.
-  The levels are defined below.
  1. Behavioral or algorithmic level
     - This is the highest level of abstraction provided by Verilog HDL.
     - A module can be implemented in terms of the desired design algorithm without concern for the hardware implementation details.
     - Designing at this level is very similar to C programming.
  2. Dataflow level
     - At this level the module is designed by specifying the data flow. The designer is aware of how data flows between hardware registers and how the data is processed in the design.
  3. Gate level
     - The module is implemented in terms of logic gates and interconnections between these gates. Design at this level is similar to describing a design in terms of a gate-level logic diagram.
  4. Switch level
     - This is the lowest level of abstraction provided by Verilog. A module can be implemented in terms of switches, storage nodes, and the interconnections between them.
     - Design at this level requires knowledge of switch-level implementation details. 

- Verilog allows the designer to mix and match all four levels of abstractions in a design.
- In the digital design community, the term register transfer level (RTL) is frequently used for a Verilog description that uses a combination of behavioral and dataflow constructs and is acceptable to logic synthesis tools.
- Normally, the higher the level of abstraction, the more flexible and technology independent the design.
- As one goes lower toward switch-level design, the design becomes technology dependent and inflexible. A small modification can cause a significant number of changes in the design.

## 📝 3.4: Module Instantiation

- A module provides a template from which you can create actual objects. When a module is invoked, Verilog creates a unique object from the template.
- Each object has its own name, variables, parameters and 1/0 interface. The process of creating objects from a module template is called instantiation, and the objects are called instances.
- Module definitions simply specify how the module will work, its internals, and its interface. Modules must be instantiated for use in the design.
- E.g.:  We'll define a module called and_gate that performs a logical AND operation on two inputs.
---
    module and_gate (
      input a,
      input b,
      output y
    );
      assign y = a & b;
    endmodule

- Now we'll create another module called top_module and instantiate the and_gate inside it.

      module top_module;
          // Declare wires to connect to the and_gate
          wire x, z, result;

        // Assign values to inputs for simulation purposes
        assign x = 1'b1;
        assign z = 1'b0;

        // Instantiate the and_gate
        and_gate in_and (
          .a(x),
          .b(z),
          .y(result)
        );
      endmodule
    
- Illegal Module Nesting in Verilog

      module top_module;
          // some code here.............
          // 🚫 This is illegal!
          module and_gate (
              input a,
              input b,
              output y
          );
              assign y = a & b;
          endmodule
      endmodule
