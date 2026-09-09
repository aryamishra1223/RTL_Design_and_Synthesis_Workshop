# Introduction to Verilog

This includes basics of Verilog, how simulation works, and get introduced to logic synthesis.
---

## Table of Contents

1. [What is a Simulator, Design, and Testbench?](#1-what-is-a-simulator-design-and-testbench)
2. [Getting Started with iverilog](#2-getting-started-with-iverilog)
3. [Lab: Simulating a 2-to-1 Multiplexer](#3-lab-simulating-a-2-to-1-multiplexer)
4. [Verilog Code Analysis](#4-verilog-code-analysis)
5. [Summary](#5-summary)

---

## 1. What is a Simulator, Design, and Testbench?

### Simulator
It serves the purpose of checking digital circuits' functionality by applying inputs and viewing outputs.

### Design
The design in verilog code is description of intended logic functionality.

### Testbench
A simulation eenvironment that applies various inputs to intended design and checks correctness of output.

---

## 2. Getting Started with iverilog

iverilog is an open-source simulator for Verilog.
NOTE: Simulator produces a .vcd file for waveform viewing in GTKWave (here, vcd means value code dumpfile).

---

## 3. Lab: Simulating a 2-to-1 Multiplexer

### Step 1: Clone the Workshop Respository

git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git

cd sky130RTLDesignAndSynthesisWorkshop/verilog_files

### Step 2: Install Required Tools

---sudo apt install iverilog
sudo apt install gtkwave

### Step 3: Simulate the Design
 Compile the design and testbench:

iverilog good_mux.v tb_good_mux.v

Run the simulation:
./a.out

View the waveform:
gtkwave tb_good_mux.vcd

<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/4bd3a176-b275-4138-931a-73ee02a44523" />

## 4. Verilog Code Analysis
 ### Code for multiplexer(good_mux.v):

 module good_mux (
    input  i0,
    input  i1,
    input  sel,
    output reg y
);

    always @ (*)
    begin
        if (sel)
            y <= i1;
        else
            y <= i0;
    end

endmodule

## 5. Introduction to Yosys & Gate Libraries

### Yosys
1. A open-source synthesis tool for digital hardware.
2. Converts it into a gate-level netlist - a hardware blueprint.

   --
#### Features
Synthesis
Optimization
Technology Mapping
Verification
Extensibility

### Need for Different Gate "Flavours"
"Flavours", here, refers to the many versions of each and every gate in a .lib file. It includes AND, OR, NOT gates. These gates may have 2 input terminals or 3 input terminals depending upon the type of gate chosen.

This includes properties, such as, :

Performance
Power
Area
Drive Strength
Signal Integrity

## 6. Yosys Synthesis Lab
Steps for Yosys flow

 1. Start Yosys
    yosys
 2. Read liberty library
    read_liberty -lib /address/to/your/sky130/file/sky130_fd_sc_hd__tt_025C_1v80.lib
 3. Read verilog code
    read_verilog /home/vsduser/VLSI/sky130RTLDesignAndSynthesisWorkshop/verilog_files/good_mux.v
 4. Synthesize
    synth -top good_mux
 5. Technology Mapping
    abc -liberty /address/to/your/sky130/file/sky130_fd_sc_hd__tt_025C_1v80.lib
 6. Visualize the gate-level netlist
    show


## 7. Summary

1. Learned simulators, designs, and testbenches.
2. Performed iverilog simulation and visualized waveforms.
3. Analysed 2:1 mux.
4. Explored yosys.
5. Understood need for various flavors in gate liberaries.
    

