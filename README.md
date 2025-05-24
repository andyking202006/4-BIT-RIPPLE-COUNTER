# 4-BIT-RIPPLE-COUNTER

**AIM:**

To implement  4 Bit Ripple Counter using verilog and validating their functionality using their functional tables

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**

**4 Bit Ripple Counter**

A binary ripple counter consists of a series connection of complementing flip-flops (T or JK type), with the output of each flip-flop connected to the Clock Pulse input of the next higher-order flip-flop. The flip-flop holding the least significant bit receives the incoming count pulses. The diagram of a 4-bit binary ripple counter is shown in Fig. below.

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/cb4b74d4-31ab-4359-95d0-d22e67daba13)

In timing diagram Q0 is changing as soon as the negative edge of clock pulse is encountered, Q1 is changing when negative edge of Q0 is encountered(because Q0 is like clock pulse for second flip flop) and so on.

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/a573a7d6-014e-4e54-93e6-e2ac9530960b)

![image](https://github.com/naavaneetha/4-BIT-RIPPLE-COUNTER/assets/154305477/85e1958a-2fc1-49bb-9a9f-d58ccbf3663c)

**Procedure**

Type the program in Quartus software.

Compile and run the program.

Generate the RTL schematic and save the logic diagram.

Create nodes for inputs and outputs to generate the timing diagram.

For different input combinations generate the timing diagram.

**PROGRAM**
```
// 4-bit Ripple Carry Adder Module
module assexp12 (
    input [3:0] A, B,      // 4-bit Inputs: A and B
    input Cin,             // Carry-in
    output [3:0] Sum,      // 4-bit Sum output
    output Cout            // Carry-out
);

    wire C1, C2, C3;       // Internal carry wires

    // Instantiate 4 full adders
    full_adder FA0 (A[0], B[0], Cin, Sum[0], C1);  // Least significant bit (LSB)
    full_adder FA1 (A[1], B[1], C1, Sum[1], C2);
    full_adder FA2 (A[2], B[2], C2, Sum[2], C3);
    full_adder FA3 (A[3], B[3], C3, Sum[3], Cout); // Most significant bit (MSB)

endmodule 

// Full Adder Module
module full_adder (
    input A, B, Cin,       // Inputs: A, B, and Carry-in
    output Sum, Cout       // Outputs: Sum and Carry-out
);

    assign Sum = A ^ B ^ Cin;            // Sum = A ⊕ B ⊕ Cin
    assign Cout = (A & B) | (Cin & (A ^ B)); // Cout = (A ⋅ B) + (Cin ⋅ (A ⊕ B))

endmodule
```

 Developed by:Aswinth Balaji DS
 
 RegisterNumber:212224050003

**RTL LOGIC FOR 4 Bit Ripple Counter**

![assexp12](https://github.com/user-attachments/assets/2a2f24c6-caae-4dcb-83f3-56b6ea67a93b)

**TIMING DIGRAMS FOR 4 Bit Ripple Counter**

![Screenshot 2024-12-10 114947](https://github.com/user-attachments/assets/4424dd1b-8614-47d2-b9d0-8c613e9f5f7c)

**RESULTS**

Thus 4 Bit Ripple Counter using verilog and validating their functionality using their functional tables are verified successfully.
