---
tags:
  - Computer_Architecture_and_Network_Systems
aliases:
  - Hazards
---
A conflict between different pipeline stages
Can be:
- Resource hazard
	- Two different stages need access to [[RAM|Memory]]
- Data hazard
	- e.g. Write After Read (WAR)
- Control hazard
	- e.g. Branch, [[Interrupts]]


If conditional branching, subsequent instructions are flushed (removed) to ensure correct pipeline order
- Reduces throughput due to "branch penalty"