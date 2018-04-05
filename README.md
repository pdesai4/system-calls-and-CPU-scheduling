CS 550-04 Operating Systems

System calls and CPU scheduling by hacking the xv6 OS

Implementation: 

PART1 -> System call shutdown made.
		 
PART2 -> Create a child biased race condition when global variable `fork_flag` is set to 1.
		 
PART3 -> Enable stride scheduling when the value of global variable `scheduler_val` is 1. Added ticket, stride and pass values in the structure of each process. Globla variable `STRIDE_TOTAL_TICKETS` defines the system has 100 tickets. Function ticket_distrubution distributes tickets to the active processes, calculates and sets the respective stride value and sets pass value for each process as 0 initially. Function `get_proc_min_pass()` gets the process with minimum pass value, in global variable `struct proc *to_sched`, as the next process to schedule. The function `transfer_tickets()` enables each process to transfer its tickets to another process whose pid is passed to the function. This function updates the stride and ticket values of both the processes.