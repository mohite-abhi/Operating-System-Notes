# 8. CPU scheduling

**time/durations**

- arrival time
	- time instance of start
- burst time
	- time duration to execute process without counting the waiting time
- completion time
	- time instance to complete
- turn around time time
	- completition time - arrival time
- waiting time time
	- T.A.T - B.T
- response time
	- first time process is allocated cpu
- (sometimes)context switching time
	- time to change processes
**Intro**

- dispacher
	- gives cpu to process selected by short term scheduler
		- switching context
		- switching to user mode
		- jumping to location in user program to restart program
	- dispatcher latency
		- time for stopping a process and starting other process
- scenarios considered for preemption
	- access to shared data
	- while in kernel mode
	- interrupts occuring during crucial os activities
	- round robin
	- higher priority process comes


**scheduling criteria**
- cpu utilizaion
	- keep cpu as much busy as possible
- throughput
	- no. of processes that complete their execution per time unit
- turnaround time
	- amnt. of time to execute a particuar process
- waiting time
	- amnt. of time process is waiting in ready queue
- response time
	- time b/w ready state and getting cpu for first time

- Optimization Criteria for scheduling algorithm 
	
	- max cpu utilization
	- max throughput
	- min turnaround time
	- min waiting time
	- min response time




