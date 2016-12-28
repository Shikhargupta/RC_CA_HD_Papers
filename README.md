# RC_CA_HD_Papers
Database of Reconfigurable Computing, Computer Architecture and Hardware Design Papers

## Computer Architecture

### [Requirements, Bottlenecks, and Good Fortune: Agents for Microprocessor Evolution, Yale Patt, Proceedings of the IEEE Nov 2001] (computer-architecture/bottlenecks-microprocessors.pdf).

* the paper talks about
  i) basic framework for the field of microprocessors
  ii) important advancements that happened in this area during 1970-2000
  iii) future aspects (in 2001) of high performance micro-architectures
* it suggests that that this evolution did not just happen, that each step forward came as a result of one of three things, and always within the context of a computer architect making tradeoffs. The three things are: 1) new requirements; 2) bottlenecks; and 3) good fortune collectively called as agents of evolution.

#### Basic Framework
* computer architetcture is a science of trade offs. The design of a microprocessor is about making relevant tradeoffs.
* the problems goes through a series of transformations to be solved. 
  * the problem solution is first formulated as an algorithm to remove the unacceptable characteristics of natural language, such as         ambiguity. 
  * It is then encoded in a mechanical language and compiled to the instruction set architecture (ISA) of the particular microprocessor.
  * The ISA is the agreed upon interface that: 1) the compiled program uses to tell the microprocessor what it (the program) needs done     and 2)the microprocessor uses to know what it must carry out in behalf of the program.
* each microprocessor consists of circuits which implement hardware structures (collectively called the microarchitecture) which provide     an interface (called the ISA) to the software.
* At each step in the hierarchy, from choice of algorithm, to language, to ISA to microarchitecture, to circuits, there are choices and   therefore tradeoffs.
* Performance, cost, heat dissipation, and power consumption are examples of characteristics that strongly affect a design point
* as long as people dream up more uses for computers, the need for microprocessors and the tradeoffs that each will make will continue     to expand. That is, the application space (or, rather, the applications of central importance) drive the design point.
* Three things can get in the way of fully supplying the core with instructions to process: instruction cache misses, fetch breaks,       and conditional branch mispredictions.When an access tothe instruction cache fails, the supply of instructions drops to zero until the   cache miss is serviced. A fetch break occurs when an instruction being fetched is a taken branch, rendering useless all the             subsequent instructions fetched in the same cycle, independent of the issue width. A conditional branch misprediction means that all     instructions fetched since the mispredicted branch represent wasted effort, and must be thrown away before proceeding along the         correct instruction path.
* real data storage suffers from latency to obtain a particular data element and the bandwidth necessary to move that data element from   its location in the storage hierarchy to the core of the processor where it is needed

#### Agents for Evolution
1. New requirements
  * The demand for higher performance dictated that fetching one instruction each cycle was insufficient. The result is the wide-issue       microprocessor, where the fetch mechanism allows multiple instructions to be fetched, decoded and issued to the execution core each     cycle.
  * Today the prevailing new requirement involves power consumption, or what is being referred to as power-aware computing.

2. Bottlenecks
  * By far, most of the improvements to the microprocessor have come about due to attempts to eliminate bottlenecks that prevent these       three components from doing their jobs.
  * eg.- instruction supply requires fetching some number—today four—instructions each cycle. If these instructions were stored in           memory,   the time to fetch would be too long. The bottleneck is the slow memory. Thus, the instruction cache was invented

3. Good Fortune
  * Good fortune happens when something causes a windfall which can then be used to provide additional features to the microprocessor
  * A good example of this is the technology shrink that allows a next implementation of a microprocessor to take up less space on the       chip than the previous implementation did. With less space required by the old design, more space is available for doing other           things.

#### Evolution
* Pipelining: Early microprocessors processed one instruction from fetch to retirement before starting on the next instruction.           Pipelining, which had been around at least since the 1960s in mainframe computers, was an obvious solution to that performance           bottleneck
* On-Chip Caches:  The latency to get instructions and data from off-chip memory to the on-chip processing elements was too long. The     result: an on-chip cache
* Branch Prediction: The benefits of pipelining are lost if conditional branches produce pipeline stalls waiting for the condition on     which the branch is based to be resolved. Hardware (run-time) branch predictors did not show up on the microprocessor chip until the     early 1990s
* Out-of-order processing:  This produces a bottleneck each time an instruction that can not be carried out prevents a subsequent instruction from being executed if the subsequent instruction has all that it needs to begin execution
* Clusters: Single die size continues to increase, feature size continues to decrease, and on-chip frequencies continue to increase. The   result is that a value produced by a functional unit at one corner of the chip can not traverse the chip and be available as a source   to a functional unit at the opposite corner of the chip in the next cycle. The result—partition the execution core into clusters so     that most of the time, results produced by a functional unit in one cluster will be used by another functional unit in the same         cluster
* Chip Multiprocessor: An alternative use of the increasing richness of the die (many more transistors, combined with faster operating frequency) is to partition the chip into regions, with an identical processoroccupying each region.The paradigm is referred to as CMP, for chip multiprocessor

#### Future Aspects
* Some signals will require multiple cycles to traverse the chip, and one must examine carefully which signals will be allowed to do that. Most signals will probably not be allowed to. Therein lies the challenge: to redesign the data path in light of the new constraint of wire length.
* The future transistor budget can provide enormous flexibility to properly take advantage of the variability of the on-chip needs. 
* an on-chip structure, perhaps a low granularity FPGA, but more likely a higher granularity reconfigurable logic structure, will be common to future microprocessors.


### [Memory Scaling: A Systems Architecture Perspective, Onur Mutlu, Proceedings of the IEEE International Memory Workshop 2013] (computer-architecture/memory_scaling.pdf).

* In this paper, after describing the demands and challenges faced by the memory system, author examines some promising research and design directions to overcome challenges pose by memory scaling.
* He talks about three key solution directions - i) New DRAM architectures to enable better integration with rest of the system ii) New alternatives that may replace DRAM iii) Providing predictable performance and QoS to applicarions sharing the memory.
* energy and power consumption have become key design limiters as the memory system continues to be responsible for a significant fraction of overall system energy/power.
* In the context of new DRAM architecture, he says key problems can be solved more easily if we rethink the DRAM architecture and functions, and redesign the interface such that DRAM, controllers, and processors closely cooperate. He calls this high-level solution approach system-DRAM co-design. He also provides solutions to the common bottlenecks of memory scaling - refresh rates, parallelism, latency and energy consumption, capacity and bandwidth waste.
* He has shed light over new emerging technologies such as PCM and STT-MRAM that usually provide a tradeoff, and seem unlikely to completely replace DRAM, as they are not strictly superior to DRAM.
* He talks about hybrid memory - combination of storage and memory. But as the non-volatility of main memory opens up new opportunities that can be exploited by higher levels of the system stack to improve performance and eliability/consistency, it also can lead to potentially unforeseen security and privacy issues: critical and private data can persist long after the system is powered down, and an attacker can take advantage of this fact.
* He also points towards the fact that how providing performance to the various applications sharing the same memory can lead to better system performance. He has also talked about the improvement of retention of flash storages by introducing simple error correcting codes.


### [Memory Performance Attacks: Denial of Memory Service in Multi-Core Systems, Usenix Security, 2007](computer-architecture/performance in multi-core).

* This paper demonstrates that current multi-core processors are vulnerable to a new class of Denial of Service (DoS) attacks because the memory system is "unfairly" shared among multiple cores.
* 





## Reconfigurable Computing

### [A Novel FPGA Architecture Supporting Wide, Shallow Memories, Steven W. Oldridge and Steven J. E. Wilton, IEEE TRANSACTIONS ON VLSI SYSTEMS, 2005] (reconfigurable_computing/wide, shallow memories using fpga.pdf)

* The author proposes an architecture for wide and shallow memories, designed specifically to support wide buffering applications.
* These memories may be over 100 bits in width, but only a handful (8–32) words deep. As I/O bandwidth on FPGAs increases, and more circuits begin to take advantage of these high speed I/Os, the need for efficient wide data blocks, including wide, shallow memories, will grow.
*  By adding only a modest amount of circuitry, the configuration memory in the unused switch blocks can be used to implement wide, shallow buffers and other similar memory structures.
*  Rather than adding new memory bits to the switch block, author's approach is to provide circuitry to allow the user to write and read the configuration memory corresponding to all diagonal connections within the switch block.

### [Simplified Spiking Neural Network Architecture and STDP Learning Algorithm Applied to Image Classification, EURASIP Journal on Image and Video Processing, 2015] (reconfigurable_computing/STDP algo.pdf)

* The paper talks about the wide range applications of SNN and simplified algorithm to train the feed forward network on hardware. The paper also compares the results of simplified algorithm with that of conventional one.
* The network used in the paper consists of one input layer (sensory neurons) and one hidden layer. Each sensory neuron has its weighted receptive field (5x5 window).
* Spike time dependent plasticity algo is used to train the network so that synapses are adapted according to the training data (handwritten integers).
* Reinforcement learning curve is used to adapt the weights (synapses) between the neurons.
* The algorithm is simplified so that it can be efficiently implemented on FPGAs (reconfigurable logic) and hence can be used as hardware accelerators for the network.
