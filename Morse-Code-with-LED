`timescale 1ns / 1ns // `timescale time_unit/time_precision
module Morse_Display (SW, LEDR, KEY, CLOCK_50);
	input [2:0] SW;
	input CLOCK_50;
	output [0:0] LEDR;
	input [1:0] KEY;
	 
	wire [10:0] w;
	wire a;
	wire mrs_out;
	 
	lut uo (
	   .in({SW[0],SW[1],SW[2]}),
	   .out(w)
		);
	RateDivider u3(
		.clk_in(CLOCK_50),
		.clk_out(a),
		.s0(0),
		.s1(1)
		);
	hft_reg u1 (
		.start(KEY[0]),
		.in(w),
		.out(mrs_out),
		.reset(KEY[1]),
		.clock(CLOCK_50),
		.enable(a)
		);
	Morse u2 (
		.clock(a),
		.Clear_b(1),
		.Enable(mrs_out),
		.q(LEDR[0])
		);
endmodule

module lut (in, out);
	input [2:0] in;
	output reg [10:0] out;
	 
	always @(*)
	begin
	 case (in)
	  3'b000: out = 11'b00000011101;
	  3'b001: out = 11'b00101010111;
	  3'b010: out = 11'b10111010111;
	  3'b100: out = 11'b00001010111;
	  3'b011: out = 11'b00000000001;
	  3'b101: out = 11'b00101110101;
	  3'b110: out = 11'b00101110111;
	  3'b111: out = 11'b00001010101;
	  default: out = 11'b00000000000;
	 endcase
	end
endmodule
module shft_reg (in, out, reset, clock, start, enable);

	 input clock;
	 input start;
	 input enable;
	 integer i;
	 input [10:0] in;
	 input reset;
	 reg [10:0] store;
	 output reg out;
	 
	 
	 always @(posedge clock) 
	 begin
	  if (enable == 1'b1) begin
	   if (reset == 1'b0) begin
		store <= 0;
		out = 0;   
	   end
	   else if (start == 1'b0)begin 
		out = store[0];
		store = store >> 1;
		
	   end 
	   else begin
		store = in;
		out = 0;
	   end
	  end
	 end
 
endmodule

module RateDivider (clk_in, clk_out, s0, s1);
	input clk_in;
	input s0, s1;
	output reg clk_out = 1'b0;
	reg [27:0] w = 28'b0;
	 
	always @(*)
	 begin
	  case ({s0,s1})
		2'b00: clk_out = (w >= 1); 
		2'b01: clk_out = (w >= 29999999); 
		2'b10: clk_out = (w >= 99999999); 
		2'b11: clk_out = (w >= 199999999);
		default: clk_out = 0;
	  endcase
	end
	 
	always @(posedge clk_in)
	 begin
	  if (clk_out) w <= 28'b0;
	  else w <= w + 1'b1;
	end
endmodule

module Morse (clock, Clear_b, q, Enable);
	 input clock;
	 input Clear_b;
	 input Enable;
	 output reg q; 
		 
	 always @(posedge clock) 
		begin
		  if (Clear_b == 1'b0) 
		   q <= 0;  
		  else
		   q <= Enable;
		 end
endmodule
