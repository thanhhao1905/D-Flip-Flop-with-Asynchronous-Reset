```verilog
`timescale 1ps/1ps
module tb_D_flip_flop;
  reg d ,clk ,rest_n;
  wire q;
  
  d_ff_async_rst_n DUT (d,clk,rest_n,q);
  
  always #1 clk = ~clk;
  
  initial begin
   clk = 0;
   d = 0;
   rest_n = 0;
    
    #1 rest_n = 1;
    #5 d = 1;
    #5 d = 0;
    #5 d = 1;
    
    #10 rest_n = 0;
    #1 d = 0;
    #1 d = 1;
    
  #5;
  $finish;
  end
  
  initial begin
    $dumpfile("dump.vcd");
    $dumpvars;
  end
endmodule
