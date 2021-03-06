# 9. Scheduling algorithms

- main points
	- algo (FCFS, SJF, SRJF, Priority, RR)
	- burTim Pred.(static(size,type), dynamic(ave, expAve))
	- multilevel (queue, feedback queue)


**first come first served scheduling (FCFS)**

- criteria
	- according to arrival time process is scheduled
	- if arrival time s	ame
		- according to process id
- mode
	- non preemptive
- transition
	- ready to running
	- running to terminate
- gantt chart
	- ![b89dbc52f921531c400e0903fb12a27c.png](../_resources/e8700ead041b40d5bc91b3075ee6ad5d.png)
- table
	- ![f05b97bf8eecfa4e89c7e43798dc1d3f.png](../_resources/ce8d6a8248be41cfb011df9428a2b56f.png)
- average waiting time
	- (summation w.t of all processes)/ no. of processes
- average turnaround time
	- (summation t.a.t. of all processes)/ no. of processes


- example
	- ![65949a6eef0b0ee4099ddc6995d65005.png](../_resources/32c90691a996471aa1c6417ff024c955.png)
	- ![f27a95adb6abeb8a412ad9ce5825e101.png](../_resources/f6bb8fdd1c5149e2a75405990a470e43.png)
		- here the av. waiting time is too much, they starve, this is also known as convoy effect
		- if p2, p3 came before p1, w.t. would be very small
		- ![6be3464fac1b50e5cc680855c079db3e.png](../_resources/2cbb98df62db4634a699c83084a2c0b3.png)
		- so we conclude that if we take burst time as criteria, then it will be better
	- ![4a34105d1097454a8ee6385b5f067138.png](../_resources/94c3262d6fc14ba2b13adac3781c3a8e.png)
	- with context switching time = 1
		- ![22ba906155e0fa04834087cae39c4d13.png](../_resources/f65a30202aac4eb0b56c3e74966db48b.png)
- disadvantage
	- long waiting time 
	- long turn around time



**Shortest Job First (SJF)**

- criteria
	- process with lesser burst time
	- if burst time same
		- arrival time is considered
- mode
	- non preemptive
- requirement
	- process length should be known
- data structure used
	- min heap with burst time as key

- example
	- ![304f26016ffb45691aa78c9ac605c385.png](../_resources/93c07094280e49ada3324327fd363ed5.png)
	- if processes come at different time, then also this scheduling is not idle
		- ![450ba121041c0b67555abc105377ce87.png](../_resources/bb3eade233d84509b1a25b477175c19d.png)
	- ![037f6b35e871d357980c5c83413c90f1.png](../_resources/7c3500a1b9e04321b923cba088c84660.png)
		- here we can see convoy effect/ starvation

- advantage
	- maximum throughput
	- gives minimum ave. waiting time

- disadvantage
	- difficult to know burst time (non practically possible)
	- convoy effect still there (if diff Arr.Time)

**Burst time prediction**
- statis method
	- process size
		- we see actual size of process in kb maybe
		- ![effc54cb8661f910f86a3bcd7a92f7f0.png](../_resources/a866dc6a842d443dbf4f1f70460bc298.png)
		- not very accurate because there are things like loop, i/o etc that can't be calculated here
	- process type
		- types
			- os process [3-5 units]
			- interactive process [5-8 units]
			- foreground process [10-15 units]
			- background process [15-20 units]
		- not really implementable/ not good enough
- dynamic method
	- simple averaging
		- we take moving average and then predict next process
		- not really suitable
	- exponential averaging (best)
		- ![8770b71c7dc6cb9167dba0d590a69423.png](../_resources/04b6785190a34cb6a10065a62c84c7d0.png)
		- alpha * (b.t. of last process) + (1-alpha) * (predicted b.t. of last process)
		- example
			- ![66164c2f57d414f540588be31c041de8.png](../_resources/61aa229ea6ca41099a0245f3be5ae8ab.png)




**Shortest Remaining Time First (SRTF)**
- criteria
	- burst time
		- arrival time as tie breaker
- mode
	- preemptive
- example
	- ![137e6a4da13ba63dcba792d250c45506.png](../_resources/1e6eb6b187894546bd846aadf00a271c.png)
	- ![314b27b99f5eca33695b02c0d6c6bd04.png](../_resources/aaf501a0e4684a75be518b47018827eb.png)
	- ![0cb739f51fbbcb39e1fa71dc3451e3a6.png](../_resources/27f37654bfec47d3b5de856438ca9957.png)


**Priority Scheduling**

- criteria
	- priority (integer associated with each process)
		- small integer	= higher priority
- mode
	- preemptive/non preemptive
- generalisation
	- SJF is a priority scheduling where priority is inverse of predicted next cpu burst time
- problem
	- starvation : low priority process may naver execute
	- solution : 
		- aging : as time progresses increase priority of process


- example
	- ![b3397656873c6a3e3bad092c46e1524a.png](../_resources/e249c2099c1f45b88267aa4d92b76bff.png)
	- ![7d7e7a5842f31a84da7b6960d46c893d.png](../_resources/f3d85d11eaa9439ab0f9921338cbc8a2.png)
	- if explicitely non preemptive is said then, we will get a different gantt chart
		- ![80c666dde3ce632e3db92eeac8d00be0.png](../_resources/048a006a96664d9a95148f5983678249.png)






**Round Robin scheduling**

- criteria
	- time quantum (Q, it is given)
		- timer interrupts every Q to schedule next process
		- each process gets 1/n of cpu processing
	- if multiple process, fcfs
- performance based on Q
	- q too large : it will act like FIFO
	- q too small : if q approx to context switch, overhead is too high
mode
	- preemptive
- flowchart
	- ![919efbed27542e969c122b303717e250.png](../_resources/733822617c624e1cbf97ddc055eba815.png)
- example
	- ![8e89c2198b1e2ba1a6929f972fa99933.png](../_resources/e34b97280dd34b97aae3448c956cc817.png)
	- ![ff23f52ffcff1e566454a7bab4b6dd1f.png](../_resources/b9adac0862a94690b63c28a8cd904e27.png)




**Multilevel Queue**
- problem
	- we can not have system processes along with others in lets say only one scheduling algo
- solution
	- apply diff sche. algo on diff. kind of processes
	**high priority**
	- system processes - RR
	- interactive processes - SJF
	- batch processes - FCFS
	**low prioriry**
	
	
**Multilevel feedback queue**
- still problem
	- batch processes(low priority) may starve
- solution
	- we put all the diff. group queues in RR. with Q(time quantum) proportional to priority
	- ![a566fabad3c44d768e0f9a7620bc3a3b.png](../_resources/77124b31295e45b6a7047121addd3619.png)