### SYNCHRONOUS-UP-COUNTER

**AIM:**

To implement 4 bit synchronous up counter and validate functionality.

**SOFTWARE REQUIRED:**

Quartus prime

**THEORY**

**4 bit synchronous UP Counter**

If we enable each J-K flip-flop to toggle based on whether or not all preceding flip-flop outputs (Q) are “high,” we can obtain the same counting sequence as the asynchronous circuit without the ripple effect, since each flip-flop in this circuit will be clocked at exactly the same time:

![image](https://github.com/naavaneetha/SYNCHRONOUS-UP-COUNTER/assets/154305477/d5db3fa0-e413-404c-b80e-b2f39d82e7e8)


![image](https://github.com/naavaneetha/SYNCHRONOUS-UP-COUNTER/assets/154305477/52cb61eb-d04b-442d-810c-31185a68410b)

Each flip-flop in this circuit will be clocked at exactly the same time.
The result is a four-bit synchronous “up” counter. Each of the higher-order flip-flops are made ready to toggle (both J and K inputs “high”) if the Q outputs of all previous flip-flops are “high.”
Otherwise, the J and K inputs for that flip-flop will both be “low,” placing it into the “latch” mode where it will maintain its present output state at the next clock pulse.
Since the first (LSB) flip-flop needs to toggle at every clock pulse, its J and K inputs are connected to Vcc or Vdd, where they will be “high” all the time.
The next flip-flop need only “recognize” that the first flip-flop’s Q output is high to be made ready to toggle, so no AND gate is needed.
However, the remaining flip-flops should be made ready to toggle only when all lower-order output bits are “high,” thus the need for AND gates.

**Procedure**
1.Declare clock, reset, and counter output (e.g., 4-bit Q).

2.Use an always block triggered on the positive edge of the clock.

3.Inside the always block:

If reset = 1 → Set counter to 0000.

Else → Increment counter by 1 (Q = Q + 1).

4.End the always block.

**PROGRAM**

module Co_ud (
    input  wire clk,       // clock input
    input  wire rst,       // synchronous reset
	 input  wire d,
    output reg  [2:0] q   // 3-bit counter output
);

initial begin
     q <= 3'b0000;
	 end

always @(posedge clk) 
begin
q <= 3'b000;
    if (rst) 
        q <= 3'b000;       // reset counter to 0
    else if(d)
        q <= q + 1;        // increment counter
		  else
		  q <= q - 1;
end

endmodule


Developed by:MUGILARASI E


RegisterNumber:25017644


**RTL LOGIC UP COUNTER**
<img width="1920" height="1080" alt="Screenshot (53)" src="https://github.com/user-attachments/assets/42ee5a05-c7f5-4bb5-9bd3-157636058daf" />


**TIMING DIAGRAM FOR IP COUNTER**
<img width="1920" height="1080" alt="Screenshot (52)" src="https://github.com/user-attachments/assets/49de97fd-0a1b-42e8-8c51-4426816b0835" />

**TRUTH TABLE**


**RESULTS**
Thus the synchronous-up-counter using verilog and validating their functionality using their functional tables is verified.
