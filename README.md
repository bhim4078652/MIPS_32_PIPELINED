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

### structural hazard
- The first hazard is called a structural hazard. It means that the hardware cannot support the combination of instructions that we want to execute in the same clock 
  cycle. 
- structural hazard When a planned instruction cannot execute in the proper clock cycle because the hardware does not  support the combination  of instructions 
  that are set to execute.
- Separate instruction and data memory is solution for structural hazard encountered in memory access.
 
### data hazard
- Data hazards occur when the pipeline must be stalled because one step must wait  for another  to complete.
- In a computer pipeline, data hazards arise from the dependence of one  instruction on an earlier one that is still in the pipeline.For example, suppose we have an     add instruction  followed immediately by a subtract instruction that uses the sum ($s0):
#####                                                      add $s0, $t0, $t1 
#####                                                      sub $t2, $s0, $t3 

- Without intervention, a data hazard could severely stall the pipeline. The add instruction doesn’t write its result until the fifth stage, meaning that we would have   to waste three clock cycles in the pipeline.
- The primary solution is based on the observation that we don’t need to wait for the instruction to complete before trying to resolve the data hazard. For the code     sequence above, as soon as the ALU creates the sum for the add, we can supply it as an input for the subtract. Adding extra hardware to retrieve the missing item       early from the internal resources is called forwarding or bypassing.
- In this graphical representation of events, forwarding paths are valid only if the destination stage is later in time than the source stage. For example, there         cannot be a valid forwarding path from the output of the memory access stage in the first  instruction to the input of the execution stage of the following, since     that would mean going backward in time.

     ![App Screenshot](https://github.com/bhim4078652/MIPS_32_PIPELINED/blob/main/IMAGE_REQ/p1.jpg)

