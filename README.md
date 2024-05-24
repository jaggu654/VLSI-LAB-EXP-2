EXP-2

Date:

                  SIMULATION AND IMPLEMENTATION OF COMBINATIONAL LOGIC CIRCUITS

AIM:
 To simulate and synthesis ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, MAGNITUDE COMPARATOR using VIVADO 2023.2

APPARATUS REQUIRED: 

VIVADO 2023.2

PROCEDURE:

STEP:1 Launch the Vivado 2023.2 software.

STEP:2 Click on “create project ” from the starting page of vivado.

STEP:3 Choose the design entry method:RTL(verilog/VHDL).

STEP:4 Crete design source and give name to it and click finish.

STEP:5 Write the verilog code and check the syntax.

STEP:6 Click “run simulation” in the navigator window and click “Run behavioral simulation”.

STEP:7 Verify the output in the simulation window.

LOGIC DIAGRAM

ENCODER

![332091231-4c6ced98-23b7-4280-abfb-8687124c5219](https://github.com/jaggu654/VLSI-LAB-EXP-2/assets/167850134/fd11e7a0-bca6-4be1-86a1-56d39461df54)


verilog code
```
module encoder(a,y);
input [7:0]a;
output[2:0]y;
or(y[2],a[6],a[5],a[4],a[3]);
or(y[1],a[6],a[5],a[2],a[1]);
or(y[0],a[6],a[4],a[2],a[0]);
endmodule
```
output

![332091184-d4ae55b1-ef3f-47c2-aa5f-6a0711158dc4](https://github.com/jaggu654/VLSI-LAB-EXP-2/assets/167850134/1b1414a9-2bcb-45a9-b4f0-258421f56df5)

LOGIC DIAGRAM DECODER

![332091144-e2f81b2b-b4e6-4888-ad05-353a846985d9](https://github.com/jaggu654/VLSI-LAB-EXP-2/assets/167850134/cd9836e3-931c-409f-b24d-0d365f389594)

verilog code
```
module decoder1(a,y);
input [2:0]a;
output[7:0]y;
and(y[0],~a[2],~a[1],~a[0]);
and(y[1],~a[2],~a[1],a[0]);
and(y[2],~a[2],a[1],~a[0]);
and(y[3],~a[2],a[1],a[0]);
and(y[4],a[2],~a[1],~a[0]);
and(y[5],a[2],~a[1],a[0]);
and(y[6],a[2],a[1],~a[0]);
and(y[7],a[2],a[1],a[0]);
endmodule
```
output

![332091104-db92d907-a04b-4ff0-8d03-4bfcd5ec19bc](https://github.com/jaggu654/VLSI-LAB-EXP-2/assets/167850134/f4d458b3-22b6-432e-b8d4-ef3cfab3e35b)


LOGIC DIAGRAM MULTIPLEXER

![332091085-c9512139-7bb6-4dca-bfaa-d28323044278](https://github.com/jaggu654/VLSI-LAB-EXP-2/assets/167850134/df634d2e-05b9-4f7f-bfe5-0150ca216080)

VERILOG CODE
```
module mux(s,c,a);
input [2:0]s;
input [7:0]a;
wire [7:0]w;
output c;
and(w[0],a[0],~s[2],~s[1],~s[0]);
and(w[1],a[1],~s[2],~s[1],s[0]);
and(w[2],a[2],~s[2],s[1],~s[0]);
and(w[3],a[3],~s[2],s[1],s[0]);
and(w[4],a[4],s[2],~s[1],~s[0]);
and(w[5],a[5],s[2],~s[1],s[0]);
and(w[6],a[6],s[2],s[1],~s[0]);
and(w[7],a[7],s[2],s[1],s[0]);
or (c,w[0],w[1],w[2],w[3],w[4],w[5],w[6],w[7]);
endmodule
```
output
![332091021-804c467d-0dc8-4115-90ce-32f8b7d65df5](https://github.com/jaggu654/VLSI-LAB-EXP-2/assets/167850134/ed68545d-89f0-4e28-bae0-307378af3733)


VERILOG CODE DEMULTIPLEXER

![332090983-d3602d4d-d42e-402a-96e5-5a24b6e160a2](https://github.com/jaggu654/VLSI-LAB-EXP-2/assets/167850134/d41b8dee-98d2-4ed4-a7d8-1bb206339042)

VERILOG CODE
```
module demux_8(s,a,y);
input [2:0]s;
input a;
output [7:0]y;
and(y[0],a,~s[2],~s[1],~s[0]);
and(y[1],a,~s[2],~s[1],s[0]);
and(y[2],a,~s[2],s[1],~s[0]);
and(y[3],a,~s[2],s[1],s[0]);
and(y[4],a,s[2],~s[1],~s[0]);
and(y[5],a,s[2],~s[1],s[0]);
and(y[6],a,s[2],s[1],~s[0]);
and(y[7],a,s[2],s[1],s[0]);
endmodule
```

output

![332090895-43ecf731-a33e-4fd7-a3fa-2b45d98d8c04](https://github.com/jaggu654/VLSI-LAB-EXP-2/assets/167850134/b3e77dbe-75d1-4946-a66e-058dbecd2653)

MAGNITUDE COMPARATOR

![332090881-351260d9-4ecf-411d-adcb-9d55f7209a46](https://github.com/jaggu654/VLSI-LAB-EXP-2/assets/167850134/98d05bf4-7775-4574-8112-86f10b0abec9)

VERILOG CODE
```
module comparator(a,b,eq,lt,gt);
input [3:0] a,b;
output reg eq,lt,gt;
always @(a,b)
begin
 if (a==b)
 begin
  eq = 1'b1;
  lt = 1'b0;
  gt = 1'b0;
 end
 else if (a>b)
 begin
  eq = 1'b0;
  lt = 1'b0;
  gt = 1'b1;
 end
 else
 begin
  eq = 1'b0;
  lt = 1'b1;
  gt = 1'b0;
 end
end 
endmodule
```
OUTPUT

![332090849-e0ea6b5a-d060-4e01-998d-e53938f6de93](https://github.com/jaggu654/VLSI-LAB-EXP-2/assets/167850134/0284b4a0-0ec0-4bb3-86f1-2ab89597d511)

RESULT

Thus the simulation and synthesis of ENCODER, DECODER, MULTIPLEXER, DEMULTIPLEXER, 2bit MAGNITUDE COMPARATOR using vivado is successfully completed and executed.



