
# Code
module alu(input[1:0]a,b,input[2:0]sel,
output reg[1:0] result,
output reg carry);
always @ (*) begin
result =2'b00;
carry = 1'b0;
case(sel)
3'b000 : {carry,result}= a+b;
3'b001 : {carry,result}= a-b;
3'b010 : result = a&b;
3'b011 : result = a|b;
3'b100 : result = a^b;
default: result = 2'b00;
endcase
end
endmodule
# Testbench
module alu_tb;
    reg [1:0] a, b;
    reg [2:0] sel;
    wire [1:0] result;
    wire carry;
    alu uut (.a(a), .b(b), .sel(sel), .result(result), .carry(carry));

initial begin
$monitor("Time=%0t | A=%b B=%b Sel=%b | Res=%b Carry=%b", $time, a, b, sel, result, carry);
a = 2'b10; b = 2'b01; sel = 3'b000; 
#10;
a = 2'b11; b = 2'b10; sel = 3'b001; 
#10;
a = 2'b11; b = 2'b01; sel = 3'b010; 
#10;
a = 2'b11; b = 2'b10; sel = 3'b011; 
#10;
a = 2'b11; b = 2'b11; sel = 3'b100; 
#10;
$stop; 
end
endmodule


<img width="1600" height="574" alt="WhatsApp Image 2026-05-12 at 12 31 16 PM (1)" src="https://github.com/user-attachments/assets/05a45b1f-7714-4d17-b97a-5bd4d51bff6b" />

