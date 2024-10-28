---
tags:
  - Computer_Architecture_and_Network_Systems
aliases:
  - Scheduler
---
CPU [[Scheduling]] occurs to make decisions when a [[Processes|Process]]:
- Switches from running to blocked
- Switches from running to ready
- Switches from blocked to ready
- Terminates

Scheduling can be either:
- Non-preemptive:
	- Process decides when to give up the CPU
- Preemptive:
	- Scheduler decides when process gives up the CPU

There are a number of different policies:
- First-come First-serve ( FCFS, FIFO)
- Priority based (preemptive and non-preemptive)
- Shortest Job First (SJF)
- Shortest Remaining Time First (SRTF)
- [[Round Robin Scheduling|Round Robin]] (RR)