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

* Divide the 32 bits of an instruction into
“fields”.
### How Does RISC-V work?
Computer processors follow sets of instructions to perform tasks. 
<br/>
RISC-V instructions are grouped into different types based on their function. Here are some key types:
<br/>
#### R-Type (Register Operations):
<br/><br/>
These instructions perform tasks like adding or subtracting numbers directly in the computer's registers (small storage areas inside the CPU).
Example: add x1, x2, x3 (Add the data of registers x2 and x3, and store the result in x1).
#### I-Type (Immediate and Load Operations):
<br/><br/>
Used for tasks that involve a fixed number (an immediate value) or loading data from memory.
Example: addi x1, x2, 10 (Add the number 10 to the data of register x2, and store the result in x1).
#### S-Type (Store Operations):
<br/> <br/>
These instructions store data from a register into memory.
Example: sw x3, 4(x2) (Store the contents of register x3 into the memory location calculated by adding 4 to the contents of register x2).
#### B-Type (Branch Operations):
<br/> 
<br/>
Used for making decisions and changing the flow of the program (like if-else statements in programming).
Example: beq x1, x2, 8 (If the contents of x1 and x2 are equal, jump to the instruction located 8 places ahead).
#### U-Type (Upper Immediate Operations):
<br/> <br/>
These set a part of a register to a large immediate value, often used for initializing addresses or constants.
Example: lui x1, 0x10000 (Load the upper 20 bits of register x1 with the value 0x10000).
#### J-Type (Jump Operations):
<br/><br/>
These are used for jumping to a new location in the code, useful for loops and function calls.
Example: jal x1, 16 (Jump to the instruction located 16 places ahead and save the return address in x1).
