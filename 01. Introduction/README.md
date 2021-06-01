# 1. INTRONDUCTION


- Definition
	- it is system software
	- acts as intermediatory b/w hardware and user
	- user request not hw but os so os ask hw and then return result to user
	- removes direct access to low level

- Goals
	- primary
		- convinience/ user friendly
	- secondary
		- efficiency (how efficiently using hardware)

- Responsibility (al[location]ma[nager])
	- Resource Allocation
		- Resources
			1) cpu - process
			2) i/o -kb, mouse, display, hdd
			3) memory (dram)

	- Resource Manager(files, memory ,cpu(processes), security)
		- functions of os
			- process management
			- memory management
			- i/o management
			- file management
			- network manager
			- security management
	
	- heirarchy
		- hardware => os => system programs(drivers, compilers) and application programs
	

- Typtes of OS
	- mainframes 
		- before batch processing
		- i/p & o/p in form of punch card & tapes
		- cpu consists low memory & processed jobs
		- job contains the program, data and control instruction
		- os always present in memory and transfers control from one job to another
		- only one memory
	- Batch os 
		- batches of jobs are formed having similar needs like same languages so that the time for loading and unloading compiler can be saved
		- the cpu wil do a job and data required organised as a batch and batch after batch jobs are done as fifo
		- but disadvantage is that still no i/p o/p interaction
		- only one memory
	- Spooling
		- we add a secondary memory(disk) with main memory
		- now the cpu deals main memory which takes the data from the disk, which aquires it from the i/o devices
		- i/p is there but during the i/p processes stops

	- Multiprogramming os 
		- keeps multiple process in the pool
		- then when one process is busy in i/o operation, then it is left idle and another proccess is picked up(context switch)
		- cpu never idle when processes in pool
		- but still during the context switch time, the cpu is idle
		- difficulty in scheduling, who to pick up and why
		- main memory management is required for the given processes
		- there is memory fragmentation
			- paging is used (non-contiguous/continuous meloc)

	- Multitasking os 
		- when multiprocess do not cause wait, but still they are left and passed on to another process after a certain time
		- also called time sharing, fair share, multiprogramming with round robin
		- illution of dedicated processing due to instananious context switch
		- multitasking may refer to multiple thread of same process
		- time shared processing between users in a round robin fassion, is also a interactive os

	- Multiprocessing os
		- multiple cpu in same computer in close communicacation, sharing same bus, memory and other i/o devices
		- true parallel execution
		- types
			- symmetric
				- one os controls all cpus having equal rights
			- assymetric
				- system process are given a certain processes, while the remaining handle application programs (sometimes one processor controls other processors)
		-multiple processes are available to process

	- Realtime os
		- reoponse time which is time from i/p to o/p, which is negligible here 
		- the time between data aquisition and processing negligible, these are supposed to complete tatsks in timely manner or the task at hand will fail. common designs
		- event based - like games, missiles
		- types
			- hard
				- purely deterministic and time constraint system
			- soft
				- meeting of deadline is not compulsory everytime, but the process should be completed
		

- what os do 
	- user only care about ease of use and good performance, not about resource allocation
	- but mainframe or supercomputer must keep all users happy
	- workstations have dedicated resources but they frequently  use shared resources from servers
	- handheld computers are resource poor, optimized for battery life
	- embedded computers like routers and in automobiles have litle or no ui

**definition**

- os is resource allocator, decides bw conflicting request for efficient and fair resource use
- os is a control program , to control execution of program to prevent errors and improper use of computer
- kernel is a program running all the time
- everything is either a system program(os), or an application program


storage notation

	bit, byte(that computer can move with instruction), word(64 bit word or 8 byte word)
	but in networking still bit is used beause network transfers data a bit at a time
	
	
