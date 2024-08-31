___
## Preview
	SystemCallSessionTask:
___
### **Time**
		______________________
		ls vs. find
		ls    time --> 0.000585
		find  time --> 0.005306
		______________________
		cp vs. rsync 
		cp    time --> 0.003637
		rsync time --> 0.004973
		______________________
		diff vs. cmp
		diff  time --> 0.001808
		cmp   time --> 0.006670
		______________________
		uniq vs. sort
		uniq  time --> X!!
		sort  time --> X!!
		______________________
		grep vs. sed
		grep  time --> 0.001978
		sed   time --> 0.007754	
Search for why is the time we get from the strace different from the time command although they should be the same(the strace is bigger than)
___


***In this session we will study our first stack --> the process management stack*** 
## Main Points
___
- A process is the the act of running a program
- The PM stack deals with managing and controlling processes in the OS.
- The key components of the PM stack.
	Process scheduler 
	process creation and termination
	Process state management
	IPC (Inter Process Communication)
	Process synchronization
	Process resource management
	Process signals
- Important terms :
	**PID**   : process identifier
	**PPID** : parent process identifier 
		 when a process X creates another process Y the process X is called parent process and the process Y is called child, then the process Y (the child process) will have something called PPID which will be the same PID of the process X (the parent process)
		 The PPID is significant in scenarios where a process needs to communicate with or send signals to its parent process. Additionally, it helps in process management, as terminating a parent process may result in the termination of its child processes as well. 
	**Priority** : the order in which processes are allocated CPU time by the process scheduler.
	**Daemon** : a background process that runs independently of user interaction.
	**Zombie** : a process that has completed its execution but still has an entry in the process table.
	**Init Process** : ???
	**Signal** : a signal is a software interrupt delivered to a process to notify it of an event or request some action.	 	 
- RUN operation --> 2 types 
	 $$Foreground$$
	 1- When a program runs in the foreground mode, it executes directly within the terminal, and its output is displayed on the screen.
     2- The program typically takes control of the terminal, and the user needs to wait for it to complete before running other commands.
     3- The user can interact with the program by providing input and receiving output directly in the terminal.
     4- In foreground mode, the program may also receive signals from the terminal, such as interrupt signals (e.g., pressing Ctrl+C) or suspend signals (e.g., pressing Ctrl+Z). and
    $$Background$$
     1-  Running a program in the background mode allows it to execute independently of the terminal, freeing up the terminal for other tasks.
	 2- The program runs in the background without blocking the terminal, so the user can continue entering commands or working on other tasks.
	 3- The program's output is typically not  displayed on the screen unless explicitly redirected to a file or another output stream.
	 4- By default, background processes do not receive input from the terminal, and their output is not shown. However, they can still generate output, which is often redirected to log files.
	 5- Background processes can continue running even after the user logs out of the terminal session.
	
	 will be more clear when we reach the Linux customization part
	
- Priority --> 2 types
	First one : can be set from the user space and takes a value from { -20 (max priority) --> 19 (min priority)} through < nice > command, it doesn't
	guarantee that the kernel will actually run the program with the priority you asked, basically when you use the nice command you are saying to the kernel : "it will be nice from you if you give this command this priority".
	
	Second one : the kernel has another range of priority the specific range and interpretation of the priority values can vary depending on the scheduling algorithm and system configuration.
- 







## Questions & points for search
___
How could i know if the kernel did my request or not(in the operation section) ? **Answered**

Search for why is the time we get from the strace different from the time command although they should be the same(the strace is bigger than) :: -->https://www.baeldung.com/linux/time-command

Files of interaction