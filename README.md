# EC1801-DLC-EXP1
### EXPERIMENT 1 
### MINIMIZATION AND IMPLEMENTATION OF BOOLEAN FUNCTION
## Aim
To minimize and implement a Boolean function using logic gates and verify the functionality using Synopsys VCS and DVE.
## Software Required
•	Synopsys VCS
•	Synopsys DVE
•	Linux Terminal
•	Verilog HDL
## Boolean Function
Consider the Boolean function:
F(A,B,C,D)=Σm(0,2,5,7,8,10,13,15)
The minimized Boolean expression is: F=B'D'+BD
The function is implemented using Verilog HDL.
## Files Used
File	Description
exp1_boolean_min.v	Verilog design file
exp1_boolean_min_tb.v	Verilog testbench
exp1_boolean_min.vcd	VCD waveform dump generated during simulation

## Verilog Program
```
module boolfun (
input wire A, 
input wire B, 
input wire C, 
input wire D, 
output wire F 
); 
assign F = (~B & ~D)|(B & D) ;    // F = B'D' + BD 
endmodule
```


## TestBench Program
```
module boolfun_tb;

reg A, B, C, D;
wire F;

boolfun uut (
    .A(A),
    .B(B),
    .C(C),
    .D(D),
    .F(F)
);

initial begin

    $dumpfile("boolfun.vcd");
    $dumpvars(0, boolfun_tb);

    $monitor("Time=%0t A=%b B=%b C=%b D=%b F=%b",
              $time, A, B, C, D, F);

    A=0; B=0; C=0; D=0; #10;
    A=0; B=0; C=0; D=1; #10;
    A=0; B=0; C=1; D=0; #10;
    A=0; B=0; C=1; D=1; #10;

    A=0; B=1; C=0; D=0; #10;
    A=0; B=1; C=0; D=1; #10;
    A=0; B=1; C=1; D=0; #10;
    A=0; B=1; C=1; D=1; #10;

    A=1; B=0; C=0; D=0; #10;
    A=1; B=0; C=0; D=1; #10;
    A=1; B=0; C=1; D=0; #10;
    A=1; B=0; C=1; D=1; #10;

    A=1; B=1; C=0; D=0; #10;
    A=1; B=1; C=0; D=1; #10;
    A=1; B=1; C=1; D=0; #10;
    A=1; B=1; C=1; D=1; #10;

    $finish;
end

endmodule
```






    
## Truth Table
 
<img width="795" height="311" alt="image" src="https://github.com/user-attachments/assets/dd4ba5b9-016b-4ae5-a693-f309c60c4c0e" />

## Simulation Procedure
STEP 1 – Open Terminal
Open a terminal in the experiment folder.
bash

STEP 2 – Load Synopsys Environment
source /synopsys/start.sh

STEP 3 – Compile Using VCS
vcs exp1_boolean_min.v exp1_boolean_min_tb.v -full64
 
If compilation is successful, VCS generates the simulation executable:
simv

STEP 4 – Run Simulation
./simv
The terminal displays the input combinations and corresponding output F.
A VCD waveform file is also generated:
exp1_boolean_min.vcd

STEP 5 – Open DVE
dve -full64
Other option
dve -full64 &
A DVE environment will open.

## DVE Waveform Verification
In DVE:
1.	Open the testbench hierarchy.
2.	Locate the signals:
o	A
o	B
o	C
o	D
o	F
3.	Add the signals to the waveform window.
4.	Run/inspect the waveform.
5.	Verify that F = 1 whenever B and D are equal.
6.	Verify that F = 0 whenever B and D are different.
The waveform should agree with the truth table.
 
### Expected Result
<img width="1600" height="790" alt="image" src="https://github.com/user-attachments/assets/0194336d-0d66-428b-8e68-3af6def6ffb5" />

## OUTPUT
<img width="1899" height="988" alt="Screenshot 2026-10-24 130014" src="https://github.com/user-attachments/assets/394ed6ba-fb3a-4d4e-94ac-177d54d6f74f" />




Result
Thus, the Boolean function was minimized, implemented using Verilog HDL, successfully simulated using Synopsys VCS, and verified using Synopsys DVE.

