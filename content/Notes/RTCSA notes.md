---
title: RTCSA notes
date: 2023-12-11
draft: false
author: HNO3
---

# Lectures

## Lecture 1 Real-time System

- software
	- system program
		- software that interfaces with the hardware
		- example: drivers, interrupt handlers, task schedulers, compilers, assemblers, linkers, locators
		- operating system: specialized collection of system programs that manage physical resources of computer
	- application programs
		- programmed to solve specific problems
- system
	- mapping of a set of inputs into a set of outputs
	- input & output
		- input: associated with sensors, convert analog signals into digital signals
		- output: converted to analog to control external hardware devices
	- ![[Pasted image 20231203212129.png]]
- definition of real-time system
	- a system that responds within specified times. (Not necessarily fast – must meet timing deadline)
- response time
	- time between the presentation of a set of inputs to a system and the realisation of the required behaviour
	- how fast? depends on specific system's characteristic and purpose
- real-time computing
	- study of system subjected to a "real-time constraint" (deadline)
	- logical correctness is based on both the correctness of the **outputs** and their **timeliness**
- failed system
	- cannot satisfy one or more of the requirements
- embedded system
	- perform dedicated functions, often with real-time computing constraints
	- system has a central role in the functionality of the system, but the system is not explicitly called a computer
	- hardware tightly coupled and software integrated that designed to dedicated function
	- embedded into a larger product, often hidden from view
	- encapsulated by the device it controls
	- can be sub-system within a larger system
	- one can have multiple embedded system coexist
- firmware
	- program instructions written for embedded systems
	- stored in read-only memory or Flash memory chips
	-  run with limited hardware resources
- reactive system
	- task scheduling is driven by ongoing interaction with their environment
- main requirement of an embedded system
	- environmental
	- performance
	- economic
	- consequential

### types of real-time system
1. *soft real-time system*
	1. performance is **degraded** but **not destroyed** by failure to meet response-time constraints
2. *firm real-time system*
	1. a few missed deadlines will not lead to total failure, but missing more than a few may lead to complete system failure
3. *hard real-time system*
	1. failure to meet even a single deadline may lead to complete system failure

### real-time punctuality
- cost-effective and robust real-time systems
	- process everything as slow as possible
	- repeat as less as possible
- real-time punctuality
	- response time has average $t_R$ and upper bound & lower bound $\varepsilon_{\mathrm{U}}$ and $\varepsilon_L$

### CPU Utilization Factor (U)
- or called time-loading factor, a relative measure of non-idle processing taking place
	- time-overloaded: U>100%
	- too tightly utilized: changes/addition/correction cannot be made
	- not sufficiently utilized: not cost-effective
- 50%: common for new product
- 80%: acceptable for system without growth
- 70%: best!
- <span style="background:rgba(3, 135, 102, 0.2)">how to calculate</span>
	- $$ u_i=e_i/p_i$$
	  $$U = \sum u_i$$
	  $e_i$: execution time, $p_i$: execution period
- Event & Release time
	- event: occurrence that causes program to change non-sequentially
	- release time: time at which an instance of scheduled task is ready to run and is generally associated with an interrupt
- Synchronous vs Asynchronous Events
	- synchronous: occur at predictable times in the flow-of-control
	- asynchronous: occur at unpredictable points in the flow-of- control and are usually caused by <font color="#0070c0">external sources</font>
- Deterministic System
	- each possible state and input will result in the same output
	- event determinism: next state and output of system are known for each set of input and events

## Lecture 2 Computer Number System

### binary digital system
- motivation
	- world analog
	- need to quantify, but not infinite precision
- binary data used to represent
	- number
	- character
	- instruction
	- logical
- radix system (base)
	- radix or base: defines a set of symbols used to represent number
	- radix point: reference point that determine the value of each digit
- Radix Representation
	- number: $d_{31}...d_1d_{0}$
	- value: ($d_{31}\times B^{31}+...+d_0 \times B^{0}$)
- conversions
	- binary to hex: 1 hex digit = 4 bits binary
	- ![[Pasted image 20231204151342.png]]
- interpretations of binary number
	- <font color="#0070c0">signed vs. unsigned</font>
	- *unsigned*
		- N-bit unsigned integer: range $(0,2^N-1)_{10}$
	- *signed*
		- N-bit signed integer: range $(-2^{N-1},2^{N-1}-1)$
	- sign and magnitude
		- <font color="#0070c0">two's complement</font> to represent a negative number
			1. invert digits (+28 = 00011100, invert: 11100011)
			2. add one to the result (11100011 + 1 = 11100100 = -28)
	- representation width
		- make sure to pad the original value to full representation width

### Floating point number
- motivation: <font color="#0070c0">relative accuracy</font> is needed
- how does this work?
	- <font color="#00b050">signifcand</font>: contains number's digits, if negative: negative number
	- <font color="#00b050">exponent</font>: where the decimal or binary point is placed relative to the beginning of the sinificand

| signifcand | exponent | scientific notation | fixed-point value |
| ----------- | -------- | ------------------- | ----------------- |
| 1.5         | 4        | $1.5\times 10^4$    | 15000             |

- IEEE-754 Standard Floating Point
	- structure: (MSB) {<font color="#d99694">sign-bit</font> (1)}-{<font color="#fbd5b5">exponent</font> (8)}-{<font color="#92cddc">significand</font> (23)} (LSB)
	- ![[Pasted image 20231204153600.png]]
	- exponent: in bias -127 integer format (add 127 to it)
	- signifcand: only fractional part of the mantissa, MSB of mantissa is always 1 and not stored
	- example
		- -88 = $-2.75\times 2^5$, $2.75 = (10.11)_2 = (1.011)_2 \times 2$
		- exponent part: <font color="#fac08f">6 (00000110) +127 (01111111) = 1000 0101</font>
		- significand:<font color="#92cddc"> 0110 0000 0000 0000 0000 000</font>
		- sign: <font color="#d99694">1</font>
- IEEE-754 Double Precision Format
	- structure: (MSB) {<span style="background:rgba(240, 107, 5, 0.2)">sign-bit (1)</span>}-{<span style="background:rgba(240, 200, 0, 0.2)">exponent (11)</span>}-{<span style="background:rgba(5, 117, 197, 0.2)">significand (52)</span>}
	- exponent: in bias -1023 integer format (add 1023 to it)
	- signifcand: only fractional part of mantissa, MSB is always 1 and not stored.
- comparison of fixed & floating point
	- floating point
		- pro: large dynamic range, resolution determined by sinificand
		- con: implementation slow
	- fixed point
		- pro: implementation fast
		- con: limited range and resolution

### other representation
- character
	- ACSII code, 8-bit byte represent character
- character / string in C
	- how to represent a variable length string: use <font color="#0070c0">'\0' to mark ending</font>
- gray code
	- a binary numbering system
	- characteristic: two successive values differ by 1 bit

## Lecture 3 Performance

### measure performance
- <span style="background:rgba(5, 117, 197, 0.2)">system clock</span>
	- operations of processors are governed by system block
	- <font color="#0070c0">speed of processor</font> is dictated by <font color="#0070c0">pulse frequency</font>, unit: cycles per second or Hz
	- clock signal generated by <font color="#0070c0">quartz crystal</font>, which generates a constant sine wave, converted into a digital voltage pulse stream
	- rate of pulses: <font color="#0070c0">clock rate</font> or <font color="#0070c0">clock speed</font>
		- clock rate is determined by the physical layout of the processor
	- operations are <font color="#d99694">synchronized</font> and <font color="#d99694">paced</font> so that proper signal values are available for each operation
	- most instructions require multiple clock cycles to complete
	- <font color="#d99694">pipelining</font>: multiple instructions executed simultaneously
	- direct comparison of system clock frequency will not show the performance.
- <span style="background:rgba(5, 117, 197, 0.2)">cycles per instruction (CPI)</span>
	- $$ \tau=1/f$$
	  f: constant frequency, $\tau$: constant cycle time
	- instruction count $I_c$ : number of machine instruction executed for that program until it runs completion
	- CPI: average cycles per instruction
		- all instruction require same amount of clock cycles: CPI will be constant
		- $CPI_i$ : number of cycles required for instruction type i
		  $I_i$: number of executed
		- $CPI=\frac{\sum_{i=1}^n(CPI_i\times I_i)}{I_c}$
		- processor time $T = I_C \times CPI \times \tau$
		- refine $T$: some time is used during execution, some is used to transfer data from memory (determined by <font color="#d99694">memory time</font>)
			- $T = I_C \times [p + (m\times k)]\times \tau$
			- p: number of processor cycles
			- m: number of memory references
			- k: ratio between memory cycle time and processor cycle time
		- factors that influences T
			- instruction set design
			- compiler technology (if the compiler is effective enough to convert efficient machine language from a high-level program)
			- processor implementation
			- cache and memory hierarchy
		- ![[Pasted image 20231204163225.png|475]]
- <span style="background:rgba(5, 117, 197, 0.2)">Millions of Instructions per Second (MIPS)</span>
	- $$ \text{MIPS rate}=\frac{I_c}{T\times10^6}=\frac{f}{CPI\times10^6}$$

## Lecture 4 Overview of an Operating System (OS)

### what is OS
- definition: program that <font color="#d99694">manages</font> all the other programs in a computer
	- other programs called applications
	- applications request for services through application program interface (<font color="#953734">API</font>)
- OS performs as <font color="#953734">environmental architecture</font>
	- for efficient usage
	- act as control program
- ![[Pasted image 20231204170452.png]]
- services of OS
	1. multitasking
	2. manage memory sharing
	3. handle input and output
	4. send message
	5. offload batch job
	6. provide parallel processing
- OS provides abstraction of hardware
	- allow users to program without knowledge of hardware
- OS resources management
	- process management
	- memory management
	- time & space multiplexing

### OS component
- Process management
	- applications
	- allocate independent memory space for each process
	- creation and destruction of processes
	- schedule process according to their deadline, priority, sequence...
	- maintain communication of process
	- maintain concurrency of process
- Memory management
	- support multiprogramming
	- sharing data between processes
	- virtual memory: use secondary memory (RAM) as cache
- File system
	- abstraction of a bulk of information
- I/O
	- requires device specific knowledge
- Network
- Security
- GUI

### Operating System Structure
- monolithic
	- ![[Pasted image 20231204172045.png]]
	- single program includes all kernel code and offers all os services
	- system calls
	- fast and efficient
	- less portable, difficult to maintain
	- minor bug can crash whole system
	- traditional (Unix, Linux)
- microkernel
	- ![[Pasted image 20231204172231.png]]
	- simplify kernel design
	- user-space servers
	- rapid deployment, unit testing, easy maintenance
	- huge memory footprint
	- frequent context switching, and high inter-process communication
	- not easy to implement
- monolithic vs. microkernel
	- monolithic has better performance
	- microkernel has better modularity and extensibility
	- <font color="#953734">modern OS</font> adopt <font color="#953734">hybrid</font> approach

### Types of OS
- Network OS
	- for computer network
	- allow facilities file sharing and hardware access
	- more communication features compared with single computer OS
- Distributed Operating System
	- microkernel plus service component that coordinates with other nodes
	- work collectively to fulfil all system resources
	- single node has full access to all system resources
		- complicated scheduling and parallelism
		- user not aware of which node is executing
- RTOS
	- dedicated to meet specific timing constraints
	- key design requirement
		- predictability and determinism
		- speed (by simplified OS design)
		- responsiveness and user control
		- fail-safety
	- require advanced scheduling and memory allocation
	- vs. embedded OS (EOS)
		- interchangable in this course
	- RTOS on embedded system vs. Super Loop
		- Super loop: straightforward to implement, fit computational model of Embedded system
			- depends on lengthy interrupt service routine
			- needs to synchronization between interrupt service routine (ISR)
			- poor predictability
			- change of ISR will result in change of the whole system
		- RTOS
			- better program flow
			- multitasking
			- better communication and resource management

### processes
- process has:
	- CPU time allocation
	- memory
	- process ID
	- threads
- process can be aware of each other
- memory layout of an program
	- <span style="background:rgba(5, 117, 197, 0.2)">{stack}</span> -> <span style="background:rgba(163, 67, 31, 0.2)">{unused}</span> <- <span style="background:rgba(3, 135, 102, 0.2)">{heap}</span> <span style="background:rgba(240, 200, 0, 0.2)">{data (uninitialized)} {data (initialized)}</span> <span style="background:rgba(240, 107, 5, 0.2)">{code / text}</span>
	- code / text
		- instruction
		- clone of program
		- read-only
		- program counter to the next instruction
	- static data
		- variables shared between threads
		- if not initialized: 0 or Null
	- heap
		- malloc/free
	- stack
		- used for procedure call for return
		- stack pointer
			- FILO
- abstraction of process
	- switch execution needs to keep <span style="background:rgba(163, 67, 31, 0.2)">context</span>
		- memory state
		- CPU state
		- OS state
	- <font color="#953734">program</font>: instructions stored on the disk
	- <font color="#953734">process</font>: program with execution context
	- <font color="#953734">thread</font>: lightweight process, a process can have multiple threads
- process control block (PCB) or Task Control Block (TCB)
	- contains all relevant information for the process
		- ID
		- state
		- registers
		- scheduling information
		- memory management information
		- accounting information
		- user information
- process creation
	- 3 ways
		- initialization
		- request of process
		- request of users
	- generate unique ID
	- allocate memory
	- initialize PCB and memory management
	- link PCB in the queue
- process termination
	- stopped by OS/users or terminate itself
	- handle the output
	- release resources and reclaim the memory
	- unlink PCB
	- many embedded software never terminate
- context switching
	- PCB makes this easier
		- scheduler will start/stop process accordingly
		- stores info to start/stop
			- register
			- program counter
			- memory state/stack/heap
			- state
		- load info from the PCB
	- context switching will consume time
		- can up to thousand CPU cycles
		- overhead and bottleneck
		- need hardware support
	- multiprogramming
- process state
	- standard model has 5 states
		1. *new*: just created, not ready for queue
		2. *ready*: can be loaded by OS
		3. *running*: scheduler picked this process from queue and executed it
		4. *blocked*: not in the queue, waiting
		5. *exit*: finished, needs to terminate
	- state information also recorded by PCB
	- context switching needed when processes leave/enter the running state
	- state transition may voluntarily (terminate) or involuntarily (error)
	- OS maintains queue or queue-like structure for process in the same state
- state transition
	- ![[Pasted image 20231205110136.png]]
	- *admit*: process is fully loaded into memory and control established
	- *dispatch*: scheduler begin to assign CPU to process
	- *time out*: expired/preempted, push back to queue
	- *event occur/wait*: request cannot be met now, has to wait until something occurs
		- why
			- OS not ready for survice
			- unavailable resources
			- wait for input
	- *release*: release resources and end the process


## Lecture 5 Computer Components and Function

### computer components
- von Neumann architecture
	- ![[Pasted image 20231205111335.png|325]]
	- data & instruction
		- stored in read-write memory
	- memory
		- addressable by location
	- execution
		- sequential fashion
- hardwired & micro-programmed
	- hardwired
		- fixed set of logic gates and circuit to execute instructions
		- control signals are *hardwired* into control unit, control unit has dedicated circuit for each possible instruction
		- simple and fast, inflexible
	- micro-programmed
		- control unit uses microcode to execute instructions
		- microcode: a set of instructions that can be modified/updated, allowing for greater flexibility
		- control signals for each instruction are generated by a micro-program stored in the memory
- hardware program
	- connect various components in the desired configuration
	- "program" is in the form of hardware
	- accept data and produce result
- software program
	- accept data and control signals then produce results
	- each step needs different set of control signals
- software
	- motivation
		- change/control through programming is easier than rewiring hardware
	- code is instructions, and hardware interpret each instruction to generate control signals
	- software = a sequence of codes/instructions
- programming in software
	- two major components of the system and constitute CPU
		- instruction interpreter
		- general-purpose arithmetic and logic functions
	- I/O components
		- input module
			- accept data and instructions
			- convert into internal form of signals
		- output module
			- report results
- computer components from top level view
	- ![[Pasted image 20231205141126.png]]
	- memory module: consist a set of locations, defined by sequentially numbered addresses
		- each location contains binary number that can be interpreted as data/instruction
	- I/O module: transfer data from/to external devices to CPU and memory
		- contains internal buffers for temporarily holding these data

### major components
- CPU
	- interpret instruction
	- arithmetic and logic functions
- I/O components
	- input module
		- accept data/instruction and convert into internal form of signals
	- output module
		- report results
- memory
	- definition: place to store temporarily both instruction and data
	- memory address register (MAR)
		- specify address in memory for the next read/write
	- memory buffer register (MBR)
		- contain data to be written into memory or receive data read from memory
	- I/O address register (I/O AR)
		- specify particular I/O device
	- I/O buffer register (I/O BR)
		- exchange data between I/O and CPU
- basic instruction cycle
	- processor does actual work by executing instructions specified in the program
	- two steps of instruction processing
		- ![[Pasted image 20231205142243.png]]
		1. read (fetch) instructions from memory
			- <font color="#548dd4">program counter (PC)</font> holds address of instruction to be fetched next
			- processor increments PC after fetch
			- fetched instruction loaded into <font color="#548dd4">instruction register (IR)</font>
		2. execute
			- categories of actions
				- processor-memory
					- transfer data between processor and memory
				- processor-I/O
					- transfer data between processor and I/O
				- data processing
					- perform arithmetic or logic operation on data
				- control
					- alter the sequence of execution
- Characteristics of a Hypothetical Machine
	- accumulator (AC): single data register
	- both instruction and data are 16-bit long, memory is then organized using 16-bit word
	- instruction format
		- <span style="background:rgba(240, 200, 0, 0.2)">{opcode (0-3)}</span> - <span style="background:rgba(5, 117, 197, 0.2)">{address (4-15)}</span>
	- example of program execution
		- ![[Pasted image 20231205143804.png|350]]
- ![[Pasted image 20231205143837.png]]
	- states
		- instruction address calculation (*IAC*): determine the address of next instruction to execute
		- instruction fetch (*IF*): read instruction from memory into processor
		- instruction operation decoding (*IOD*): analyze instruction to determine type of operation
		- operand address calculation (*OAC*): if involves reference ot operand in memory or I/O device, determine the address of operand
		- operand fetch (*OF*): fetch operand from memory or I/O
		- data operation (*DO*): perform operation indicated in the instruction
		- operand store (*OS*): write result into memory or I/O

### interrupt
- class of interrupts
	- definition: mechanism for other modules (I/O, memory) interrupt the normal processing of processors

| class of interrupts | description                                                                                                                    |
| ------------------- | ------------------------------------------------------------------------------------------------------------------------------ |
| program             | generated by some condition occurs as a result of instruction execution                                                        |
| timer               | generated by timer within processor, allow to perform functions in a regular basis                                             |
| I/O                 | generated by I/O controller, indicate completion of operation OR request service from processor OR variety of error conditions |
| hardware failure    | generated by failure                                                                                                                               |

- program timing
	- short I/O wait
		- ![[Pasted image 20231205144959.png|400]]
	- long I/O wait
		- ![[Pasted image 20231205145131.png|400]]
- transfer of control via interrupts
	- OS's responsibility to suspend the user program then resume it at the point interrupt is completed
- instruction cycle with interrupts
	- ![[Pasted image 20231205150656.png]]

## Lecture 6 Computer Interconnection

### Interconnect Structure
- 3 basic modules
	- processors
	- memory
	- I/O
- collection of paths for them to connect with each other: <font color="#0070c0">interconnection structure</font>
- memory interconnection
	- ![[Pasted image 20231206150727.png|425]]
	- a memory contains N words of equal length
	- each word has its own numerical address
- I/O interconnection
	- ![[Pasted image 20231206150920.png|425]]
	- each port represent an external device
- CPU interconnection
	- ![[Pasted image 20231206151202.png|425]]

### Types of Transfers
- memory to processor
	- processor reads an instruction or data from memory
- processor to memory
	- processor writes data to memory
- I/O to processor
	- processor reads data from I/O via I/O module
- processor to I/O
	- processor sends data to I/O device
- I/O to/from memory
	- I/O module is allowed to directly exchange data with memory (direct memory access)

### Bus Interconnection
- what is bus
	- communication pathway connect devices
	- signal transmitted by any device are available for reception
		- if transmit at the same time: garbled (overlap)
- system bus
	- bus connects major computer components
- bus interconnection
	- ![[Pasted image 20231206152556.png|500]]
	- three groups of buses
		- data
		- address
		- control
- operation of bus
	- <font color="#0070c0">send data</font>
		1. obtain use of bus
		2. transfer via bus
	- <font color="#0070c0">request data</font>
		1. obtain use of bus
		2. transfer request via control and address bus
- data bus
	- move data among system modules
	- number of lines referred to as the <span style="background:rgba(5, 117, 197, 0.2)">width</span> of data bus
	- width determines how many bits can be transferred at the same time
	- width is a key factor that determine the performance of the system
- address bus
	- designate the source/destination of data
	- width determines maximum possible capacity of the system
	- also used to address I/O ports
		- higher order bit: select module (memory or I/O)
		- lower order bit: memory location or I/O port
- control bus
	- control the access of and the use of data and address lines
		- why: data & address lines are shared by all components
	- information transmitted here:
		- command: specify the operation to be performed
		- timing: indicate validity of data

### Traditional Bus Architecture
- local bus
	- CPU - Cache
- system bus
	- memory - cache
- expansion bus
	- I/O modules - main memory





## Lecture 7 Interconnection and Communication

- On-chip protocols: communication protocols within a single integrated circuit (IC)
- Peripheral protocols: connect an IC to external devices
	- examples: I2C, SPI, and UART
- Serial vs Parallel Transmission
	- serial
		- sent bit by bit, each bit has a clock pulse rate
		- start & stop bit known as parity bit
	- parallel
		- bits transmit simultaneously with one clock pulse rate
		- use multiple lines to transmit
- Point-to-Point Interconnect
	- common: share bus architecture, but more point-to-point
	- reason for change: electrical constraints with increasing frequency of wide synchronous buses (difficult to perform the <font color="#548dd4">synchronization</font> and arbitration functions in a timely fashion)
	- advantages: lower <font color="#548dd4">latency</font>, higher <font color="#548dd4">data rate</font>, and better <font color="#548dd4">scalability</font>

### Quick Path Interconnect (QPI)
- a kind of <font color="#548dd4">point-to-point interconnection</font>
	- provide high bandwidth and low latency
- multicore configuration using QPI
	- Multiple direct connections
		- eliminate the need for arbitration found in the shared transmission system
	- Layered protocol architecture
		- take the place of simple use of control signals
	- Packetized data transfer
		- data sent as a sequence of packets (including headers & error control codes)
- QPI 4-Layer Protocol Architecture
	- *physical*: unit of transfer is 20 bits (Phit), actual wires carrying signals, circuitry and logic
		- 84 individual links
		- each data path consists of a pair of wires (lane)
		- 20 data lanes in each direction (tx & rx) + 1 clock lane in each direction
		- speed: 6.4GT/s (transfers/second), for 20-bits per transfer -> 16GB/s, due to bi-direction pairs -> 32GB/s
		- lanes are grouped into 4 quadrants, where each can operate independently
			- reduce power consumption
			- work around failure
		- <font color="#548dd4">multilane distribution</font>
			- physical layer manage translation between 80-bit flit and 20-bit phit by multilane distribution
			- ![[Pasted image 20231207212159.png]]
			- flit can be considered as bit stream across data lanes in round-robin fashion (shown in the figure)
	- *link*: reliable transmission and flow control. unit of transfer is 80 bit (Flit)
		- two key functions
			- flow control
				- ensure sending data not faster than the receiver can process data and clear buffer for more data
			- error control
				- detect and recover from bit error, therefore isolate higher layers from bit error
		- operate on the level of flit (flow control unit)
		- each flit consists 72-bit message and 8-bit error control code (cyclic redundancy check (CRC))
	- *routing*: framework for directing packets through fabric
		- determine the course that packet will traverse across the available system
		- defined by firmware and describe paths that packets can follow
	- *protocol*: high-level rules for exchanging packets of data between devices. A packet contains integral number of Flits.
		- packet defined as the unit of transfer
		- key function: cache coherency protocol (ensures main memory values in caches are consistent)
		- typical data packet payload: block of data sent to/from cache

### Peripheral Component Interconnection (PCI)
- PCI is local computer bus for attaching hardware devices to computer
- popular high bandwidth, processor independent bus functioned as peripheral bus
- better system performance for high speed I/O subsystems
- PCI Special Interest Group (SIG)
	- to develop further and maintain the compatibility of PCI specification
- PCI Express (PCIe)
	- point-to-point interconnect scheme
	- designed to replace older PCI-like bus standards
	- common interface for PC hardware connections
	- key requirement
		- high capacity to support the need of higher data rate I/O devices
		- support time-dependent data streams
	- PCIe Configuration
		- ![[Pasted image 20231207214655.png]]
		- *switch*: manage PCIe stream
		- *PCIe endpoint*: I/O device or controller
		- *Legacy endpoint*: for existing designs that have migrated to PCIe and allow legacy behaviors (use of I/O space, lock transactions, which PCIe endpoints are not permitted to)
		- *PCIe/PCI bridge*: allow older PCI devices to be connected to PCIe-based systems
	- PCIe Protocol Layers
		- *physical*: actual wires carrying signals
		- *data link*: transmission and flow control
			- data packets by data link layer (DLL) called Data Link Layer Packets (DLLPs)
		- *transaction*: generate and consume data packets used to implement load/store data transfer mechanisms & manage flow control of packets
			- data packets generated and consumed by TL are called Transaction Layer Packets (TLPs)
	- PCIe Multilane Distribution
		- ![[Pasted image 20231207215707.png]]
		- same round-robin scheme
		- at each physical lane, data buffered and processed 16 bytes (128 bits) at a time, each 128-bits encoded into 130-bit codeword for transmission (<font color="#548dd4">128b/130b encoding</font>), thus effective data rate reduced to $\cfrac{128}{130}$
	- PCIe Transmit and Receive
		- ![[Pasted image 20231208122407.png]]
		- At receiver, the clock is synchronized to the incoming data to recover the bit stream
	- PCIe Transaction Layer (TL)
		- receives write/read requests from the software above TL
		- create request packets for transmission via link layer
		- <font color="#548dd4">split transaction</font> technique
			- request packet sent by a source PCIe device, then waits for response called a completion packet
		- some are <font color="#548dd4">posted transactions</font> (no response expected)
		- TL packet format supports 32-bit memory addressing & 64-bit extended memory addressing
		- TL supports 4 address spaces
			1. memory
				- system main memory & PCIe I/O devices
				- certain ranges of memory addresses mapped into I/O devices
				- purpose: transfer data from/to in the system memory map
			2. configuration
				- enable TL to read/write configuration registers associated with I/O devices
				- purpose: transfer data to/from in the configuration space of a PCIe device
			3. I/O
				- used for legacy PCI devices
				- purpose: transfer data to/from in the system memory map for legacy devices
			4. message
				- used for control signals related to interrupts, error handling and power management
				- purpose: provide in-band messaging and event reporting

### Universal Asynchronous Receiver Transmitter (UART)
- definition
	- protocol for exchanging serial data between two devices
	- simple and use only two wires to transmit and receive in both directions
	- common ground connection
	- data in UART transmitted in the form of frames
	- ![[Pasted image 20231208123959.png]]
- communication modes
	- *simplex*: data sent in one direction only
	- *half-duplex*: data sent in both directions but one direction at a time
	- *full-duplex*: both directions can transmit simutaneously

### Inter-Integrated Circuit (I2C)
- I2C protocol
	- bus interface connection protocol incorporated into devices for serial communication
	- widely used for short distance communication
	- known as Two Wired Interface (TWI)
	- I2C uses only 2 bi-directional open-drain lines for data communication (SDA for data & SCL for clock signal), both are pulled high
- I2C communication mode
	- ideally: allow to connect 128 devices (saves PCB wiring)
	- master and slave send data at the same wire, controlled by master (device that send clock signal)
	- don't use separate Slave Select to select, but has address to identify slave devices

### Other Peripheral Interfaces

#### USB
- widely used, default interface for slower-speed devices
- controlled by a root host controller which attaches to devices to create local network with a hierarchical tree topology

#### FireWire Serial Bus
- alternative to small computer system interface (SCSI)
- objective: meet the increasing demand for high I/O rate while avoiding bulky and expensive I/O technologies designed for supercomputer
- use daisy chain configuration, one port can connect up to 63 devices
- characteristic: <font color="#548dd4">hot plugging</font>, automatic configuration, no terminations, automatically assign addresses

#### small computer system interface (SCSI)
- common standard for connecting peripheral devices to small/medium size computers
- lost popularity after USB and FireWire in small systems
- high-speed version still used in massive systems
- physical organization
	- shared bus: support up to 16 or 32 devices, parallel transmission, bus width 32 bits, speed up to 160Mbps

#### Thunderbolt
- fastest peripheral connection technology
- combines data, video, audio and power into a single high-speed connection
- 10 Gbps throughput in each direction, 10W power

#### InfiniBand
- aimed at high-end server
- standard described for data flow among processors and I/O devices
- popular interfaces for storage area
- enable server, remote storage and network devices attached in a central fabric of switches and links

#### SATA
- Serial Advanced Technology Attachment
- for disk storage systems
- 6 Gbps, 300Mbps per device

#### Ethernet
- networking technology
- 100 Gbps
- moved from bus-based to switch-based
	- a central switch with all of the devices connected directly to the switch

#### Wi-Fi
- wireless Internet access technology
- 9.6 Gbps (Wi-Fi 6 or 802.11ax)

## Lecture 8 Computer Memory Technologies

### key characteristic of memory
- location
	- internal
		- equated with main memory
			- processor requires its own local memory (<font color="#4f81bd">register</font>)
			- <font color="#4f81bd">cache</font> is another form of internal memory
	- external
		- peripheral storage devices
		- access to processor via I/O controllers
- capacity
	- number of bytes
	- number of words
	- word length
		- 8/16/32 bits
- unit of transfer
	- for internal: unit of transfer = number of electrical lines in/out of memory module
	- may equal word length, often larger than word length (64/128/256 bits)
	- three concepts of internal memory
		- word: natural unit of organization of memory, usually
		  = number of bits used to represent integer
		  = instruction length
		- addressable units: some = word, while some allow addressing at byte level
			- $2A=N$, where $A$ is length in bits, $N$ is number of addressable units
		- unit of transfer: number of bits read out of or written into memory at a time, need NOT equal to word/addressable unit
	- block
		- data are often transferred in larger unit for external memory, referred to as blocks
- access method
	- sequential
		- memory organized into units of data called records
		- access must be made in linear sequence
		- access time is variable
	- direct 
		- involved a shared read-write mechanism
		- individual blocks/records have unique address based on physical location
		- access time is variable
	- random
		- each location has unique, physical wired addressing mechanism
		- time to access is independent of sequence of prior address and it's <font color="#4f81bd">constant</font>
		- any location can be selected at random and directly addressed and accessed
		- used at <font color="#4f81bd">main memory</font> & some <font color="#4f81bd">cache systems</font>
	- associative
		- word is retrieved based on a portion of its content rather than address
		- each location has its own addressing mechanism and retrieval time is <font color="#4f81bd">constant</font>, independent of location or prior access patterns
		- used at some <font color="#4f81bd">cache memories</font>
- performance
	- access time (latency)
		- for random access: time it takes to read/write
		- for non-random access: time to position the read/write at the desired location
	- cycle time
		- defined as: access time + additional time required before second access can commence
			- additional time for: <font color="#0070c0">transients</font> to die out on signal lines; <font color="#0070c0">regenerate data</font> if read destructively
	- transfer time
		- defined as: rate at which data can be transferred into/out of memory unit
		- for random access: equal to $\dfrac{1}{cycle\:time}$
- physical type
	- semiconductor
		- can be either volatile or non-volatile
	- magnetic
		- non-volatile
	- optical
	- magneto-optical
- physical characteristic
	- volatile/non-volatile
		- volatile: information lost when switched off
		- non-volatile: once recorded, information maintains until deliberately changed
		- no electricity needed to retain information
	- erasable/non-erasable
		- non-erasable: can't altered, except destroying storage unit
			- ROM: read only memory, non-erasable semiconductor memory
- organization
	- memory modules

### memory hierarchy
- ![[Pasted image 20231210114007.png|575]]
- design constraints of memory around three questions
	- how fast (access time), how much (capacity), how expensive (cost)
- typical hierarchy
	- from up to down (processor register -> processor cache -> RAM -> USB/flash -> hard drives -> tape backup)
		- decreasing cost per bit (cheaper)
		- increasing capacity
		- increasing access time (slower)
		- decreasing the frequency of access of the memory by processor (less used)
- motivation
	- three levels exploits the fact that semiconductor memory comes in a variety of types which differ in speed and cost
	- Data are stored more permanently on external mass storage devices (<font color="#0070c0">secondary</font> memory or <font color="#0070c0">auxiliary</font> memory)
- disk cache
	- a portion of main memory used as buffer to hold data temporarily that read out of disk
	- large transfer of data can be used instead of small transfers of data
	- data can be retrieved faster from software cache rather than slowly from disk

## Lecture 9 Cache Memory

>[!info] Supplemental Information about Working Principle of Cache Memory
>
>before program execution:
>- firstly loaded the whole program into main memory
>- parts most likely to execute in the near future will be loaded to cache
>
>start
>1. CPU requires any word of the memory, firstly search the CPU register
>	1. found in register: read from register
>	2. not found: step 2
>2. search the cache memory (using Tag to search whether the required word is present in the cache or not)
>	1. found: **cache hit**, the word will be delivered to CPU
>	2. not found: step 3, **cache miss**
>3. search the required word in the main memory (using Page Table to determine whether the required page is present or not)
>	1. found: page will be mapped from main memory to cache memory (using cache mapping techniques), then delivered to CPU
>	2. not found: page fault occurs
>		1. page containing required word is mapped from secondary memory to the main memory
>		2. then mapped from main memory to cache memory
>		3. then required word delivered to CPU
> ![[Pasted image 20231210143941.png|475]]

- usage: temporarily store frequently used instructions/data for quicker processing by CPU
- cache is an extension of computer's main memory
- organization of cache
	- <span style="background:#d3f8b6">CPU</span> ➡ (*word* transfer) <span style="background:#b1ffff">Cache</span> ➡ (*block* transfer) <span style="background:#d2cbff">main memory</span>
	- if multiple levels of cache:
		- <span style="background:#d3f8b6">CPU</span> ➡ (fastest) <span style="background:#b1ffff"> L1 cache</span> ➡ (fast) <span style="background:#b1ffff">L2 cache</span> ➡ (less fast) <span style="background:#b1ffff">L3 cache</span> ➡ (slow) <span style="background:#d2cbff">main memory</span>

### elements of cache design

- cache address
	- (supplement concept) virtual memory
		- allow programs to address memory from <font color="#0070c0">logical</font> point of view, regardless of amount of main memory physically available
		- when used: address fields of machine instructions contain virtual addresses
		- when there is read/write operation: a hardware called <font color="#0070c0">memory management unit (MMU)</font>
	- logical
		- virtual cache, storing data using virtual address
		- processor access memory directly, without going through MMU
	- physical
		- physical cache stores data using main memory physical address
	- comparison between logical and physical
		- logical is faster (without translation of MMU)
		- logical: <span style="background:#d2cbff">CPU</span> ➡(logical address) <span style="background:#d3f8b6">cache</span> ➡ <span style="background:#d2cbff">CPU</span>
		- physical: <span style="background:#d2cbff">CPU</span> ➡ <span style="background:#fff88f">MMU</span> ➡ <span style="background:#d3f8b6">cache</span> ➡ <span style="background:#d2cbff">CPU</span>
- cache size
- mapping function ([more info found here](https://www.geeksforgeeks.org/cache-memory-in-computer-organization/))
	- (supplement knowledge) why we need this function?
		- fewer cache lines than main memory blocks, so we need to map main memory blocks into cache lines
	- direct
		- ![[Pasted image 20231210120709.png|450]]
		- simplest
		- assign each memory block to a specific line in the cache
		- address space is split into two parts index field and a tag field, <font color="#0070c0">cache</font> is used to <font color="#0070c0">store</font> the <font color="#0070c0">tag field</font> whereas the rest is stored in the main memory![[Pasted image 20231210124456.png|400]]
	- associate
		- ![[Pasted image 20231210120735.png|450]]
		- used to store the <font color="#0070c0">content & addresses</font> of the memory word
		- allow each memory block to be loaded into any line of cache
		- cache control logic interprets memory address simply as a Tag and Word field
		- to examine whether a block is in the cache, cache control logic must simultaneously examine every line's Tag for a match
	- set associate
		- compromise that exhibits the strengths of both the direct and associative approaches while reducing their disadvantages
- replacement algorithm
	- least recently used (LRU)
	- first in first out (FIFO)
	- least frequently used (LFU)
	- random
- write policy
	- write through
	- write back
- line size
	- retrieve from main memory to cache: at least a block, which contains desired word + some other adjacent words but not desired
	- block size increase ➡ at first the hit ratio will increase due to the <font color="#0070c0">principle of locality</font> (more useful data is brought into cache)
		- but as the block become bigger, <font color="#0070c0">probability</font> of using <font color="#0070c0">newly</font> fetched information becomes <font color="#0070c0">less</font> than the <font color="#0070c0">probability</font> of <font color="#0070c0">reusing</font> information to be replaced for new block (old information is more useful but be replaced!)
	- two effects of larger block
		- reduce number of blocks that fit into cache
		- each additional word is farther from the requested word
- number of cache
	- single or multi-level
		- <font color="#0070c0">on chip cache</font>: <font color="#0070c0">logic density</font> increases
			- reduce processors' external bus activity
			- speed up execution time
			- increase overall performance
		- two level cache
			- internal cache: L1
			- external cache: L2
			- potential savings due to L2 depends on <font color="#0070c0">hit rates</font> in both caches
				- total hit ratio![[Pasted image 20231210160107.png]]
				- L2 has no effect on cache hits until it's <font color="#0070c0">twice</font> of L1
					- why this make sense: if L2 size is equal to L1, basically L2 is the mirror of L1
			- multiple cache make design more complicated
	- unified or split
		- trend: split L1 but unify cache for higher levels
		- split cache for
			- one dedicated cache for <font color="#0070c0">instruction</font>
			- one dedicated cache for <font color="#0070c0">data</font>
			- both exist at the same level (L1)
		- advantage of split
			- Eliminates cache disagreement between instruction fetch/decode unit and execution unit
			- pipelining
		- advantage of unified cache
			- higher hit rate: balance load of instruction and data fetches automatically
			- only one cache needs to be designed and implemented

### mapping function
#### direct-mapping cache organization
![[Pasted image 20231210125901.png|550]]
![[Pasted image 20231210144203.png|425]]
In direct mapping [reference: cache mapping techniques](https://www.gatevidyalay.com/cache-mapping-cache-mapping-techniques/), and [reference: direct mapping](https://www.gatevidyalay.com/direct-mapping-cache-mapping/)
- no need of replacement algorithm
-  a main memory block can map ($j$) only to a particular line of the cache ($i=j\:mod\:n$ out of $n$ lines).
- new incoming block will always replace the existing block (if any) in that particular line
- division of physical address: <span style="background:rgba(240, 107, 5, 0.2)">{Tag}</span><span style="background:rgba(240, 200, 0, 0.2)">{Line Number}</span><span style="background:rgba(3, 135, 102, 0.2)">{Block/Line Offset}</span>, where <span style="background:rgba(240, 107, 5, 0.2)">Tag</span> + <span style="background:rgba(240, 200, 0, 0.2)">Line Number</span> = Block Number
- working procedure of direct mapping cache
	1. <span style="background:rgba(240, 200, 0, 0.2)">line number</span> field of the address is used to access the particular line of the cache
	2. <span style="background:rgba(240, 107, 5, 0.2)">tag</span> field of the CPU address is then compared with the <span style="background:rgba(240, 107, 5, 0.2)">tag</span> of the line
		1. <span style="background:rgba(240, 107, 5, 0.2)">tag</span> match: cache hit, desired word found in the cache
		2. <span style="background:rgba(240, 107, 5, 0.2)">tag</span> not match: cache miss, required word needs to be found in the main memory
- calculation
	- <span style="background:rgba(240, 107, 5, 0.2)">Tag (s-r bits)</span> <span style="background:rgba(240, 200, 0, 0.2)">Line Number (r bits)</span> <span style="background:rgba(3, 135, 102, 0.2)">word (w bits)</span>
	- address length: (s+w) bits
	- number of addressable units: $2^{s+w}$ words or bytes
	- block size = line size = $2^w$ words or bytes
	- number of blocks in main memory = $2^{s+w}/2^{w}=2^{s}$
	- number of lines in cache: $m=2^r$
	- size of tag = $(s-r)$ bits

#### Fully Associated Cache Organization
![[Pasted image 20231210150117.png]]
- any block of main memory can map to any line of the cache.
- Had all the cache lines been occupied, then one of the existing blocks will have to be replaced.
	- this is why we need replacement algorithm
- division of physical address: <span style="background:rgba(240, 107, 5, 0.2)">{Block Number / Tag (s)}</span><span style="background:rgba(3, 135, 102, 0.2)">{Block / Line Offset (w)}</span>
- calculation
	- address length: $(s+w)$ bits
	- number of addressable units: $2^{s+w}$ words or bytes
	- block size = line size = $2^w$ words or bytes
	- number of blocks in main memory = $2^s$
	- number of line in cache: undetermined
	- size of tag = $s$ bits

#### K-Set or v-way Set Associate Mapping
![[Pasted image 20231210151538.png|400]]
![[Pasted image 20231210151620.png]]
- cache contains $K$ sets
- each set has $v$ lines
- any given block can map to any line in a given set
- physical address division: <span style="background:rgba(240, 107, 5, 0.2)">{Tag (s-d)}</span> <span style="background:rgba(240, 200, 0, 0.2)">{Set (d)}</span> <span style="background:rgba(3, 135, 102, 0.2)">{Word (w)}</span>
- calculation
	- address length = $(s+w)$ bits
	- number of addressable units = $2^{s+w}$ words or bytes
	- block size = line size = $2^w$ words or bytes
	- number of blocks in main memory = $2^s$
	- number of lines in a set = $v$
	- number of sets: $K = 2^d$
	- number of lines in cache = $m=kv=k\times 2^d$
	- size of cache = $k\times 2^{d+w}$
	- size of tag = $(s-d)$ bits
- varying associativity over cache size
	- ![[Pasted image 20231210153206.png]]
	- cache size increase will improve performance until cache size reach 32 kB
	- change from <font color="#0070c0">direct</font> to <font color="#0070c0">2-way set associate</font> will significantly improve performance until cache size reach 64 kB
	- when cache size is between 4 kB and 8 kB, the improvement to use 4-way compared with 2-way is most significant

### replacement algorithms
- why we need
	- when cache has been all filled, when a new block is brought into the cache, one of the existing block should be replaced
- used for associative mapping
- algorithm is implemented in <font color="#0070c0">hardware</font> to achieve high speed
- LRU
	- most effective
	- replace block in the set that has been <font color="#0070c0">in the cache longest with no reference</font> to it
- FIFO
	- Replace that block in the set that has been in the cache <font color="#0070c0">longest</font>
	- easy to implement
- LFU
	- Replace that block in the set that has <font color="#0070c0">experienced the fewest references</font>
	- implemented by associating a counter with each line (counter for how many times each line is referenced)

### Write Policy
- consider two cases when a block in cache is to be replaced
	- old block had not been altered: may be overwritten with a new block without first writing out the block
	- at least one <font color="#0070c0">write</font> operation has been performed on a word in that line of the cache: main memory must be updated by writing the line of cache <font color="#0070c0">out</font> to the block of memory before bringing the new block
- two problems to contend
	- more than one device have access to main memory
	- more complex problem when multiple processors are attached to the same bus and each processor has its own local cache
		- a word is altered in one cache, but it could conceivably invalidate a word in other caches
- write through & write back
	- write through
		- simple, all write operations are made to the main memory as well as to the cache
		- disadvantage: generates substantial memory traffic and may create a bottleneck
	- write back
		- minimize memory writes
		- updates only made in cache
		- portions of main memory are invalid, accesses by I/O modules can be allowed only through cache
		- disadvantage: complex and potential bottleneck

## Lecture 10 Input and Output Organisation

Accessing I/O devices: I/O module interfaces to the system bus and controls one or more peripheral devices

### Generic Model of I/O module
- ![[Pasted image 20231210161351.png|300]]
- two major functions of an I/O module
	- interface to <font color="#0070c0">processor</font> and <font color="#0070c0">memory</font> via <font color="#0070c0">system bus</font> and <font color="#0070c0">central switch</font>
	- interface to one or more peripheral devices by tailored data links
- all major functions
	- control and timing
		- coordinate flow of traffic between external devices and internal resources
	- processor communication
		- command decoding
		- data, status reporting
		- address recognition
	- device communication
		- command, status, data
	- data buffering
		- balance device and memory speed
	- error detection
		- detect and report transmission error
- ![[Pasted image 20231210162906.png|400]]


### External Devices
- provides means of exchanging data between the environment and the system
- I/O module and system connected with a link
	- used to exchange <font color="#0070c0">control</font>, <font color="#0070c0">status</font> and <font color="#0070c0">data</font>
- category of external devices
	- human readable
	- machine readable
	- communication
- ![[Pasted image 20231210161828.png|325]]
- Keyboard/Monitor
	- basic unit of exchange is the <font color="#0070c0">character</font>
	- associate each character is a code
	- each character in this code represented by unique 7-bit code (128 different characters)
	- types of characters
		- printable
		- control
			- `\n`
			- related to communication procedures
	- input through keyboard ➡ electronic signals ➡ interpreted by transducer ➡ translated into bit pattern ➡ I/O module ➡ system
	- system transmit codes ➡ I/O module ➡ transducer interprets code ➡ send signals to output device

### I/O techniques
![[Pasted image 20231210163625.png|475]]
- programmed I/O
	- processor control I/O operation through executing program
	- when the processor issues a command, it must wait until I/O operation is complete
	- processor is faster than I/O module: waste processor time
- Interrupt-driven I/O
	- Processor <font color="#0070c0">issues</font> an I/O command, <font color="#0070c0">continues</font> to execute <font color="#0070c0">other</font> instructions, and is <font color="#0070c0">interrupted</font> by the I/O module when the latter has <font color="#0070c0">completed</font> its work
- direct memory access (DMA)
	- I/O module exchange data with main memory directly without involvement of processor

### I/O commands
4 types of I/O commands
1. control
	- activate peripheral device and tell it what to do
2. test
	- test various status conditions associated with I/O and peripherals
3. read (from peripheral)
	- I/O obtain data from peripheral and place it in internal buffer
4. write (to peripheral)
	- I/O take data from the data bus and transmit data to peripheral

### I/O instructions
- for programmed I/O
	- close correspondence between I/O related instructions and I/O commands issued by processor
	- form of I/O instruction depends on the way external devices addressed
- each I/O device connected to I/O module is given a unique identifier/address
	- when processor issues command, <font color="#0070c0">command contains address</font> of desired devices
	- I/O module must interpret address lines to determine if command is for itself
- memory-mapped I/O
	- a single address space for memory locations and I/O devices
	- A single read line and a single write line are needed on the bus

### I/O mapping
- Memory mapped I/O
	- device and memory <font color="#0070c0">share</font> address space
	- I/O just like memory read/write
	- no special command for I/O
- isolated I/O
	- <font color="#0070c0">separate</font> address spaces
	- need I/O or memory select lines
	- special command for I/O
		- limited set

<span style="background:rgba(140, 140, 140, 0.12)">example of memory-mapped I/O</span>

| address | instruction      | operand | comment                |
| ------- | ---------------- | ------- | ---------------------- |
| 200     | Load AC          | 1       | load accumulator       |
|         | store AC         | 517     | initiate keyboard read |
| 202     | load AC          | 517     | get status byte        |
|         | branch if Sign=0 | 202     | loop until ready       |
|         | load AC          | 516     | load data type                       
- two addresses dedicated to keyboard input
	- 516: refers to data register
	- 517: refers to status register, functioning as a control register for receiving processor command

<span style="background:rgba(140, 140, 140, 0.12)">example of isolated I/O</span>

| address | instruction      | operand | comment                |
| ------- | ---------------- | ------- | ---------------------- |
| 200     | Load I/O         | 5       | initiate keyboard read |
| 201     | Test I/O         | 5       | check for completion   |
|         | branch not ready | 201     | loop until complete    |
|         | In               | 5       | Load data type                       |
- I/O ports are accessible only by special I/O command

### interrupt-driven I/O
- problem of programmed I/O
	- processor has to wait for a long time for I/O module to be ready
- interrupt-driven I/O: issue I/O command, then go on doing other work. Then, I/O module will interrupt processor to request service once it's ready to exchange data
- procedure of interrupt
	1. device issue an interrupt signal to processor
	2. processor finishes execution of current instruction, then respond to the interrupt
	3. processor tests for interrupt and sends acknowledgement signal, allowing device to remove interrupt signal
	4. processor prepare to transfer control to interrupt routine
	5. processor loads program counter (PC) with entry location of interrupt handling program
	6. PC and program status word (PSW) relating to interrupt program saved on system stack (saving context)
	7. interrupt handler process interrupt
	8. When interrupt processing is complete, the saved register values are retrieved from the stack and restored to the registers (restore context)
	9. restore PSW and PC values from stack
- ![[Pasted image 20231210173256.png]]
- design issues of interrupt I/O
	- how does processor determine which device issued interrupt
		- solutions
			- multiple interrupt lines
				- between the processor and I/O modules
				- even if multiple lines are used, it is likely that each line will have multiple I/O modules attached to it
			- software poll
				- once detecting interrupt, it branches to an interrupt-service routine (ISR) whose job is to poll each I/O module to determine which module caused the interrupt
			- daisy chain (hardware poll, vectored) [more information: check this](https://www.geeksforgeeks.org/priority-interrupts-sw-polling-daisy-chaining/)
				- interrupt acknowledge line is daisy chained through the modules
				- Vector - address of the I/O module or some other unique identifier
				- Vectored interrupt - processor uses the vector as a <font color="#0070c0">pointer</font> to the appropriate device-service routine, avoiding the need to execute a general interrupt-service routine first
			- bus arbitration (vectored)
				- I/O module must first gain control of the bus before raise interrupt request
				- when processor detect interrupt, it responds on interrupt acknowledge line
				- requesting module places its vector on the data lines
	- if multiple interrupts happen, which one should processor choose to process

### drawbacks of programmed and interrupt driven I/O
- both
	- I/O transfer rate is limited by the speed with which processor can <font color="#0070c0">test</font> and <font color="#0070c0">service</font> a device
	- processor tied up in managing I/O transfer, each I/O transfer needs a number of instructions to be executed
- when use DMA: large volume of data need to be moved

### DMA
- ![[Pasted image 20231210175129.png|400]]
- DMA and Interrupt Breakpoints During an Instruction Cycle![[Pasted image 20231210175208.png|425]]
- alternative DMA configurations
	- ![[Pasted image 20231210175245.png|400]]
	- ![[Pasted image 20231210175309.png|400]]
	- ![[Pasted image 20231210175325.png|400]]
- ![[Pasted image 20231210175525.png|475]]
- fly-by DMA controller
	- data doesn't pass or store in DMA chip
		- DMA only in between I/O module and memory
		- not between two I/O ports or two memory locations
	- memory to memory via register

### Direct Cache Access (DCA)
- DMA is not able to scale to meet increased demand due to dramatic increase in data rates
	- demand comes from
		- Ethernet
		- Wi-Fi
- cache related performance issues
	- network traffic transmission feature
		- transmit in the form of <font color="#0070c0">sequence</font> of protocol block, called <font color="#0070c0">packets</font> or <font color="#0070c0">protocol data units</font>
	- Ethernet payload consists of block of data with <font color="#0070c0">TCP header</font> & <font color="#0070c0">IP header</font>
	- outgoing data: Ethernet packets are formed in a peripheral component, such as in <font color="#0070c0">I/O controller</font> or <font color="#0070c0">network interface controller</font> (NIC)
	- incoming traffic:  I/O controller <font color="#0070c0">strips off </font>the Ethernet information and <font color="#0070c0">delivers the TCP/IP packet</font> to the host <font color="#0070c0">CPU</font>
	- both outgoing and incoming traffic the <font color="#0070c0">processor</font>, <font color="#0070c0">main memory</font>, and <font color="#0070c0">cache</font> are all involved
- for DMA
	- data to be transmitted is placed in an <font color="#0070c0">application-assigned buffer</font> in main memory
		- core transfers data to system buffer in main memory & create TCP and IP headers, which are also buffered in system memory
		- packet then picked up via DMA for transfer via NIC
		- activity involves main memory & cache
		- Similar transfers between system and application buffers are required for incoming traffic
- DCA strategies
	- simplest
		- applied to only incoming traffic
		- DCA function in the memory controller sends a <font color="#0070c0">prefetch hint</font> to the <font color="#0070c0">core</font> once the data is available in system memory
		- enable core to prefetch data packet from system buffer
	- gains to avoid system buffer in main memory altogether
		- packet and packet descriptor information are accessed only once in the system buffer by the core
		- incoming packets: the core <font color="#0070c0">reads the data</font> from the buffer and <font color="#0070c0">transfers</font> the packet payload to an <font color="#0070c0">application buffer</font>

### Packet Traffic Steps
- incoming
	-  Packet arrives 
	- DMA
	- NIC interrupts host
	- Retrieve descriptors and headers
	- Cache miss occurs
	- Header is processed
	- Payload transferred
- outgoing
	- Packet transfer requested
	- Packet created
	- Output operation invoked
	- DMA transfer
	- NIC signals completion
	- Driver frees buffer

### Comparison of DMA and DDIO
![[Pasted image 20231210181722.png|400]]

### Evolution of the I/O Function
From early to latest
1. CPU directly control
2. controller or I/O <font color="#0070c0">module</font> added, using programmed I/O
3. employ <font color="#0070c0">interrupt</font> to improve efficiency
4. I/O module given <font color="#0070c0">access to memory</font> (DMA), transfer data without CPU, except the beginning & end of transfer
5. I/O module is enhanced to become a <font color="#0070c0">processor</font> in its own right, with a specialized instruction set tailored for I/O
6. I/O module has a local <font color="#0070c0">memory</font> of its own and is, in fact, a computer in its own right. With this architecture a large set of I/O devices can be controlled with minimal CPU involvement

### I/O Channel Architecture
![[Pasted image 20231210182121.png|400]]

## Lecture 11-12 Instruction Set: Characteristics and Function

- assembly code vs. machine code
	- assembly code ➡ (assembler + linker) machine language for processor
- machine instruction characteristic
	- operation of the processor determined by <font color="#0070c0">machine instructions</font> or <font color="#0070c0">computer instructions</font>
	- collection of different instructions referred to as <font color="#0070c0">instruction set</font>
	- instruction must contain the information required by the processor for execution
- elements of machine instruction
	- operation code (opcode)
		- specify operation to be performed
	- source operand reference
		- can be one or more
		- inputs for the operation
	- result operand reference
	- next instruction reference
		- tell processor where to fetch next instruction
- instruction state diagram![[Pasted image 20231210205201.png|375]]
- source & result operands
	- main or virtual memory
		- memory address must be supplied
	- processor register
		- can be referenced by instructions
		- if more than one register exists, and the instruction must contain the number of desired register
	- immediate
		- value of operand is contained
	- I/O device
		- instruction must specify I/O module and device for operation
- instruction representation
	- a sequence of bits
	- 16-bit instruction example: <span style="background:rgba(240, 200, 0, 0.2)">{Opcode (4 bits)}</span><span style="background:rgba(160, 204, 246, 0.55)">{Operand reference (6 bits)}</span><span style="background:rgba(160, 204, 246, 0.55)">{Operand reference (6 bits)}</span>
	- opcodes represented by abbreviations called <font color="#0070c0">mnemonics</font>
	- each symbolic opcode has <font color="#0070c0">fixed binary representation</font>
	- operands can also be represented symbolically
- instruction types
	- example: X = X (513) + Y (514)
		- operation accomplished by:
			1. <font color="#0070c0">load</font> a register with contents of memory location 513
			2. <font color="#0070c0">add</font> content of memory location 514 to the register
			3. <font color="#0070c0">store</font> content of register in memory location 513
	- requirements of instruction
		- express operations in a concise algebraic form using variables
		- express operations in basic form involving movement of data to/from registers
		- high-level language program must be translated into machine language to be executed
		- instruction set must be sufficient to express any instruction from a high-level language
	- category of instructions
		- *data processing*: arithmetic or logic
		- *data storage*: movement of data into/out of register
		- *data movement:* I/O instructions
		- *control*: test & branch instruction
- number of addresses
	- <font color="#0070c0">data processing</font> instructions require the most operands
	- maximum of two addresses to reference source operands
	- result needs to be saved, suggesting a third address (<font color="#0070c0">destination operand</font>)
	- after completion of an instruction, next instruction need to be fetched, and its address is needed
	- most architecture instructions have 1/2/3 operand addresses
- instruction set design
	- fundamental design issues
		- *operation repertoire*: number of instructions, which instruction to provide, how complex the operation should be
		- *data types*
		- *instruction format*: instruction length, number of addresses, size of various field
		- *registers*: number of processor registers that can be referenced
		- *addressing*: modes by which address of an operand is specified
- types of operands
	- address
	- number
		- limit to magnitude of numbers representable on a machine
		- floating-point number: limit to precision
		- three common types of numerical data
			- binary integer or binary fixed point
			- binary floating point
			- decimal
		- for simple computation: preferable to store and operate on number in decimal
			- most common: <font color="#0070c0">packed decimal</font>
				- each digit represented by 4-bit code
				- 246 ➡ 0000 0010 0100 0110
				- avoids conversion overhead
	- character
		- ASCII, each character represented by a unique 7-bit pattern
	- logical
		- considered as 1-bit item of data, with value of either 0 or 1
		- advantages to bit-oriented view
			- memory used efficiently
			- can manipulate the bits of a data item
- ARM data types
	- 3 types
		- *byte (8 bits)*
			- can be stored at any location in memory
		- *half-word (16 bits)*
			- half-word access should be half-word aligned
		- *word (32 bits)*
	- after loading from memory, data can have different bit-length, but it must be <font color="#0070c0">extended</font> into 32 bits (equal to the <font color="#0070c0">size of register</font>)
		- unsigned number: extended by inserting 0 ahead number
		- positive number: also inserting 0 ahead number
		- negative number: extended by inserting 1 ahead number
		- MSB shows polarity of data (positive or negative)
	- all data types can be used for two's complement signed integers
	- majority of ARM processors don't provide floating point hardware (but can be implemented in software)
	- Endian Support
		- little endian (E-bit = 0)
			- LSB stored at lowest memory address
		- big endian (E-bit = 1)
			- MSB stored at lowest memory address
- types of operatons
	- data transfer
		- if involving memory
			- determine memory address
			- perform virtual to physical address transformation
			- check cache
			- initiate memory read/write
		- things need to specify in instruction
			- location (in memory/register/top of stack)  of source and destination
			- length of data
			- mode of addressing
	- arithmetic
		- can include data transfer before/after operation
		- perform function in ALU
		- set condition codes and flags
	- logical
		- performed on binary data
		- *logical shift*: fills vacant LSB/MSB with zero, and discards the previous value
		- *arithmetic shift*: treat data as a signed integer, <font color="#0070c0">doesn't shift the sign bit</font>
		- *rotate*: or called cyclic shift
	- conversion
		- can include special logic
	- I/O
		- issue command to I/O module
		- if memory-mapped I/O, need to determine memory-mapped address
	- system control
		- reserved for the use of operating system
		- can be executed only when processor in a privileged state or the program is privileged.
	- transfer of control
		- used to change the sequence of instruction execution
			- way to realize: update the program counter
		- most common operation
			- branch
				- also referred to as <font color="#0070c0">jump</font>, can be either forward or backward
				- conditional branch
				- unconditional branch
			- skip
				- imply skipping one instruction, implied address equals to $address \:of\: next \:instruction + one\: instruction\: length$
			- procedure call
				- any point of program, procedure can be invoked or called.
				- instruct processor to execute the entire procedure then return to the point where it's called
				- why use procedure
					- economy
					- modularity
				- mechanism
					- involve two basic instruction
						- call instruction
						- return instruction
					- where to keep return address
						- register
						- top of stack
- ARM condition codes
	- defined 4 condition flags, stored in <font color="#0070c0">program status register</font>
		- N (negative)
		- Z (zero)
		- C (carry)
		- V (overflow)

## Lecture 13 Addressing Modes and Formats

### addressing modes
- notation
	- A = contents of an address field in the instruction
	- R = contents of an address field in the instruction that refers to a <font color="#0070c0">register</font>
	- EA = actual (effective) address of the location containing the referenced operand
	- (X) = contents of memory location X or register X
- most common addressing techniques
	- Immediate
		- simplest, operand value present in instruction $Operand = A$
		- used to define and use constants or set initial value
		- pros: no memory reference
		- cons: limited operand magnitude
	- Direct
		- address field contains the effective address of the operand $EA=A$
		- pro: simple
		- con: limited address space
	- Indirect
		- purpose: length of address field limited the range
		- solution: address filed <font color="#0070c0">refer to</font> the address of the word contains <font color="#0070c0">full-length address</font> of the operand $EA=(A)$
		- pro: large address space
		- con: multiple memory references
	- Register Direct
		- similar to direct, but address field refers to a register $EA = R$
		- pro: no memory reference, small address field
		- con: limited address space
	- Register indirect
		- similar to indirect, address field refer to a register where contains a full-length address, storing value of operand $EA = (R)$
		- pro: large address space
		- con: extra memory reference
	- Displacement
		- combine the capability of direct addressing and register indirect addressing, $EA=A+(R)$
		- ![[Pasted image 20231211143437.png|225]]
		- most common displacement addressing
			- relative addressing
				- PC relative addressing, referenced register is program counter
				- next instruction address added to address field to produce EA
				- if most memory references are <font color="#0070c0">near</font> to the instruction being executed, the use of relative addressing saves address bits in the instruction
			- base-register addressing
				- referenced register (<font color="#0070c0">base register</font>) contains a <font color="#0070c0">main memory address</font>, and <font color="#00b050">address field</font> contains <font color="#00b050">displacement</font> (usually unsigned integer representation) from that address
				- memory address calculated by $base\:address + displacement$
				- useful for addressing elements of arrays or other structured data
			- indexing
				- <font color="#0070c0">address field</font> references a <font color="#0070c0">main memory address</font>, referenced <font color="#00b050">register</font> contains a positive <font color="#00b050">displacement</font> from that address
				- just the opposite of the interpretation for base-register addressing
				- useful for performing iterative operations
		- pro: flexibility
		- con: complexity
	- Stack
		- stack: a linear array of locations, also referred to as <font color="#0070c0">pushdown list</font> or <font color="#0070c0">last-in-first-out queue</font>
		- items are appended to the top of the stack
		- associated with stack: pointer whose value is the address of the top of the stack
		- stack pointer maintained in a register
		- pro: simple instruction
		- con: limited applicability

| mode              | algorithm         | advantage           | disadvantage               |
| ----------------- | ----------------- | ------------------- | -------------------------- |
| immediate         | operand = A       | no memory reference | limited operand magnitude  |
| direct            | EA = A            | Simple              | Limited address space      |
| indirect          | EA = (A)          | large address space | multiple memory references |
| register direct   | EA = R            | no memory reference | limited address space      |
| register indirect | EA = (R)          | large address space | extra memory reference     |
| displacement      | EA = A + (R)      | flexibility         | complexity                 |
| stack             | EA = top of stack | simple instruction  | limited applicability                           |

### ARM addressing modes
- overview
	- use simple and straightforward set of addressing mode (RISC)
	- can be classified with respect to the type of instruction
		- different types of instructions often associate with specific addressing mode
- *load/store multiple addressing*
	- load/store multiple instructions: load a subset or all of the general purpose registers from memory
	- 4 addressing modes are used
		- ![[Pasted image 20231211151526.png|400]]
		- increment after (IA)
		- increment before (IB)
		- decrement after (DA)
		- decrement before (DB)

### instruction format
- define the layout of the bits of an instruction
- include an <font color="#0070c0">opcode</font> and, implicitly or explicitly, zero or more <font color="#0070c0">operands</font>
- instruction length
	- factors affect the choice of length
		- memory size
		- memory organization
		- bus structure
		- processor complexity
		- processor speed
	- trade-off between <font color="#0070c0">powerful instruction repertoire</font> and <font color="#0070c0">need to save space</font>
- allocation of bits
	- trade-off between <font color="#0070c0">number of opcodes</font> and the power of the <font color="#0070c0">addressing</font> capability
	- factor affects choice of allocation
		- number of addressing modes
		- number of operand
		- register vs. memory
		- number of register sets
		- address range
		- address granularity
- programmed data processor-8 (PDP-8)
	- simplest instruction designs for a general-purpose computer
	- 12-bit instructions and operates on 12-bit words
	- 3 types of instructions
		- Memory Reference Instruction
		- Input/output instructions
		- Register reference instructions
- PDP-10
	- emphasis on making the system <font color="#0070c0">easy to program</font>, even if <font color="#0070c0">additional hardware expense</font> was involved
	- 36-bit word length and a 36-bit instruction length
	- 9-bit opcode
	- two types of registers: <font color="#0070c0">general-purpose</font> registers and <font color="#0070c0">index</font> registers for different purposes
- Variable-Length Instructions
	- pros
		- large repertoire of opcodes with different opcode length
		- more flexible addressing
		- various combination of register and memory reference
	- cons
		- processor does not know the length of the next instruction to be fetched
			- One strategy is to <font color="#0070c0">fetch</font> a number of bytes or words <font color="#0070c0">equal</font> to at least the <font color="#0070c0">longest</font> possible instruction (increases the <font color="#0070c0">complexity</font> of the processor)
- PDP-11
	- designed to provide a <font color="#0070c0">powerful</font> and <font color="#0070c0">flexible</font> instruction set
	- 16 bits long
	- employs a set of eight 16-bit general-purpose registers
- Virtual Address Extension (VAX)
	- complex instruction set computing (CISC)
	- <font color="#0070c0">variable</font> in length, allowing for a wide range of addressing modes, operand types, and instruction formats
	- two criteria of VAX instruction design
		- have the natural number of operand
		- all operands should have the same generality in specification

### ARM instruction format
- instruction length: 32 bits, has regular format
- format
	- <span style="background:#fff88f">conditional code (4bits)</span> + <span style="background:#d3f8b6">type of instruction (3bits)</span> +  <span style="background:#affad1">opcode and/or modifier bits (5bits)</span> + <span style="background:#fdbfff">operand addressing (20bits)</span>

## Lecture 14 Processor Structure and Function

### processor organization
- requirements of processor
	- fetch instruction
		- read instruction from memory (register, cache or main memory)
	- interpret instruction
		- decode to determine what action is required
	- fetch data
		- read data from memory or I/O module
	- process data
	- write data
		- write result of execution to memory or I/O module
- internal structure
  ![[Pasted image 20231211160821.png|350]]

### register organization
- level is higher than cache and main memory
- 2 roles of registers
	- user-visible register
		- enable programmer to <font color="#0070c0">minimize main memory references</font> by optimizing use of registers
	- control and status register
		- Used by the <font color="#0070c0">control unit</font> to control the operation of the processor and by privileged operating system programs to <font color="#0070c0">control the execution</font> of programs
- user-visible register
	- category
		- general purpose register
			- can be assigned to a variety of functions
		- data register
			- can only to <font color="#0070c0">hold data</font> and cannot be employed in the calculation of an operand address
		- address register
			- devoted to particular addressing mode
		- condition codes
			- partially visible to user, holds condition codes (also referred to as <font color="#0070c0">flags</font>)
			- pros
				- reduce `COMPARE` and `TEST` instructions
				- simplify `BRANCH` instructions
				- facilitate multiway branches
				- saved on the stack during subroutine calls
- control and status registers
	- 4 essential registers
		1. program counter (PC)
			- contains address of <font color="#245bdb">next</font> instruction
		2. instruction register (IR)
			- contains instruction <font color="#245bdb">most recently</font> fetched
		3. memory address register (MAR)
			- contains <font color="#245bdb">address</font> of a location in memory
		4. memory buffer register (MBR)
			- contains a word of data <font color="#245bdb">to be written</font> to memory or the word most <font color="#245bdb">recently read</font>.
- program status word
	- what's this: registers that contain <font color="#245bdb">status information</font>
	- common fields or flags
		- sign
		- zero
		- carry
		- equal
		- overflow
		- interrupt enable/disable
		- supervisor
- example of register organization
	- MC68000
		- length: 32 bit
		- partition: 8 data registers and 9 address registers
		- data register: for data manipulation & addressing as index register
		- allows 8-, 16-, and 32-bit data operations, determined by opcode
	- Intel 8086
		- length: 16-bit
		- category
			- *General-purpose registers*: addressable on a byte or 16-bit basis
			- *Special purpose registers*: Pointers and Index
			- *Segment registers*: allows only four segments to work at a time
			- *Flag register*: condition control and program status

### instruction cycle
- 4 stages of instruction cycle
	1. fetch: <font color="#245bdb">Read</font> the <font color="#245bdb">next instruction</font> from memory into the processor.
	   ![[Pasted image 20231212110428.png|450]]
	2. execute: <font color="#245bdb">Interpret</font> the opcode and perform the indicated operation.
	3. Interrupt: If interrupts are enabled and an interrupt has occurred, <font color="#245bdb">save</font> the <font color="#245bdb">current state</font> and <font color="#245bdb">service</font> the interrupt
	   ![[Pasted image 20231212110545.png|475]]
	4. Indirect: If indirect addressing is used, then additional memory accesses are required
	   ![[Pasted image 20231212110502.png|475]]

### Pipelining Strategy
- pipeline: new inputs are accepted at one end before previous inputs, and outputs appear at the other end
- simple approach: (instruction) ➡ fetch ➡ execute ➡ (result)
	- problem of this approach: during execution, main memory is not addressed (low usage)
	- solution: fetch next instruction in parallel with execution
- decomposition of instruction processing
	- fetch instruction (FI)
	- decode instruction (DI)
	- calculate operands (CO)
	- fetch operand (FO)
	- execute instruction (EI)
	- write operand (WO)
- factors limit performance enhancement
	- <font color="#245bdb">waiting</font> involved at various pipeline stages
	- <font color="#245bdb">conditional branch instruction</font>, which will <font color="#245bdb">invalidate</font> several instruction fetches (some other instructions have to wait until certain instruction is completed)
	- <font color="#245bdb">interrupt</font>
- things need to consider
	- CO stage may depend on contents of a <font color="#245bdb">register</font> that can be <font color="#245bdb">altered</font> by the <font color="#245bdb">previous instruction</font> in the pipeline

### pipeline hazards
- some part of pipeline need to <font color="#245bdb">stall</font> (called <font color="#245bdb">pipeline bubble</font>) until the condition allows to continue
- 3 types of hazards
	- resource
	- data
	- control or branch

#### resource hazard
- when: two or more instructions in the pipeline require the same resource
- result: instruction must be executed in serial for this portion of pipeline
- also referred to as *structural hazard*

#### data hazard
- when: conflict in the <font color="#245bdb">access</font> of <font color="#245bdb">operand location</font>. Generally, <font color="#245bdb">two instructions</font> in a program are to be executed in sequence and <font color="#245bdb">both access</font> a particular memory or register <font color="#245bdb">operand</font>
- 3 types of data hazards
	- read after write, RAW (true dependency)
		- 1st instruction make modification, 2nd instruction reads the data in that location
		- hazard occurs if read before writing completes
	- write after read, WAR (antidependency)
		- 1st instruction read, 2nd writes to that location
		- hazard occurs if writing completes before read
	- write after write, WAW (output dependency)
		- 2 instructions both write to the same location
		- hazard occurs if write operation take place in the reverse order of intended sequence

#### branch hazard
- when: <font color="#245bdb">wrong branch prediction</font> brings <font color="#245bdb">instructions</font> into the pipeline that must be <font color="#245bdb">discarded</font>
- how to deal with
	- *multiple streams*: allow pipeline to fetch two instructions, making use of two streams
	- *prefetch branch target*: once recognized branch, target of branch is prefetched
	- *loop buffer*: a small, high-speed memory <font color="#245bdb">retains most recently fetched instructions</font> in sequence. If a branch is to be taken, hardware firstly checks if the branch target is within the buffer.
	- *delayed branch*: rearrange instructions within a program ➡ desire to let branch occur later
	- *branch prediction*: predict whether a branch will be taken

##### branch prediction
- static branch prediction
	- never taken
	- always taken
- dynamic branch prediction (based on previous execution history)
	- 1-bit branch prediction
	- 2-bit predictor



### interrupt processing
- two classes of events
	- interrupts (signal from hardware causes)
		- maskable interrupts: can be controlled and ignored by CPU (like keyboard input)
		- non-maskable interrupts: always treated as high-priority, CPU can't ignore or disable (like hardware failure)
	- exceptions (signal from software)
		- processor-detected exceptions: errors that are detected by the CPU during normal operation and are critical for system stability (like divided-by-zero)
		- programmed exceptions: instructions that generate an exceptions (like explicit system calls)

## Lecture 15 Instruction-Level Parallelism, and Superscalar Processors

### superscalar overview
- what is superscalar: machine that is designed to improve the performance of execution of scalar instructions
	- most applications are operating <font color="#245bdb">scalar quantities</font>
- approach: ability to execute instructions <font color="#245bdb">independently</font> and <font color="#245bdb">concurrently</font> in different pipelines
- improve by allowing instructions to be executed in a <font color="#245bdb">different order</font> from the program order.

### superscalar vs. scalar organization
- traditional scalar organization
	- one pipelined functional unit for integer operations and one for floating-point operations
	- ![[Pasted image 20231212134849.png|400]]
	- parallelism achieved by multiple instructions to be at different stages of the pipeline at one moment
- superscalar organization
	- multiple functional units, each of which is implemented as a pipeline
		- allow processor to execute <font color="#245bdb">multiple streams</font> of instruction in parallel (one stream for each pipeline)
	- ![[Pasted image 20231212135045.png|400]]
	- each individual functional unit provide parallelism by virtue of its pipelined structure
	- <font color="#245bdb">hardware</font> + <font color="#245bdb">compiler</font> to ensure no violation of original program

### superpipelining
- where to improve: based on the fact that many pipeline <font color="#245bdb">stages</font> perform tasks that <font color="#245bdb">require less than half a clock cycle</font>
- ![[Pasted image 20231212135528.png|450]]
	- base pipeline: issue one instruction per clock cycle, perform one pipeline stage per clock cycle, only one instruction is in its execution stage at any one time
	- superpiplined: capable of performing two pipeline stages per clock cycle
		- functions performed in each stage can be split into two non-overlapping parts and each can execute in half a clock cycle
	- superscalar: capable of executing two instances of each stage in parallel
- constraints
	- how many percents of one program can be executed in parallel (degree of parallel)
	- combination of <font color="#245bdb">compiler-based optimization</font> and <font color="#245bdb">hardware</font> techniques can be used to maximize instruction level parallelism
- fundamental limitations
	- Procedural dependency: if a instruction is followed by a branch, procedural dependency on the branch and cannot be executed until the branch is executed.
	- Resource conflicts: is a competition of two or more instructions for the same resource at the same time
	- other three aspects are the same as data hazard

#### effect of dependencies
![[Pasted image 20231212140625.png|500]]
- for data dependency
	- delayed as many clock cycles as required to remove dependency
	- can be solved by <font color="#245bdb">register renaming</font>
- for branch
	- complicates the pipeline operation
	- consequence is much more severe than data dependency

### design issues
- instruction level parallelism
	- require instructions in a sequence are independent
	- execution can be in parallel by overlapping
	- governed by data & procedural dependency
- machine parallelism
	- <font color="#245bdb">measure</font> ability of processor can exploit the improvement by instruction level parallelism
	- governed by number of parallel pipelines

### instruction issue policy

instruction issue
- refer to the process of initiating instruction execution in the processor’s functional units

instruction issue policy
- processor try to look ahead of the current point of execution to locate instructions that can be brought into the pipeline and executed
- refers to the protocol used to issue instructions

3 types of orderings
1. order of fetching instructions
2. order of executing instructions
3. order of updating contents of register and memory locations

3 types of superscalar instruction issue policies
1. in-order issue with in-order completion
	- instruction start (issued) in order, and completion also in order
	- there will have delay on issue & execution to guarantee in-order completion
	- ![[Pasted image 20231212151306.png|300]]
2. in-order issue with out-of-order completion
	- ![[Pasted image 20231212151351.png|300]]
	- allow instructions to be completed earlier
3. out-of-order issue with out-of-order completion
	- to allow out-of-order issue
		- necessary to separate decode and execute stage of the pipeline
		- done with buffer referred to as *instruction window*
		- As long as this buffer is <font color="#245bdb">not full</font>, the processor can continue to fetch and decode new instructions
	- conditions to issue execution stage
		- particular functional unit for execution is available
		- no conflicts or dependencies block this instruction
	- ![[Pasted image 20231212152448.png|300]]

### branch prediction

examples
- Intel 80486: fetching both the next sequential instruction after a branch
- RISC: delayed branch, execute single instruction that immediately follow the branch to keep the pipeline full
- superscalar: delayed branch less appeal (problems about dependencies)

### machine parallelism
- not worthwhile to add functional units without register renaming
- adding functional units can have slight improvement, but the hardware complexity increase is huge


## Lecture 18 Multi-core Computers



## Lecture 19&20 CPU Scheduling



# Lab

## Lab 1

### binary number system


<font color="#d99694">Operators</font>

| Operator    | Symbol |
| ----------- | ------ |
| AND         | &      |
| OR          | \|     |
| XOR         | ^      |
| NOT         | ~      |
| Left Shift  | <<     |
| Right Shift | >>       |

<font color="#d99694">Application of Operators</font>

* Useful when manipulating registers

Steps to make a 8 bit register need 3rd and 5th bit 1 and 0:

1. $101<<3 = 00101000$
2. ~00101000 = 11010111
3. xxxxxxxx | 11010111 = xx0x0xxx
4. 001<<2 = 00000100
5. xx0x0xxx | 00000100 = xx0x1xxx

or we can use less steps:

1. Register &= ~(101<<3)
2. Register |= (001<<3

### Register

* why manipulating register directly:
	* sometimes specially for <font color="#95b3d7">time intensive</font> applications, it might be better to use direct register access as it is much faster than using the HAL library
* GPIOX_CRL and GPIOX_CRH
	* used to <font color="#95b3d7">initialize</font> GPIO ports
* GPIOX_ODR
	* set to change i.e to set or reset any specific pin of a GPIO port and can used to write bits on the pins when the pin is in output mode
	* When used by the system, 16 to 31 bits are reserved, which can't be changed.


## Lab 2

<span style="background:rgba(74, 82, 199, 0.2)">UART</span>
- parameters
	- data length
	- start stop signal
	- baud rate (number of pulses per second)
- 3 ports for this board
	- default config: Async, Baud rate 115200 Bits/s, length 8 bits and stop bit 1
- 3 methods using UART in STM32
	- Polling: block CPU until data received
	- Interrupt: efficient (NOT blocking CPU), once data received, call interrupt
	- Direct Memory Access (DMA): CPU do nothing, data transfer to memory directly

<span style="background:rgba(74, 82, 199, 0.2)">I2C</span>
- 2 wires: SDA and SCL -> synchronous
- specify address of slave to designate
- ![[Pasted image 20231012132949.png]]
- ![[Pasted image 20231012133312.png]]
- NACK indicate all data received and stop the communication

<span style="background:rgba(74, 82, 199, 0.2)">SPI</span>
- CLK, MOSI, MISO, CS
- full duplex, synchronous
- on STM32


