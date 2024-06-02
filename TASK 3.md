# VSDSqaudron Mini Research Internship
### TASK 3 ---> FUNCTIONAL SIMULATION OF RISCV INSTRUCTIONS
###### Reference : https://github.com/vinayrayapati/rv32i
###### Installing ICARUS VERILOG AND GTKWAVE [used for simulation purpose]
->ICARUS VERILOG (iverilog)
 - Icarus Verilog is an implementation of the Verilog hardware description language compiler that generates netlists in the desired format and a simulator.<br/>
->GTKWAVE<br/>
 - GTKWave is a fully featured GTK+ based waveform viewer which reads FST and GHW files as well as standard Verilog VCD/EVCD files and allows their viewing. The viewer supports both post-mortem viewing of VCD files and interactive viewing of VCD data.<br/>
##### Steps for installing both in ubuntu:<br/>
-Open the terminal.<br/>
-Type the following command.<br/>
$ sudo apt-get install iverilog gtkwave<br/>
-Then clone the given reference repository which contains the verilog netlist and testbench in it.<br/>
-Now get into the3 iiitb_riscv32i file for this, use <br/> $ cd iiitb_rv32i<br/>
-Now to simulate the verilog code and to get output type the following command<br/>
 $ iverilog -o iiitb_rv32i iiitb_rv32i.v iiitb_rv32i_tb.v
 $ ./iiitb_rv32i
![Screenshot 2024-05-31 213851](https://github.com/nisarg-patel-24/VSDSquadron-Mini-Research-Internship/assets/167600511/0fd162ea-f995-45f1-8c0a-09899dc34150)<br/>
![Screenshot 2024-05-31 213911](https://github.com/nisarg-patel-24/VSDSquadron-Mini-Research-Internship/assets/167600511/695cfe2f-ae2c-457e-bb08-4e863d5095ce)<br/>
-Now to see the output waveform, type 
 $ gtkwave iiitb_rv32i.vcd
 
