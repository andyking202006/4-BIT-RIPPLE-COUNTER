Exp: 12( should complete on or before 19.05.25)

module ripple_counter_4bit (
    input clk,         // Clock input
    input reset,       // Asynchronous reset
    output [3:0] q     // 4-bit counter output
);

    wire clk1, clk2, clk3;

    // First flip-flop toggles with main clock
    T_FF tff0 (.clk(clk), .reset(reset), .q(q[0]));

    // Subsequent flip-flops toggle with output of previous FF
    T_FF tff1 (.clk(q[0]), .reset(reset), .q(q[1]));
    T_FF tff2 (.clk(q[1]), .reset(reset), .q(q[2]));
    T_FF tff3 (.clk(q[2]), .reset(reset), .q(q[3]));

endmodule

// T Flip-Flop module
module T_FF (
    input clk,
    input reset,
    output reg q
);
    always @(posedge clk or posedge reset)
    begin
        if (reset)
            q <= 0;
        else
            q <= ~q;
    end
endmodule
