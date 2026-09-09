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

Step 1: Clone the Workshop Respository

git clone https://github.com/kunalg123/sky130RTLDesignAndSynthesisWorkshop.git

cd sky130RTLDesignAndSynthesisWorkshop/verilog_files

Step 2: Install Required Tools

---sudo apt install iverilog
sudo apt install gtkwave

Step 3: Simulate the Design
 Compile the design and testbench:

iverilog good_mux.v tb_good_mux.v

Run the simulation:
./a.out

View the waveform:
gtkwave tb_good_mux.vcd


