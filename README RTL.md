```verilog
module D_flip_flop (input d ,clk ,rest_n,
                    output reg q);
  
  always @ (posedge clk or negedge rest_n) begin
    if(rest_n ==0)
      q <= 0;
    else
      q <= d;
  end

endmodule
