# 7. Process II


**Process in virtual memory space**

**page table**
- the each row in the memory page is called page frame
- the each row in virtual memory is called block
	- sizeOf(block) is equal to sizeOf(frame)
- there is a mapping between the process block and page frame for mapping virtual address memory and physical memory
	- ![Screenshot_2020-08-16_11-57-33.png](../_resources/b10b61b18ff54a9fb3d9658695f49bbf.png)
- to convert virtual address to physical address we subtract from max size. and vice versa
- in ram the kernel memory will have one whole concequtive section of frames
	- ![e762390df2ee8af40479f39bb42fff2e.png](../_resources/0bc691e80f064357adb46dafb825790c.png)
- for multiple processes
	- ![9a7236e322b866f2dacd506fb1b33d0d.png](../_resources/d060d6c1dd7c416e8f00533f94b65676.png)

- kernal keeps metadata about each process (metadata)
	- process control block(open file, closed file, register)
	- kernal stack for user process (stored in the kernel part of virtual memory)
	- page table for user process



- process stack (each process has 2 stack)
	- user space stack
		- used when executing user code
	- kernal space stack
		- used when kernal code in the context of the process(eg. during system call exec we store, so we know we need to go back to the parent terminal etc.)
		- even if user stack is affected then also kernal can execute
	
--------

			
**Operations on process**

- Creation
- Scheduling
- Execution
- Killing/delete



- process creation
	- parent process creates child processes, thus make a tree
	- process identified and managed by pid (process identified
	- resource sharing
		- parent and children share all resources
		- children share subset of parent's resources
		- parent and child share no resources
	- execution options
		- parent and children execute concurrently
		- parent waits until children terminates


![Screenshot_2020-08-04_21-57-25.png](../_resources/1e81e67c4b7f44599b0c28e6152b610f.png)

- fork createss child dublicate or parent by cloning
	- creating process by cloning
	```
	int p;
	p = fork();
	if(p > 0){
		printf("Parent : child PID = %d", p);
		p = wait();
		printf("Parent : child %d exited\n", p);
	}
	else if (p == 0){
		printf("In child process");
		exit(0);
	} else{
		printf("Error\n");
	}
	}
	```


- fork tasks in kerne
	- ![d112035dcb4f5a5b6405b5b2ce3a9702.png](../_resources/1f7903e6e7ee4b6f8317b29397922174.png)
	- the page table is also copied from parent to child
		- ![353dea405372ab2e0a005160d94bd7c0.png](../_resources/7f8605e96d104f359fe9830cff35244f.png)

- using fork in c

	```
	int main(){
		fork();
		fork();
		fork();
		printf("hello");
	}
	/*output : 
	hello
	hello
	hello
	hello
	hello
	hello
	hello
	hello
	*/
	```
- ![c9089844ddf1f2b202b008fc9c23a9b4.png](../_resources/91583c3b5349496687db4bd250f64f01.png)





**Process creation

- child copy parent table
	- ![01f789efd082cee1859218c0986bd6a7.png](../_resources/11ff53045fdd42059a94a10179622f4f.png)

- copy on write (cow)
	- at start the parent pages are shared
	- but if shared page change, os stops and make a copy of 'that' page only


- executing new program
	- fork
	- exec
		- find the executable from hard disk
		- load on demand pages required to execute

**process termination**
- voluntary termination
	- exit()
		- called in child, causes termination, returns 0 to parent
- involuntary termination
	- kill(pid, signal)
		- can be sent by os/other process
- wait()	
	- parent calls, if exit() returns zero here we can resume


- types
	- cascading termination
		- if parent terminates, all children and their children need to terminate
	- zombie
		- if child process terminates it becomes zombie (defunct process)
			- pcb still exists 
			- parent process reads child status here by wait
			- after read status zombie entry removed (reaped)
			- if parent doesn't read status, os periodic reaper process will collect and remove entry
	- orphan
		- if parent terminates before child
		- adopted by super process
		- types
			- unintentional orphan
				- when parent crash
			- intentional orphan (daemons)
				- process detach from user session and run in background
				- used to run background services
				- in linux names end with d are daemons, e.g. bluetoothd
				- daemons can be invoked with 'systemctl start mysql' etc






