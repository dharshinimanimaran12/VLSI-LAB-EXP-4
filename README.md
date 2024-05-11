# VLSI-LAB-EXP-4
SIMULATION AND IMPLEMENTATION OF SEQUENTIAL LOGIC CIRCUITS

## AIM: 
 To simulate and synthesis SR, JK, T, D - FLIPFLOP, COUNTER DESIGN using Xilinx ISE.

## APPARATUS REQUIRED:

Xilinx 14.7
Spartan6 FPGA

## PROCEDURE:
STEP:1  Start  the Xilinx navigator, Select and Name the New project.
STEP:2  Select the device family, device, package and speed.       
STEP:3  Select new source in the New Project and select Verilog Module as the Source type.                       
STEP:4  Type the File Name and Click Next and then finish button. Type the code and save it.
STEP:5  Select the Behavioral Simulation in the Source Window and click the check syntax.                       
STEP:6  Click the simulation to simulate the program and  give the inputs and verify the outputs as per the truth table.               
STEP:7  Select the Implementation in the Sources Window and select the required file in the Processes Window.
STEP:8  Select Check Syntax from the Synthesize  XST Process. Double Click in the  FloorplanArea/IO/Logic-Post Synthesis process in the User Constraints process group. UCF(User constraint File) is obtained. 
STEP:9  In the Design Object List Window, enter the pin location for each pin in the Loc column Select save from the File menu.
STEP:10 Double click on the Implement Design and double click on the Generate Programming File to create a bitstream of the design.(.v) file is converted into .bit file here.
STEP:11  On the board, by giving required input, the LEDs starts to glow light, indicating the output.


## SR FLIPFLOP
### Logic Diagram:
![image](https://github.com/dharshinimanimaran12/VLSI-LAB-EXP-4/assets/167978093/413e8e9c-1a6a-4804-aa97-50ed7c6d74b1)
### Verilog Code:
```
module srff(s,r,clk,rst,q);
input s,r,clk,rst;
output reg q;
always@(posedge clk)
begin
if(rst==1)
q=0;
else
begin
case({s,r})
2'b00:q=q;
2'b01:q=0;
2'b10:q=1;
2'b11:q=1'bX;
endcase
end
end
endmodule
```
### Output:
![image](https://github.com/dharshinimanimaran12/VLSI-LAB-EXP-4/assets/167978093/5b712fd3-bb71-4771-91ca-24ce12a0d893)

## JK FLIPFLOP
### Logic Diagram:
![image](https://github.com/dharshinimanimaran12/VLSI-LAB-EXP-4/assets/167978093/eaafbd49-290e-4102-b87d-98cd0046943d)
### Verilog Code:
```
module jkff(j,k,clk,rst,q);
input j,k,clk,rst;
output reg q;
always@(posedge clk)
begin
if(rst==1)
q=0;
else
begin
case({j,k})
2'b00:q=q;
2'b01:q=0;
2'b10:q=1;
2'b11:q=~q;
endcase
end
end
endmodule
```
### Output:
![image](https://github.com/dharshinimanimaran12/VLSI-LAB-EXP-4/assets/167978093/a18b34ff-646e-4e74-8407-a7a7476dd372)

## T FLIPFLOP
### Logic Diagram:
![image](https://github.com/dharshinimanimaran12/VLSI-LAB-EXP-4/assets/167978093/bb92c37e-5c58-42ea-91bb-eaa5f096f286)

### Verilog Code:
```
module tff(clk,rst,t,q);
input clk,rst,t;
output reg q;
always @(posedge clk)
begin
if (rst==1)
q=1'b0;
else if (t==0)
q=q;
else
q=~q;
end
endmodule
```
### Output:
![image](https://github.com/Nandhak23/VLSI-LAB-EXP-4-/assets/160568515/1d84bc96-d7b9-44bf-9f1b-b1793188a121)

## D FLIPFLOP
### Logic Diagram:
![image](https://github.com/dharshinimanimaran12/VLSI-LAB-EXP-4/assets/167978093/dd7babc8-0e5c-4acc-9a4c-23eea3021b4b)

### Verilog Code:
```
module dff(d,clk,rst,q);
input d,clk,rst;
output reg q;
always @(posedge clk)
begin
if (rst==1)
q=1'b0;
else
q=d;
end
endmodule
```
### Output:
![image](https://github.com/dharshinimanimaran12/VLSI-LAB-EXP-4/assets/167978093/8dab28eb-dea8-4db9-a3b8-cb60a98c595b)

## COUNTER
### Logic Diagram:
![image](https://github.com/dharshinimanimaran12/VLSI-LAB-EXP-4/assets/167978093/8fb49fce-8471-4f89-9851-b09eac799b5a)
## Updown Counter:
### Logic Diagram:
![image](https://github.com/dharshinimanimaran12/VLSI-LAB-EXP-4/assets/167978093/89d3229e-234c-4b07-81bd-7815df12ae75)

### Verilog Code:
```
module udc(clk,rst,updown,out);
input clk,rst,updown;
output reg [3:0]out;
always@(posedge clk)
begin
if (rst==1)
out=4'b0000;
else if(updown==1)
out=out+1;
else
out=out-1;
end
endmodule
```
### Output:
![image](https://github.com/dharshinimanimaran12/VLSI-LAB-EXP-4/assets/167978093/3150a687-e657-4fa5-a9b5-888dd0bb3d46)

## Mod-10 Counter:
### Logic Diagram:
![image](https://github.com/dharshinimanimaran12/VLSI-LAB-EXP-4/assets/167978093/73dcd739-5278-4ea7-86ec-a250fda7f812)
### Verilog Code:
```
module mod10(clk,rst,out);
input clk,rst;
output reg [3:0]out;
always@(posedge clk)
begin
if (rst==1 | out==4'b1001)
out=4'b0000;
else
out=out+1;
end
endmodule
```
### Output:
![image](https://github.com/dharshinimanimaran12/VLSI-LAB-EXP-4/assets/167978093/b0602693-0820-4557-8aa0-d15c1f413801)

## Ripple Carry Counter:
### Logic Diagram:
![image](https://github.com/dharshinimanimaran12/VLSI-LAB-EXP-4/assets/167978093/05eb0ed5-8bc9-4a09-b47b-60da107263e0)

### Verilog Code:
```
module tff(q,clk,rst);
input clk,rst;
output q;
wire d;
dff df1(q,d,clk,rst);
not n1(d,q);
endmodule

module dff(q,d,clk,rst);
input d,clk,rst;
output q;
reg q;
always @(posedge clk or posedge rst)
begin
if (rst)
q=1'b0;
else 
q=d;
end
endmodule

module rcc(clk,rst,q);
input clk,rst;
output [3:0]q;
tff tf1(q[0],clk,rst);
tff tf2(q[1],q[0],rst);
tff tf3(q[2],q[1],rst);
tff tf4(q[3],q[2],rst);
endmodule
```
### Output:
![image](https://github.com/dharshinimanimaran12/VLSI-LAB-EXP-4/assets/167978093/fb2819d1-cbc5-4f8e-bfd1-9516452e1974)

## RESULT:
Hence SR, JK, T, D - FLIPFLOP, COUNTER DESIGN are simulated and synthesised using Xilinx ISE.


