---
tags:
  - Computer_Architecture_and_Network_Systems
aliases:
  - Round Robin
---
A preemptive version of FCFS.
[[Processes]] are added to the queue ordered by time of arrival.
Each process is executed for a certain time frame, if it needs more time, it's added to the end of the queue

May lead to long waiting times, performance relies on length of time slice