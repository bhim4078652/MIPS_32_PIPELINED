# MIPS_32_PIPELINED

## Five stages of MIPS pipelined implementation :
1) Fetch instruction from memory.
2) Read registers while decoding the instruction.The regular format of MIPS instructions allows reading and decoding to occur simultaneously.
3) Execute the operation or calculate an address
4) Access an operand in data memory.
5) Write the result into a register.

"Pipelining improves performance by increasing instruction throughput, as opposed to decreasing the execution time of an individual instruction, but instruction 
 throughput is the important metric because real programs execute billions of instructions".

All the architecture is same as single cycle but extra components added in datapath are listed below.
- 4 pipeline registers to pass on the information calculated in previous stage.
- comparator and adder in ID stage to reduce the number of stall cycles to 1 in case of branch instructions.
- Hazard detection unit in ID stage to detect load word hazard.
- Forwarding unit in EX stage to reduce unnecessary stall cycles.
- some small components like mux etc.

### Pipeline Hazards
There are situations in pipelining when the next instruction cannot execute in the  following clock cycle. These events are called hazards, and there are three 
different types.

1) structural hazard.
2) data hazard.
3) control hazard.

- The first hazard is called a structural hazard. It means that the hardware cannot support the combination of instructions that we want to execute in the same clock 
  cycle. structural hazard When a planned instruction cannot execute in the proper clock cycle because the hardware does not  support the combination  of instructions 
  that are set to execute.Separate instruction and data memory is solution for structural hazard encountered in memory access.
 
 - 
