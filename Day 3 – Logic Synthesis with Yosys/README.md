# Day 3: Combinational and Sequential Optimization

[23:30, 09/09/2026] Mummy: ## Table of Contents

- [1. Constant Propagation](#1-constant-propagation)
- [2. State Optimization](#2-state-optimization)
- [3. Cloning](#3-cloning)
- [4. Retiming](#4-retiming)
- [5. Labs on Optimization](#5-labs-on-optimization)
  - [Lab 1](#lab-1)
  - [Lab 2](#lab-2)
  - [Lab 3](#lab-3)
  - [Lab 4](#lab-4)
  - [Lab 5](#lab-5)
  - [Lab 6](#lab-6)

---

## 1. Constant Propagation

In VLSI design, constant propagation is a compiler optimization technique used to replace variables with their constant values during synthesis. This can simplify design and enhance performance.

*How it works:*
Constant propagation analyzes the design code to identify variables with constant values. These are replaced directly, allowing tools to simplify logic and reduce circuit siz…
[23:32, 09/09/2026] Mummy: ## 2. State Optimization

Refines FSMs for efficiency by reducing states, optimizing encoding, and minimizing logic.

- *State Reduction:* Merge equivalent states
- *State Encoding:* Assign optimal codes
- *Logic Minimization:* Simplify Boolean equations
- *Power Optimization:* Clock gating, etc.

---

## 3. Cloning

Duplicates a logic cell/module to balance load, reduce wire length, and improve timing or power.

- Identify critical paths
- Duplicate target cell/module
- Redistribute connections
- Place and route clone
- Verify via timing/power analysis
[23:35, 09/09/2026] Mummy: ## 4. Retiming

Repositions registers to improve performance without changing functionality.

1. *Graph Representation:* Model circuit as a directed graph
2. *Register Repositioning:* Move registers to balance path delays
3. *Constraints Analysis:* Maintain timing/functional equivalence
4. *Optimization:* Adjust positions to minimize clock period, optimize power

---

## 5. Labs on Optimization

### Lab 1


module opt_check (input a , input b , output y);
	assign y = a?b:0;
endmodule

<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/dbafa0ed-e4cc-4f52-b9fc-b572b3ba236e" />

### Lab 2

module opt_check2 (input a , input b , output y);
	assign y = a?1:b;
endmodule

<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/71995d0e-a511-42b5-bed1-118f2a3fce6a" />

### Lab 3

module opt_check2 (input a , input b , output y);
	assign y = a?1:b;
endmodule

<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/6006429d-9c48-4e49-9f57-66bb89c11a08" />

### Lab 4

module opt_check2 (input a , input b , output y);
	assign y = a?1:b;
endmodule

<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/0f877a3a-85cf-4289-90bb-fb1064c09fa8" />

### Lab 5
 module dff_const1(input clk, input reset, output reg q);
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b0;
	else
		q <= 1'b1;
end
endmodule

<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/b1cc2117-e587-4bb8-86c9-515f39e3fae8" />

### Lab 6

module dff_const2(input clk, input reset, output reg q);
always @(posedge clk, posedge reset)
begin
	if(reset)
		q <= 1'b1;
	else
		q <= 1'b1;
end
endmodule

<img width="1920" height="1080" alt="Image" src="https://github.com/user-attachments/assets/71d8f058-1770-45ba-8508-761fdf72672c" />
