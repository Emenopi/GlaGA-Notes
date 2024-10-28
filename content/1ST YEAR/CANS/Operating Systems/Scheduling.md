---
tags:
  - Computer_Architecture_and_Network_Systems
---
The act of assigning resources to the system for execution of actions
Schedulers mainly aim to maximise CPU utilisation by:
- Maximise throughput
- Minimise wait time
- Minimise latency
- Maximise fairness

This is achieved by usage of two queues:
- Ready queue:
	- Processes in [[RAM|Memory]] ready for execution
- Device queue:
	- Processes waiting on a device, one queue per device

There are a number of different [[Schedulers]]:
- Long-term scheduler (Job Scheduler)
	- Loads programs into memory
	- Strives for mix of IO bound and CPU bound processes
- Medium-term scheduler
	- Freezes and unloads processes to be reintroduced at a later stage, e.g. when there is not enough RAM for all processes
- Short-term scheduler (CPU Scheduler)
	- Selects which processes to execute next
