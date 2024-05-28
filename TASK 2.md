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
U-Type (Upper Immediate) Instructions are used to handle large immediate values in RISC-V. These instructions are essential for setting up addresses or constants in registers. U-Type instructions provide a straightforward way to manipulate the upper 20 bits of a 32-bit register.<br/> <br/>

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
* Effect: x5 = 0x12345000
* Opcode: 0110111
##### AUIPC (Add Upper Immediate to PC)
* Instruction: auipc rd, imm
* Operation: Adds the upper 20 bits of the immediate value to the current program counter (PC), then stores the result in register rd.
* Example: auipc x5, 0x12345
* Effect: x5 = PC + 0x12345000
* Opcode: 0010111<br/>
  
Example: lui x1, 0x10000 (Load the upper 20 bits of register x1 with the value 0x10000).
#### J-Type (Jump Operations):
<br/><br/>
These are used for jumping to a new location in the code, useful for loops and function calls.
Example: jal x1, 16 (Jump to the instruction located 16 places ahead and save the return address in x1).
