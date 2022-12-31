# MIPS_32_PIPELINED

## Five stages of MIPS pipelined implementation :
1) Fetch instruction from memory.
2) Read registers while decoding the instruction.The regular format of MIPS instructions allows reading and decoding to occur simultaneously.
3) Execute the operation or calculate an address
4) Access an operand in data memory.
5) Write the result into a register.

### "Pipelining improves performance by increasing instruction throughput, as opposed to decreasing the execution time of an individual instruction, but instruction 
###  throughput is the important metric because real programs execute billions of instructions".
