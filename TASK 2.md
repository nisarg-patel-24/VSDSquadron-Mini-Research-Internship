# VSDSquadron-Mini-Research-Internship
## TASK 2 ---> UNDERSTANDING THE RISCV INSTRUCTION SET
#### ABOUT RISCV:
##### What is RISCV ?
RISC-V is an open way to design computer processors. It’s a set of instructions that tells the hardware how to perform tasks. 
The full form of RISCV is  Reduced Instruction Set Computer Five.
<br/><br/>
RISC relates with the designing of architecture.
<br/>V (five) signifies that it is fifth generation architecture.
###### By convention, RISCV instructions are each
1 word = 4 bytes = 32 bits
* Divide the 32 bits of an instruction into“fields”.
### How Does RISC-V work?
Computer processors follow sets of instructions to perform tasks. 
<br/>
RISC-V instructions are grouped into different types based on their function. Here are some key types:
<br/>
#### R-Type (Register Operations):
Define “fields” of the following number of bits
each: 7 + 5 + 5 + 3 + 5 + 7 = 32
<br/>![Screenshot 2024-05-28 144917](https://github.com/nisarg-patel-24/VSDSquadron-Mini-Research-Internship/assets/167600511/195ac657-0d17-4fd5-9b54-9a4fd8372245)<br/>
Each field has a name as shown below:
     ![Screenshot 2024-05-28 144950](https://github.com/nisarg-patel-24/VSDSquadron-Mini-Research-Internship/assets/167600511/97af4e2e-5e89-4992-895e-e9fc9143ad0f)
<br/>
* Each field is viewed as its own unsigned int.
* 5-bit fields can represent any number 0-31,
  while 7-bit fields can represent any number 0-128.
* opcode (7): partially specifies operation
   – e.g. R-types have opcode = 0b0110011,
* funct7+funct3 (10): combined with opcode,these two fields describe what operation to perform.
We can encode 1024 instructions under this R type. As 2^10 = 1024.<br/>
![Screenshot 2024-05-28 170944](https://github.com/nisarg-patel-24/VSDSquadron-Mini-Research-Internship/assets/167600511/a748567b-094a-4c99-ac0e-148c57d49584)<br/>
These instructions perform tasks like adding or subtracting numbers directly in the computer's registers (small storage areas inside the CPU).<br/>
Example: add x1, x2, x3 (Add the data of registers x2 and x3, and store the result in x1).
#### I-Type (Immediate and Load Operations):
* Define “fields” of the following number of bits
each: 12 + 5 + 3 + 5 + 7 = 32
   <br/> ![Screenshot 2024-05-28 150236](https://github.com/nisarg-patel-24/VSDSquadron-Mini-Research-Internship/assets/167600511/ad6b17ac-9cb7-43a2-b279-0f7c3497a663)<br/>
   Each field has a name as shown below:
<br/> ![Screenshot 2024-05-28 150348](https://github.com/nisarg-patel-24/VSDSquadron-Mini-Research-Internship/assets/167600511/3e557ea6-c2d3-4a35-b8c9-19419e545a5a)<br/>
* Only imm field is different from R-format: rs2 and funct7 replaced by 12-bit signed immediate, imm[11:0].
* opcode (7): uniquely specifies the instruction.
* rs1 (5): specifies a register operand.
* rd (5): specifies destination register that receives result of computation.<br/>
Used for tasks that involve a fixed number (an immediate value) or loading data from memory.<br/>
Example: addi x1, x2, 10 (Add the number 10 to the data of register x2, and store the result in x1).<br/>
#### S-Type (Store Operations):
S-type is used for stores.<br/>
Store needs to read two registers, rs1 for base memory address, and rs2 for data to be stored
<br/> ![Screenshot 2024-05-28 151558](https://github.com/nisarg-patel-24/VSDSquadron-Mini-Research-Internship/assets/167600511/906512b7-3514-4af4-99fa-91356850b913)
<br/>![Screenshot 2024-05-28 155156](https://github.com/nisarg-patel-24/VSDSquadron-Mini-Research-Internship/assets/167600511/56b7977a-c724-4451-b98d-b2fa9beb4f36)<br/>
Total 32 bits: 7 + 5 + 5 +3 + 5 + 7 =32<br/>
###### Breakdown of each field:
* imm[11:5]: The upper 7 bits of the 12-bit immediate value.
* rs2: The register containing the data to be stored (5 bits).
* rs1: The base address register (5 bits). The memory address is computed by adding the immediate value to the contents of this register.
* funct3: The function field (3 bits) that specifies the type of store operation (e.g., byte, halfword, word).
* imm[4:0]: The lower 5 bits of the 12-bit immediate value.
* opcode: The operation code (7 bits), which is 0100011 for S-Type instructions.<br/>
S-Type instructions in RISC-V provide a simple and efficient way to move data from CPU registers to memory, which is essential for a wide range of computing tasks.<br/>
#### Types of S-Type Instructions <br/>
###### SB (Store Byte): 
Stores a byte (8 bits) from a register to memory.<br/>
Example: sb x3, 4(x2)<br/>
funct3 = 000<br/>
###### SH (Store Halfword): 
Stores a halfword (16 bits) from a register to memory.<br/>
Example: sh x3, 4(x2)<br/>
funct3 = 001<br/>
###### SW (Store Word): 
Stores a word (32 bits) from a register to memory.<br/>
Example: sw x3, 4(x2)<br/>
funct3 = 010<br/>

Example: sw x3, 4(x2) (Store the contents of register x3 into the memory location calculated by adding 4 to the contents of register x2).
#### B-Type (Branch Operations):
B-Type (Branch Type) Instructions are used for conditional branching in RISC-V. These instructions allow the program to change the flow of execution based on the comparison of two registers. Conditional branching is essential for implementing control structures like if-else statements and loops.<br/>
Total 32 bits: 1 + 6 + 5 + 5 +3 + 4 + 1 + 7 = 32.<br/>
![Screenshot 2024-05-28 160410](https://github.com/nisarg-patel-24/VSDSquadron-Mini-Research-Internship/assets/167600511/b6f348c5-0fe3-4d9e-9f6d-76cb19cbe4aa)<br/>
![Screenshot 2024-05-28 160653](https://github.com/nisarg-patel-24/VSDSquadron-Mini-Research-Internship/assets/167600511/89140253-05c3-4098-bfd0-384fbc509a03)<br/>

#### Breakdown of each field:

* imm[12]: The 12th bit of the immediate value.
* imm[10:5]: The 10th to 5th bits of the immediate value.
* rs2: The second source register (5 bits).
* rs1: The first source register (5 bits).
* funct3: The function field (3 bits) that specifies the type of branch operation (e.g., equal, not equal, less than).
* imm[4:1]: The 4th to 1st bits of the immediate value.
* imm[11]: The 11th bit of the immediate value.
* opcode: The operation code (7 bits), which is 1100011 for B-Type instructions.
#### Types of B-Type Instructions
###### BEQ (Branch if Equal):
* Instruction: beq rs1, rs2, offset
* Operation: Branch to PC + offset if rs1 == rs2.
* funct3: 000
##### BNE (Branch if Not Equal):
* instruction: bne rs1, rs2, offset
* operation: Branch to PC + offset if rs1 != rs2.
* funct3: 001
##### BLT (Branch if Less Than):
* instruction: blt rs1, rs2, offset
* Operation: Branch to PC + offset if rs1 < rs2 (signed comparison).
* funct3: 100
##### BGE (Branch if Greater or Equal):
* Instruction: bge rs1, rs2, offset
* operation: Branch to PC + offset if rs1 >= rs2 (signed comparison).
* funct3: 101
##### BLTU (Branch if Less Than Unsigned):
* instruction: bltu rs1, rs2, offset
* operation: Branch to PC + offset if rs1 < rs2 (unsigned comparison).
* funct3: 110
##### BGEU (Branch if Greater or Equal Unsigned):
* Instruction: bgeu rs1, rs2, offset
* operation: Branch to PC + offset if rs1 >= rs2 (unsigned comparison).
* funct3: 111<br/><br/>

Example: beq x1, x2, 8 (If the contents of x1 and x2 are equal, jump to the instruction located 8 places ahead).
#### U-Type (Upper Immediate Operations):
U-Type (Upper Immediate) Instructions are used to handle large immediate values in RISC-V. These instructions are essential for setting up addresses or constants in registers. U-Type instructions provide a straightforward way to manipulate the upper 20 bits of a 32-bit register.<br/> ![Screenshot 2024-05-28 164203](https://github.com/nisarg-patel-24/VSDSquadron-Mini-Research-Internship/assets/167600511/791a3321-8237-4b67-8122-9af6b747e2c7)<br/>
![Screenshot 2024-05-28 164249](https://github.com/nisarg-patel-24/VSDSquadron-Mini-Research-Internship/assets/167600511/a7482e82-c657-4b4e-8e92-26e9e05d828a)<br/>

#### Breakdown of each field:
* imm[31:12]: The upper 20 bits of the immediate value (20 bits).
* rd: The destination register (5 bits) where the result will be stored.
* opcode: The operation code (7 bits).
### Types of U-Type Instructions
There are two primary U-Type instructions in RISC-V:<br/>
##### LUI (Load Upper Immediate)
* Instruction: lui rd, imm
* Operation: Loads the upper 20 bits of register rd with the immediate value imm. The lower 12 bits of the register are set to zero.
* Example: lui x5, 0x12345
* Opcode: 0110111
##### AUIPC (Add Upper Immediate to PC)
* Instruction: auipc rd, imm
* Operation: Adds the upper 20 bits of the immediate value to the current program counter (PC), then stores the result in register rd.
* Example: auipc x5, 0x12345
* Opcode: 0010111<br/>
  
Example: lui x1, 0x10000 (Load the upper 20 bits of register x1 with the value 0x10000).
#### J-Type (Jump Operations):
J-Type (Jump Type) Instructions are used for unconditional jumps in RISC-V. These instructions allow the program to jump to a new address, which is essential for implementing control flow structures like function calls and loops.<br/>
![Screenshot 2024-05-28 165730](https://github.com/nisarg-patel-24/VSDSquadron-Mini-Research-Internship/assets/167600511/e4e2cde0-32cb-4459-8bfd-928be90870d8)<br/>
![Screenshot 2024-05-28 165905](https://github.com/nisarg-patel-24/VSDSquadron-Mini-Research-Internship/assets/167600511/5ace81f4-f826-4fae-a7b2-cae79a04a630)<br/>
#### Breakdown of each field:
* imm[20]: The 20th bit of the immediate value.
* imm[10:1]: Bits 10 to 1 of the immediate value.
* imm[11]: The 11th bit of the immediate value.
* imm[19:12]: Bits 19 to 12 of the immediate value.
* rd: The destination register (5 bits) where the return address will be stored.
* opcode: The operation code (7 bits), which is 1101111 for J-Type instructions<br/>
#### Types of J-Type Instructions
There is one primary J-Type instruction in RISC-V:<br/>
##### JAL (Jump and Link):
* Instruction: jal rd, offset
* Operation: Jumps to the address calculated by adding the signed immediate value to the current PC. The address of the next instruction (PC + 4) is stored in the destination register rd.
* Example: jal x5, 0x2000
* Opcode: 1101111<br/>
  
These are used for jumping to a new location in the code, useful for loops and function calls.<br/>
Example: jal x1, 16 (Jump to the instruction located 16 places ahead and save the return address in x1).
<br/>
### List of RISCV Instructions type:
1. ADD r6, r2, r1
-> This is R-type instruction. it performs the adddition of values stored in r2 and r1 and adds them and stores the result in r6.
   * funct7: 0000000
   * rs2: r1 is register 1, so the binary encoding is 00001.
   * rs1: r2 is register 2, so the binary encoding is 00010.
   * funct3: 000 (for ADD).
   * rd: r6 is register 6, so the binary encoding is 00110.
   * opcode: 0110011<br/>
32 bit pattern is 0000000 00001 00010 000 00110 0110011

2. SUB r7, r1, r2
-> This is R-type instruction, it performs substraction of r2 from r1 and stores result in r7.
   * funct7: 0100000
   * rs2: r2 is register 2, so the binary encoding is 00010.
   * rs1: r1 is register 1, so the binary encoding is 00001.
   * funct3: 000 (for SUB).
   * rd: r7 is register 7, so the binary encoding is 00111.
   * opcode: 0110011<br/>
32 bit pattern is 0100000 00010 00001 000 00111 0110011

3. AND r8, r1, r3
-> This is R-type instruction,it performs BITWISE AND operation between r1 and r3 and stores the result in r8.
   * funct7: 0000000
   * rs2: r3 is register 3, so the binary encoding is 00011.
   * rs1: r1 is register 1, so the binary encoding is 00001.
   * funct3: 111 (for AND).
   * rd: r8 is register 8, so the binary encoding is 01000.
   * opcode: 0110011<br/>
32 bit pattern is 0000000 00011 00001 111 01000 0110011

4. OR r9, r2, r5
-> this is R-type instruction,it performs the bitwise OR of the values in r2 and r5, and stores the result in r9.
   * funct7: 0000000
   * rs2: r5 is register 5, so the binary encoding is 00101.
   * rs1: r2 is register 2, so the binary encoding is 00010.
   * funct3: 110 (for OR).
   * rd: r9 is register 9, so the binary encoding is 01001.
   * opcode: 0110011<br/>
32 bit pattern is 0000000 00101 00010 110 01001 0110011

5. XOR r10, r1, r4
-> this is R-type instruction, it performs bitwise xor operation on r1 and r4 and stores results in r10.
  * funct7: 0000000
  * rs2: r4 is register 4, so the binary encoding is 00100.
  * rs1: r1 is register 1, so the binary encoding is 00001.
  * funct3: 100 (for XOR).
  * rd: r10 is register 10, so the binary encoding is 01010.
  * opcode: 0110011<br/>
32 bit pattern is 0000000 00100 00001 100 01010 0110011

6. SLT r11, r2, r4
-> This is R-type instruction, it performs the set-less-than comparison of the values in r2 and r4, and stores the result in r11. If the value in r2 is less than the value in r4, r11 is set to 1; otherwise, it is set to 0.
  * funct7: 0000000
  * rs2: r4 is register 4, so the binary encoding is 00100.
  * rs1: r2 is register 2, so the binary encoding is 00010.
  * funct3: 010 (for SLT).
  * rd: r11 is register 11, so the binary encoding is 01011.
  * opcode: 0110011<br/>
32 bit pattern is 0000000 00100 00010 010 01011 0110011

7. ADDI r12, r4, 5
-> This is I type instruction,it adds an immediate value of 5 to the value in register r4, and stores the result in register r12.
  * Immediate Value (imm[11:0]): 5 (decimal) is 101 in binary.
  * rs1: r4 is register 4, so the binary encoding is 00100.
  * funct3: 000 (for ADDI).
  * rd: r12 is register 12, so the binary encoding is 01100.
  * opcode: 0010011<br/>
32 bit pattern is 000000000101 00100 000 01100 0010011

8. SW r3, r1, 2
-> this is s type instruction, it stores the value in register r3 into the memory address calculated by adding the immediate offset of 2 to the value in register r1.
   * Immediate Offset (imm): 2 (decimal) is 00010 in binary.
   * rs2: r3 is register 3, so the binary encoding is 00011.
   * rs1: r1 is register 1, so the binary encoding is 00001.
   * funct3: 010 (for SW).
   *opcode: 0100011<br/>
32 bit pattern is 0000001 00011 00001 010 00010 0100011

9. SRL r16, r14, r2
-> THis is R type instruction, it is performed by using values from register r14 shifted by the value stored in register r2, and the result is stored in register r16.
   * funct7: 0000000
   * rs2: 00010 
   * rs1: 01110 
   * funct3: 001 
   * rd: 10000 
   * opcode: XXXXXXX ( not specific any opcode is suitable). <br/>
32 bit pattern is 0000000 00010 01110 001 10000 XXXXXXX

10. BNE r0, r1, 20
-> This is B type instruction, it branches to a target address that is calculated by adding the immediate offset (20) to the current instruction's address if the values in registers r0 and r1 are not equal.
  * Immediate Offset (imm): 20 (decimal) is 10100 in binary.
  * imm[12]: 0 
  * imm[10:5]: 000101 (binary) corresponds to 5 (decimal).
  * rs2: r1 is register 1, so the binary encoding is 00001.
  * rs1: r0 is register 0, so the binary encoding is 00000.
  * funct3: 001 (for BNE).
  * imm[4:1]: 0100 (binary) corresponds to 4 (decimal).
  * imm[11]: 0 
  * opcode: 1100011<br/>
32 bit pattern is 00010100 00001 00000 001 0100 0 1100011

11. BEQ r0, r0, 15
-> This is B -type instruction, it branches to a target address that is calculated by adding the immediate offset (15) to the current instruction's address if the values in registers r0 and r0 are equal.
 * immediate Offset (imm): 15 (decimal) is 01111 in binary.
 * imm[12]: 0 (since the immediate is positive, bit 12 is 0).
 * imm[10:5]: 000111 (binary) corresponds to 7 (decimal).
 * rs2: r0 is register 0, so the binary encoding is 00000.
 * rs1: r0 is register 0, so the binary encoding is also 00000.
 * funct3: 000 (for BEQ).
 * imm[4:1]: 0111 (binary) corresponds to 7 (decimal).
 * imm[11]: 0 (since the immediate is positive, bit 11 is 0).
 * opcode: 1100011<br/>
32 bit pattern is 0001110 00000 00000 000 0111 0 1100011

12. LW r13, r1, 2
-> This is I type instruction, it loads a 32-bit word from memory into register r13, using an offset of 2 bytes from the memory location specified by the value in register r1.
 * Immediate Offset (imm): 2 (decimal) is 000000000010 in binary.
 * rs1: r1 is register 1, so the binary encoding is 00001.
 * funct3: 010 (for LW).
 * rd: r13 is register 13, so the binary encoding is 01101.
 * opcode: 0000011<br/>
32 bit pattern is 000000000010 00001 010 01101 0000011

13. SLL r15, r1, r2
-> This is R type instruction, it shifts the value in register r1 to the left by the number of bits specified in register r2 and stores the result in register r15.
 * funct7: 0000000 (for logical left shift).
 * rs2: r2 is register 2, so the binary encoding is 00010.
 * rs1: r1 is register 1, so the binary encoding is 00001.
 * funct3: 001 (for SLL).
 * rd: r15 is register 15, so the binary encoding is 01111.
 * opcode: 0110011<br/>
32 bit pattern is 0000000 00010 00001 001 01111 0110011 
