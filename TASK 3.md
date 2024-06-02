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
-Now to see the output waveform, type <br/>
 $ gtkwave iiitb_rv32i.vcd<br/>
The GTKWAVE window will get opened.<br/>
 ![Screenshot 2024-06-02 152558](https://github.com/nisarg-patel-24/VSDSquadron-Mini-Research-Internship/assets/167600511/d7e10424-ccb5-4bb7-a4ce-2b3cb9475e4b)<br/>
Now, to observe waveforms, leftmost there is file name iiitb_rv32i, just click on add button and dropdown file of rv32i will show.<br/>
Many type of signal options will be available.<br/>
Select related and click on Insert to observe its waveform.<br/>
![Screenshot 2024-06-02 145547](https://github.com/nisarg-patel-24/VSDSquadron-Mini-Research-Internship/assets/167600511/e736322d-3ca5-4c78-b7e6-39b06af7eb1a)<br/><br/>

 #### Observing RISCV Instructions:
 1. ADD r6, r2, r1<br/>
 ![Screenshot 2024-06-02 151842](https://github.com/nisarg-patel-24/VSDSquadron-Mini-Research-Internship/assets/167600511/1cdded12-e320-4183-8991-e814dacdc585)<br/>
 2. SUB r7, r1, r2<br/>
 ![Screenshot 2024-06-02 151900](https://github.com/nisarg-patel-24/VSDSquadron-Mini-Research-Internship/assets/167600511/3bba8331-059d-479e-9ffb-824b20eb35eb)<br/>
 3. AND r8, r1, r3<br/>
 ![Screenshot 2024-06-02 151917](https://github.com/nisarg-patel-24/VSDSquadron-Mini-Research-Internship/assets/167600511/b4cbe70c-70e2-40dd-854d-8f390fe52bbd)<br/>
 4. OR r9, r2, r5<br/>
 ![Screenshot 2024-06-02 151943](https://github.com/nisarg-patel-24/VSDSquadron-Mini-Research-Internship/assets/167600511/f2da0ab5-2a7f-41ca-81c4-f81b227d3834)<br/>
 5. XOR r10, r1, r4<br/>
![Screenshot 2024-06-02 152002](https://github.com/nisarg-patel-24/VSDSquadron-Mini-Research-Internship/assets/167600511/95f740e0-7d9d-4368-82c0-e4456bc3b741)<br/>
 6. SLT r11, r2, r4<br/>
  ![Screenshot 2024-06-02 152021](https://github.com/nisarg-patel-24/VSDSquadron-Mini-Research-Internship/assets/167600511/026ef41f-bf9a-4c44-9eb1-5e6b04466e08)<br/>
 7. ADDI r12, r4, 5<br/>
 ![Screenshot 2024-06-02 152035](https://github.com/nisarg-patel-24/VSDSquadron-Mini-Research-Internship/assets/167600511/8b915532-2dfd-4d12-9af2-352752477cfa)<br/>
 8. SW r3, r1, 2<br/>
 ![Screenshot 2024-06-02 152500](https://github.com/nisarg-patel-24/VSDSquadron-Mini-Research-Internship/assets/167600511/398623af-3253-490d-8cdd-daf52b1741b9)<br/>
 9. LW r13, r1, 2<br/>
 ![Screenshot 2024-06-02 152517](https://github.com/nisarg-patel-24/VSDSquadron-Mini-Research-Internship/assets/167600511/6ec16b77-2ab3-4d15-946d-68df61d26460)<br/>
10. BEQ r0, r0, 15<br/>
-AFTER BRANCHING SHOWN IN BELOW INSTRUCTION.
11. ADD r14, r2, r2<br/>
 ![Screenshot 2024-06-02 152531](https://github.com/nisarg-patel-24/VSDSquadron-Mini-Research-Internship/assets/167600511/76d86665-6256-468f-85d0-77bcce7d2967)<br/>
