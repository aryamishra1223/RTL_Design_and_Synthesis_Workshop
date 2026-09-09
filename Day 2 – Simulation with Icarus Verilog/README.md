# Day 2: Timing Libraries, Synthesis Approaches, and Flip-Flop Coding

Welcome to Day 2! This includes:

- Understanding .lib timing libraries used in open-source PDKs
- Comparing hierarchical vs. flat synthesis
- Coding styles for flip-flops in RTL design

---

## Table of Contents

- [Timing Libraries](#timing-libraries)
- [Hierarchical vs. Flattened Synthesis](#hierarchical-vs-flattened-synthesis)
- [Flip-Flop Coding Styles](#flip-flop-coding-styles)
- [Simulation and Synthesis Workflow](#simulation-and-synthesis-workflow)

---

## Timing Libraries

### SKY130 PDK Overview
- It is based on SkyWater Technology's 130nm CMOS technology. 
- PDK stands for Process Design Kit.
- Provides essential models and libraries for IC design.


### Decoding tt_025C_1v80
- *tt*: Typical process corner
- *025C*: 25°C operating temperature
- *1v80*: 1.8V core voltage
---
## Opening and Exploring the .lib File
1. Install a text editor:
   sudo apt install gedit
   
2. Open the file:
   gedit sky130_fd_sc_hd__tt_025C_1v80.lib

## Hierarchical vs. Flattened Synthesis

### Hierarchical Synthesis
Retains modular structure of your original verilog code throughout the complete synthesis process.
It functions by maintaining internal module boundaries called grouping.

### Flattened Synthesis
Removes internal module boundaries called ungrouping.
Merges all logic into a single, massive top-level layer.

### Key Differences
| Aspect | Hierarchical | Flattened |
|---|---|---|
| Module boundaries | Preserved | Removed |
| Debug ease | Easier | Harder |
| Optimization | Limited across modules | Global |

---

## Flip-Flop Coding Styles

### Asynchronous Reset D Flip-Flop
```verilog
module dff_async_reset (
    input clk,
    input async_reset,
    input d,
    output reg q
);
    always @ (posedge clk or posedge async_reset)
    begin
        if (async_reset)
            q <= 1'b0;
        else
            q <= d;
    end
endmodule
