_**This lab instruction set is the property of Oregon State University, I claim no credit to these instructions aside from manually formatting it to appear well on .md files, only to my solution to the lab.**_

# ECE 272 Section 5: System Verilog
### 5.1 Background Information
As digital logic designs get complex, it becomes cumbersome to describe logic with schematics. Simplifying logic by hand can take a long time and is prone to human error. Hardware Description Languages describe digital hardware. As time went on and systems like FPGAs were created, Hardware Description Languages began to be used to directly describe the hardware to be implemented.

 

Computers can synthesize and simplify a design much faster than a human can. A language like Verilog (Or its newer standard, SystemVerilog) can be used to describe very complicated logic, and force a computer to synthesize the logic. This opens the door to bad design processes, such as people implementing hardware they do not understand. Do not forget the previous labs, hardware is still being described, just at a more abstract level. Keep the modules in your design simple, and then connect modules together in a way to create a more complex system.

 

### 5.2 Section Overview
Objective: Design and Implement a clock using SystemVerilog

The following modules from the textbook:

    Counter - Example 5.5

    Comparator - Example 5.3

    Synchronizer - Example 4.20

    Display Driver - Example 4.24

And a parser module will be used to create a clock. The clock should have seconds, minutes, and hours displayed on the 7-segment displays.  

### 5.3 Learning Objectives
 The objective of this lab is to understand Hardware Description Languages(HDL) / SystemVerilog (SV) 

### 5.4 Materials
1. Quartus Prime Lite Edition V. 18.0
2. DE10-Lite kit with MAX10 10M50DAF484C7G FPGA 
3. USB to USB-B cable
4. The ECE 271 textbook, Digital Design and Computer Architecture by Drs. David and Sarah Harris CH. 4 & 5
### 5.5 Procedure:
#### <div align="center">There are 6 steps to digital logic design</div>
![Design Process Flow](https://github.com/regerj/ECE-272-Lab-4/blob/master/4.1%20Design%20Process.png)
#### <div align="center">Design Process Figure 5.2: Use this process for designing the final project.</div>

1. Design: The context of the design is established in this step. The context involves defining the inputs, desired outputs, and all the logic required in-between. In this step, all the minimizations and layout are planned for the design entry process. While this step is not always the longest, it should involve the most thought and effort. This typically requires a complete block diagram showing all the logic blocks and the connections between them, often with written explanations of specific functions. 
2. Design Entry: The actual drafting of the digital logic design occurs in this step, translating the design from block diagrams and descriptions into the software. This can be accomplished directly by writing HDL code, or graphically by drawing a schematic that a software tool can convert into HDL code. 
3. Design Simulation: Before committing to hardware, this step tests the design in a controlled computer simulation. If the design does not function as specified in the ”Design” step, it is revised. 
4. Synthesize and Map Design: When the design simulates correctly, the HDL and schematic source files are synthesized into a design file that can be written to the FPGA. This includes assigning the inputs and outputs of the design to IO pins. 
5. Program Hardware: After the design file is created, it is used to configure the FPGA. Quartus Prime sends a bit stream over the USB-B cable to configure the DE10-Lite FPGA. 
6. Test Hardware: Verify hardware operation once the FPGA has been programmed. The FPGA should operate exactly as the design predicted, which was verified by the simulation. Synthesis problems, timing violations, or incorrect assumptions about the hardware can require the designer to return to the ”Design” step.
### 5.6 Design
Start by creating a software level block diagram. This step is critical. Typically Digital logic design done with a HDL is not simple, and starting with an idea of how information should ‘flow’ through the system is a good way to avoid bad design.

A partial schematic for this section is in the pre-lab. This will need to be edited to have correct values in the counter and comparator. Use the pre-lab as inspiration for your block diagram.

A good software level block diagram will have system inputs, outputs, and interconnecting logic labeled with a name and bus size. Each module and its ports will also be named.

 

The only parts the students have to create from scratch are the parser and the Top Level Design file.  

 

This parser is a module that takes a large number, and splits it up into individual digits. If this operation is done on the Maximum 10-bit number, 1023, would create 4 (one for each digit) 4-bit (0-15) outputs. The outputs would be 0001, 0000, 0010, and 0011. These four digit numbers will be fed to the 7-seg decoders.  

Create combinational logic for the parser by using math operators (In section 4 of textbook).

Edit the counter parameters to keep accurate time. Edit the comparator values to trigger reset at 60.  

 

The top level design file is very easy to make if you made a good block diagram. See the last two pages of the System Verilog Starter document for information on instantiating modules in the top level. You can think of instantiating a module a little like calling a function.

### 5.7 Design Entry.
ECE 272 is not a SystemVerilog Class, we just use it for defining a few blocks of combinational and sequential logic based on examples from the textbook.  Section 4 of the textbook, the SV starter documents, and ECE 271 lectures are great resources to learn some fundamental concepts about SystemVerilog.

 

When you create files to enter the design in, create SystemVerilog HDL files.

 

Transcribe your block diagrams and logic into SystemVerilog.

Connect all the modules together in the top level.

### 5.8 Design Simulation
It is required that you use ModleSim to simulate your design. No file conversion is needed, you created your files simulation ready! 

### 5.9 Map Design
Synthesize your design and assign pins to your inputs and outputs using the same process as in Section 1.8.

### 5.10 Program Hardware
Program the Max10 using the same process as in Section 1.9.

### 5.11 Test Hardware
Program the device and see if it keeps time. Refer to Simulation if it does not. 

### 5.12 Checkoff
* Valid hardware output

* Valid SV instancation of textbook modules

* Valid Simulation
