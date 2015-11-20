module hex_decoder(data, segments);
	input [3:0] data;
	output [6:0] segments;
	reg [6:0] segments;

	parameter BLANK = 7'b111_1111; 
	parameter ZERO = 7'b100_0000; 
	parameter ONE = 7'b111_1001; 
	parameter TWO = 7'b010_0100; 
	parameter THREE = 7'b011_0000; 
	parameter FOUR = 7'b001_1001; 
	parameter FIVE = 7'b001_0010; 
	parameter SIX = 7'b000_0010; 
	parameter SEVEN = 7'b111_1000; 
	parameter EIGHT = 7'b000_0000; 
	parameter NINE = 7'b001_0000; 
	parameter A = 7'b000_1000;
	parameter B = 7'b000_0011;
	parameter C = 7'b100_0110;
	parameter D = 7'b010_0001;
	parameter E = 7'b000_0110;
	parameter F = 7'b000_1110;
	always @(*)
	begin
		case (data)
			4'b0000: segments <= ZERO;
			4'b0001: segments <= ONE;
			4'b0010: segments <= TWO;
			4'b0011: segments <= THREE;
			4'b0100: segments <= FOUR;
			4'b0101: segments <= FIVE;
			4'b0110: segments <= SIX;
			4'b0111: segments <= SEVEN;
			4'b1000: segments <= EIGHT;
			4'b1001: segments <= NINE;
			4'b1010: segments <= A;
			4'b1011: segments <= B;
			4'b1100: segments <= C;
			4'b1101: segments <= D;
			4'b1110: segments <= E;
			4'b1111: segments <= F;
			default: segments <= BLANK;
		endcase
	end
endmodule
