---
title: RTCSA Tutorial Collections
date: 2023-12-30
draft: false
author: HNO3
---
**Table of Contents**

- [[#computer architecture vs. computer organization|computer architecture vs. computer organization]]
- [[#computer structure vs. computer function|computer structure vs. computer function]]
- [[#structural component of computer|structural component of computer]]
- [[#structural component of processor|structural component of processor]]
- [[#definition of embedded system|definition of embedded system]]
- [[#main considerations for designing an embedded system|main considerations for designing an embedded system]]
- [[#definition of real-time system|definition of real-time system]]
- [[#2 types of real-time system|2 types of real-time system]]
- [[#categories of real-time application|categories of real-time application]]
- [[#techniques for processors to increase speed|techniques for processors to increase speed]]
- [[#multicore systems, MICs, and GPGPUs|multicore systems, MICs, and GPGPUs]]
- [[#desirable characteristic of benchmark program|desirable characteristic of benchmark program]]
- [[#4 types of functions specified by instructions|4 types of functions specified by instructions]]
- [[#possible states that define an instruction execution|possible states that define an instruction execution]]
- [[#layers in QPI|layers in QPI]]
- [[#layers in PCIe|layers in PCIe]]
- [[#influence of width of data bus and address bus|influence of width of data bus and address bus]]
- [[#width of program counter register and instruction register|width of program counter register and instruction register]]
- [[#improve data transfer performance by: 2x clock frequency vs. 2x data bus width|improve data transfer performance by: 2x clock frequency vs. 2x data bus width]]
- [[#sequential access vs. direct access vs. random access|sequential access vs. direct access vs. random access]]
- [[#direct mapping vs. associate mapping vs. set-associate mapping|direct mapping vs. associate mapping vs. set-associate mapping]]
- [[#why need to store tag in cache|why need to store tag in cache]]
- [[#3 types of external devices|3 types of external devices]]
- [[#3 techniques for I/O|3 techniques for I/O]]
- [[#memory-mapped I/O vs. isolated I/O|memory-mapped I/O vs. isolated I/O]]
- [[#4 types of techniques to determine which device issue interrupt|4 types of techniques to determine which device issue interrupt]]
- [[#ports for I/O device|ports for I/O device]]
- [[#definition of OS|definition of OS]]
- [[#key services provided by an OS|key services provided by an OS]]
- [[#difference between a process and a program|difference between a process and a program]]
- [[#typical elements in machine instruction|typical elements in machine instruction]]
- [[#5 instruction set design issues|5 instruction set design issues]]
- [[#IRA and packed decimal representation|IRA and packed decimal representation]]
- [[#arithmetic shift vs. logical shift|arithmetic shift vs. logical shift]]
- [[#why transfer of control instructions|why transfer of control instructions]]
- [[#big endian vs. little endian|big endian vs. little endian]]
- [[#postindexing vs. preindexing|postindexing vs. preindexing]]
- [[#consideration for usage of addressing bits of instruction|consideration for usage of addressing bits of instruction]]
- [[#pros and cons of variable-length instruction format|pros and cons of variable-length instruction format]]
- [[#location of operand for different addressing mode|location of operand for different addressing mode]]
- [[#relative addressing mode|relative addressing mode]]
- [[#how to address main memory without indirect addressing|how to address main memory without indirect addressing]]
- [[#2 roles of processor registers|2 roles of processor registers]]
- [[#function of condition code|function of condition code]]
- [[#why 2-stage pipelining can't reduce instruction cycle time to 0.5|why 2-stage pipelining can't reduce instruction cycle time to 0.5]]
- [[#how instruction pipeline deal with conditional branch instructions|how instruction pipeline deal with conditional branch instructions]]
- [[#preemptive scheduling vs. non-preemptive scheduling|preemptive scheduling vs. non-preemptive scheduling]]
- [[#deadlock vs. starvation|deadlock vs. starvation]]
- [[#"if schedulable" calculation|"if schedulable" calculation]]
- [[#essential characteristic of the superscalar approach to processor design|essential characteristic of the superscalar approach to processor design]]
- [[#difference between superpipelining and superscalar|difference between superpipelining and superscalar]]
- [[#dependencies and conflicts|dependencies and conflicts]]
- [[#key elements of a superscalar processor organization|key elements of a superscalar processor organization]]
- [[#3 types of computer system organization|3 types of computer system organization]]
- [[#characteristics of an symmetric multiprocessor (SMP)|characteristics of an symmetric multiprocessor (SMP)]]
- [[#advantages of an SMP over uniprocessor|advantages of an SMP over uniprocessor]]
- [[#key OS design issues for an SMP|key OS design issues for an SMP]]
- [[#difference between software and hardware cache coherent schemes|difference between software and hardware cache coherent schemes]]
- [[#differences among simple instruction pipelining, superscalar, and simultaneous multithreading (SMT)|differences among simple instruction pipelining, superscalar, and simultaneous multithreading (SMT)]]
- [[#examples of applications benefit from scaling throughput with number of cores|examples of applications benefit from scaling throughput with number of cores]]
- [[#main design variables in a multicore organization|main design variables in a multicore organization]]
- [[#advantages of a shared L2 cache among cores compared to separate dedicated L2 caches for each core|advantages of a shared L2 cache among cores compared to separate dedicated L2 caches for each core]]


### computer architecture vs. computer organization
- *computer architecture*: <font color="#00b0f0">attributes</font> of system <font color="#00b0f0">visible</font> to a programmer that have a <font color="#00b0f0">direct impact</font> on logical <font color="#00b0f0">execution</font> of program
	- example: instruction set, number of bits of data types, I/O mechanism, addressing memory techniques
- *computer organization*: <font color="#00b0f0">operational units</font> and their <font color="#00b0f0">interconnections</font> that realize the architectural <font color="#00b0f0">specifications</font>.
	- example: control signals, interfaces between computer and users, memory technology used

### computer structure vs. computer function
- *computer structure*: the way computer components are interrelated
- *computer function*: operation of individual component

### structural component of computer
- *CPU*: control operation of computer and process data
- *main memory*
- *I/O*: transfer data between computer and external environment
- *system interconnection*: mechanisms that provide communication among components (bus)

### structural component of processor
- *control unit*: control operation
- *arithmetic and logic unit (ALU)*: process data
- *register*: internal storage
- *CPU interconnection*: communication mechanism

### definition of embedded system
- a <font color="#00b0f0">device</font> tightly coupled computing <font color="#00b0f0">hardware</font> and <font color="#00b0f0">software</font> that are <font color="#00b0f0">designed</font> to perform a <font color="#00b0f0">dedicated function</font>
- characteristic
	- encapsulated by the device it controls
	- hidden from view
	- usually as a sub-system within a larger system
	- multiple embedded system can coexist in a system
- examples: washing machine, TV, phone

### main considerations for designing an embedded system
- *environmental*: size, power, weight, radiation
- *performance*: responsive, predictability
- *economic*: cost, time-to-market
- *consequential*: safety, reliability, security

### definition of real-time system
- a system that responds within specified times. (not necessary fast, but must meet timing deadline)

### 2 types of real-time system
- *hard real-time system*
	- fail to meet deadline will cause fatal flaw/consequences
	- many are safety critical
	- require a means for validating deadlines are always met
- *soft real-time system*
	- timely completion desire
	- fail to meet deadline will cause performance degradation

### categories of real-time application
- *purely cyclic*: periodically execute every task, resources required won't vary significantly <font color="#a5a5a5">(example: digital controller)</font>
- *mostly cyclic*: most tasks execute periodically, and system must respond to external events asynchronously <font color="#a5a5a5">(example: process control system)</font>
- *asynchronous: mostly predictable*: most tasks are NOT periodic, variation of 1) execution interval; 2) resource utilization is large, BUT variation is bounded or known statistics
- *asynchronous unpredictable*: application react to asynchronous events and have tasks with high run-time complexity <font color="#a5a5a5">(example: intelligent real-time control system)</font>

### techniques for processors to increase speed
- *pipelining*: execution of instruction involve multiple stage of operation
- *branch prediction*: looks ahead in the instruction code fetched from memory and predict which branches are likely to be processed next
- *superscalar execution*: issue more than one instruction in every clock cycle
- *data flow analysis*: processor analyze the interdependence among data/result to optimize schedule of instructions
- *speculative execution*: processors speculatively execute instructions ahead of their actual appearance in the program execution, holding the results temporaryly

### multicore systems, MICs, and GPGPUs
- *multicore*: use multiple processing units (cores) on a single chip
- *many integrated core (MIC)*: chip containing a larger number of cores
- *general-purpose computing on GPUs (GPGPU)*: GPU designed to support a broad range of application

### desirable characteristic of benchmark program
- written in high-level language (portable)
- representative of particular kind of programming domain or paradigm
- can be measured easily
- wide distribution

### 4 types of functions specified by instructions
- *processor-memory*: data transmission between processor and memory
- *processor-I/O*: data transmission between processor and I/O modules
- *data processing*: perform arithmetic or logic operation on data
- *control*: instruction may specify the change of execution sequence

### possible states that define an instruction execution
- *instruction address calculation (IAC)*: determine address of next instruction
- *instruction fetch (IF)*: read instruction from memory into processor
- *instruction operation decoding (IOD)*: analyze instruction to determine type of operation to be performed and operands to be used
- *operand address calculation (OAC)*: if operation involves reference to an operand in memory or available via I/O, then determine the address of operand
- *operand fetch (OF)*: fetch operand from memory or I/O
- *data operation (DO)*
- *operand store (OS)*: write the result into memory or I/O

### layers in QPI
- *physical layer*: actual wires carrying signals and circuitry supporting ancillary features required in transmission and reception
- *link layer*: responsible for reliable transmission and flow control
- *routing layer*: provides framework for directing packets through fabric
- *protocol layer*: high-level rules for exchanging packets of data between devices

### layers in PCIe
- *physical layer*: <font color="#bfbfbf">(same)</font> actual wires carrying signals and circuitry supporting ancillary features required in transmission and reception
- *data link layer*: responsible for reliable transmission and flow control
- *transaction layer*: 1) generate and consume data packets to implement load/store data transfer mechanisms; 2) manage flow control of packets between two components on a link

### influence of width of data bus and address bus
- width of *data bus*
	- if width < instruction length: require more clock cycles to fetch instruction
- width of *address bus*
	- if width < address length: can't access whole memory, more complex memory interface control is required. (for example: first half as "row" and second half as "column")

### width of program counter register and instruction register
- *program counter*: $\gt$ (width of instruction - length of opcode)
- *instruction register*: 1) contain entire instruction: as long as instruction; 2) only contain opcode: as long as opcode

### improve data transfer performance by: 2x clock frequency vs. 2x data bus width
- *2x clock frequency*: new chip manufacturing technology, also need to double speed of memory chip
- *2x data bus width*: need modification to bus control logic, also word length of memory

### sequential access vs. direct access vs. random access
- *sequential access*: memory organized into units of data (records). access must be made in specific linear sequence
- *direct access*: individual record has a unique address based on physical location. access is accomplished by direct access to reach a vicinity (nearby) then sequential searching | counting | wait to reach final location
- *random access*: individual addressable location in memory has uniquely, physically wired-in addressing mechanism. time to access is constant, independent of sequence of prior accesses

### direct mapping vs. associate mapping vs. set-associate mapping
- *direct*: each block of main memory ➡ one possible cache line
- *associate*: each block ➡ any line of cache
- *set-associate*: cache divided into sets, each memory block ➡ any line in a particular set

### why need to store tag in cache
- two items with two different memory addresses can be stored in the same place in the cache. tag can distinguish them

### 3 types of external devices
- *human readable*: computer & user
- *machine readable*: computer & equipment
- *communication*: computer & remote devices

### 3 techniques for I/O
- *programmed I/O*: processor issues an I/O command as a process to an I/O module, then the process then busy-waits for operation to be completed before proceeding
- *interrupt-driven I/O*: processor issues an I/O command on behalf of a process, continues to execute subsequent instructions, and is interrupted by the I/O module when the latter has completed its work (processor doesn't wait for the completion of I/O)
- *direct memory access (DMA)*: controls exchange of data between main memory and I/O (processor sends request for transfer data to DMA module, then interrupted only after entire block transferred)

### memory-mapped I/O vs. isolated I/O
- *memory-mapped I/O*: single address space for memory locations and I/O devices (share space, treat I/O as the same as memory: instruction/location)
- *isolated I/O*: command specifies address refer to memory or I/O. (I/O has separate space & command)

### 4 types of techniques to determine which device issue interrupt
- multiple interrupt lines
- software poll
- daisy chain (hardware poll)
- bus arbitration

### ports for I/O device
- normal devices need 2 ports: 1) output port for command 2) input port for status
- status line: output line of I/O
- control line: input line of I/O ( = number of address to control device)

### definition of OS
- operating system is the software that controls the execution of programs on a processor that manages the processor's resources

### key services provided by an OS
- *program creation*
- *program execution*: require tasks like loading instruction and data, initializing I/O and files, preparing resources
- *access to I/O devices*: each I/O device require its own set of instructions or control signals for operation
- *controlled access to files*: know nature of I/O device and file format
- *system access*: control access to system
- *error detection and response*
- *accounting*: collect usage statistics and monitor performance

### difference between a process and a program
- <font color="#f79646">process</font> is a <font color="#00b0f0">program</font> in execution, together with all the state information required for execution

### typical elements in machine instruction
- *opcode*: specify operation
- *source and destination references*: input/output locations for operation

### 5 instruction set design issues
- *operation repertoire*: number, types and complexity of operations
- *data types*
- *instruction format*
- *registers*
- *addressing*

### IRA and packed decimal representation
- *International Reference Alphabet (IRA)*: 011xxxx, digits 0 through 9 are represented by their binary equivalents, 0000 through 1001, in the right-most 4 bits (same as *packed decimal*)

### arithmetic shift vs. logical shift
- *logical*: one end bits shifted out is lost, padding the other end with 0
- *arithmetic*: doesn't shift sign bit. 1) right shift: copy sign bit into bit position to its right; 2) left shift: sign bit retains, others the same as logical shift

### why transfer of control instructions
- *transfer of control instructions*: use to change the sequence of execution of a program by transferring control to another part of program
- why
	- some instructions need to be executed repeatedly, and it's not feasible to write each of them out separately. With transfer of control instruction, a program can specify a loop to execute a sequence of instruction repeatedly.
	- execute instruction based on conditions
	- help to break task up into small pieces that can be worked on parallelly

### big endian vs. little endian
- *little endian*: most significant byte/bit stores in the highest address
- *big endian*: opposite

### postindexing vs. preindexing
- *postindexing*: 1) base register value used to access memory location; 2) offset added to base register value
- *preindexing*: 1) offset added to base register; 2) address memory location

### consideration for usage of addressing bits of instruction
- *number of addressing mode*: can be indicated explicitly/implicitly
- *number of operand*
- *register vs. memory*
- *number of register set*: functional split of registers can reduce number of bits used in instruction
- *addressing range*: 1) direct addressing: # of address bits limit range; 2) displacement addressing
- *address granularity*: byte addressing or word addressing

### pros and cons of variable-length instruction format
- pros: 1) easy to provide more opcodes with different opcode length; 2) addressing is more flexible (various combinations of register and memory & addressing modes)
- cons: increase complexity of CPU

### location of operand for different addressing mode
(address field value $V$)
- *immediate addressing*: operand = $V$
- *direct addressing*: memory location $V$
- *indirect addressing*: memory location whose address is in memory location $V$
- *register addressing*: register $V$
- *register indirect addressing*: memory location whose address is in register $V$

### relative addressing mode
- commonly used in PC
- (Current PC Address + 1) + Relative Address = Effective Address

### how to address main memory without indirect addressing
- load address into register and use displacement addressing with displacement 0

### 2 roles of processor registers
- *User-visible registers*: enable assembly language programmer to minimize main-memory references by optimizing use of registers. 
- *Control and status registers*: These are used by the control unit to control the operation of the CPU and by privileged, operating system programs to control the execution of programs.

### function of condition code
- set by CPU hardware as result of operations. can be tested as part of conditional branch operation

### why 2-stage pipelining can't reduce instruction cycle time to 0.5
- execution time is usually longer than fetch time ➡ fetch stage has to wait for some time
- conditional branch instructions makes address of next instruction unknown ➡ fetch stage has to wait until next instruction address is calculated ➡ execute stage has to wait until instruction fetched

### how instruction pipeline deal with conditional branch instructions
- *multiple streams*: replicate the initial portions of the pipeline and allow the pipeline to fetch both instructions, making use of two streams (直接两个分支都先抓进来)
- *prefetch branch target*: prefetch target and the following instruction. So when branch instruction is executed, if branch is taken, target is prefetched (不管有没有分支先抓来)
- *loop buffer*: (definition: a small, very-high-speed memory maintained by the instruction fetch stage of the pipeline and containing the n most recently fetched instructions) if a branch is taken, hardware checks the buffer first and try to load from buffer
- *branch prediction*: predict whether conditional branch will be taken
- *delayed branch*: if rearranging instructions can improve performance, the branch will be delayed

### preemptive scheduling vs. non-preemptive scheduling
- *preemptive*: based on timer interrupts, where a running thread may be interrupted by OS and switched to ready state (if more important tasks come through) or when it exceeds its timing allocation
- *non-preemptive*: once the thread is in running state, it continues until it completes
- pros and cons: *non-preemptive* threads are likely to <font color="#00b0f0">monopolies</font> CPU, so it should not hold CPU unnecessarily so that every task can get their CPU time. Another issue is that non-preemptive scheduling can't guarantee response time of each thread. However, it can provide least contacting and switching time.

### deadlock vs. starvation
- *deadlock*: a number of processes all become blocked and can't proceed without a resource that another process holds, but all processes can't release any resource currently holding
- *starvation*: a process is never given required resource to proceed

### "if schedulable" calculation
- *earliest deadline first*: $U = \sum_{i=1}^{n} \dfrac{processing\:time_i}{period_i}$, if $U<1$ then it's scedulable

### essential characteristic of the superscalar approach to processor design
- multiple independent instruction pipelines are used. Each pipeline consists of multiple stages, so that each pipeline can handle multiple instructions at a time. Multiple pipelines introduce a new level of parallelism

### difference between superpipelining and superscalar
- *superpipelining*: exploit the fact that many pipeline stage perform tasks that require less than half a clock cycle. Thus, a doubled internal clock speed allows performance of two tasks in one external clock cycle
- *superscalar*: multiple pipelines

![[RTCSA notes-20231212-212.png|450]]

### dependencies and conflicts
- *true data dependency*: second instruction needs data produced by the first instruction
- *procedural dependency*: instructions following a branch (taken or not taken) have a procedural dependency on the branch and cannot execute until the branch is executed
- *resource conflict*: competition of two or more instructions for the same resource at the same time
- *output dependency*: two instructions update the same register, so they need to update the register in order
- *antidependency*: second instruction destroys the value that first instruction uses

### key elements of a superscalar processor organization
- *instruction fetch* strategies: often fetch beyond conditional branch instructions, require the use of multiple pipeline fetch, decode stage and branch prediction logic
- logic for determining true *dependencies* involving register values, and mechanisms for communicating these values
- mechanism for *initiating (issuing)* multiple instructions in paralllel
- *resources* for parallel execution of multiple instructions (functional units, memory hierarchies)
- mechanism for *committing* process state in correct order

### 3 types of computer system organization
- *single instruction, single data (SISD) stream*: single processor executes single instruction stream to operate data stored in single memory
- *single instruction, multiple data (SIMD) stream*: single instruction controls simultaneously execution of multiple processing elements. Each processing element has an associate data memory, so each instruction executed on a different set of data by different processors
- *multiple instruction, multiple data (MIMD) stream*: a set of processors simultaneously execute different instruction sequences on different data sets.

### characteristics of an symmetric multiprocessor (SMP)
- two or more similar processors of <font color="#00b0f0">comparable capability</font>
- processors <font color="#00b0f0">share same main memory</font> and I/O facilities and <font color="#00b0f0">interconnected</font> by a bus or internal connection scheme such that memory access time is approximately the same for each processor
- all processors <font color="#00b0f0">share access to I/O devices</font>, with same/separate channels to same device
- all processors perform <font color="#00b0f0">same functions</font>
- system <font color="#00b0f0">controlled by integrated OS</font> that provides interaction between processors and their programs

### advantages of an SMP over uniprocessor
- *performance*: some part of the program can be organized to be executed in parallel, then SMP will yield greater performance
- *availability*: failure of single processor will not halt the machine
- *incremental growth*: performance of the system can be enhanced by adding an additional processor
- *scaling*: based on the number of processor, vendor can offer a range of products

### key OS design issues for an SMP
- *simultaneously concurrent process*: OS should allow processors to execute same IS code simultaneously. OS tables and management must be managed properly to avoid deadlock or invalid operations
- *scheduling*: avoid conflict, scheduler should assign "ready" process to available processors
- *synchronization*: due to potential access to shared address spaces | I/O, synchronization should enforces mutual exclusion and event ordering
- *memory management*: should deal with issues on uniprocessor, as well as exploit available hardware parallelism
- *reliability and fault tolerance*: OS should provide graceful degradation facing processor failure, and recognize the loss of processor, restructuring management table accordingly

### difference between software and hardware cache coherent schemes
- *software*: attempt to avoid need for additional hardware circuitry and logic by compiler and operating system
- *hardware*: implemented in hardware

### differences among simple instruction pipelining, superscalar, and simultaneous multithreading (SMT)
- *pipelining*: instructions are executed through a pipeline of stages. One instruction ➡ one stage, another instruction is executing in another stage of pipeline
- *superscalar*: <font color="#00b0f0">multiple pipelines</font> are constructed, enable parallel execution of instructions in parallel pipelines
- *simultaneously multithreading*: register banks are replicated so that multiple threads can <font color="#00b0f0">share</font> the use of <font color="#00b0f0">pipeline resources</font>

### examples of applications benefit from scaling throughput with number of cores
- *multi-thread native applications*: (multi-thread application: small number of highly threaded processes)
- *multi-process application*: presence of many single-threaded processes
- *Java applications*
- *multi-instance applications*

### main design variables in a multicore organization
- number of processors on chip
- number of levels of cache memory
- amount of cache memory shared

### advantages of a shared L2 cache among cores compared to separate dedicated L2 caches for each core
- reduce overall miss rates
- data shared by multiple cores is not replicated at the shared cache level
- amount of shared cache can be allocated dynamically
- easy to implement interprocessor communication
- use of shared L2 confines cache coherency problem to L1 cache, providing additional performance advantage
