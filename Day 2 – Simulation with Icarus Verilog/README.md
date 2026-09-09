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
<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/36ec3a2e-836b-4ddc-9685-0c69e7dfb0ec" />

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
endmodule```



### Asynchronous Set D Flip-Flop
```verilog
module dff_async_set (
    input clk,
    input async_set,
    input d,
    output reg q
);
    always @ (posedge clk, posedge async_set)
    begin
        if (async_set)
            q <= 1'b1;
        else
            q <= d;
    end
endmodule


### Synchronous Reset D Flip-flop
```verilog
module dff_syncres (
    input clk,
    input async_reset,
    input sync_reset,
    input d,
    output reg q
);
    always @ (posedge clk)
    begin
        if (sync_reset)
            q <= 1'b0;
        else
            q <= d;
    end
endmodule
```


## Simulation and Synthesis Workflow

### Icarus Verilog Simulation

1. Compile:
   ```bash
   iverilog dff_asyncres.v tb_dff_asyncres.v
2. run
```bash
./a.out

3.View waveform
gtkwave tb_dff_asyncres.vcd

end
endmodule
  ```

<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/a683064d-9bbb-48ab-9e09-0b85a3fdf53f" />

### Synthesis with yosys

code:

yosys
read_liberty -lib /address/to/your/sky130/file/sky130_fd_sc_hd__tt_025C_1v80.lib
read_verilog /path/to/dff_asyncres.v
synth -top dff_asyncres
dfflibmap -liberty /address/to/your/sky130/file/sky130_fd_sc_hd__tt_025C_1v80.lib
abc -liberty /address/to/your/sky130/file/sky130_fd_sc_hd__tt_025C_1v80.lib
show

<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/f45fb29b-c040-4fa3-bf93-a11da9a0ac3b" />
