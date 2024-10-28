---
tags:
  - Computer_Architecture_and_Network_Systems
---
The process of performing multiple operations for different processes independently and simultaneously in parallel in order to improve speed of instruction execution.

This improves the overall throughput but not the latency of a single task

Basic idea is like an assembly line in manufacturing

Operations of an instruction (Fetching, decoding, executing, and storing) occur in sequence
Each operation is performed independently
All processing units can work simultaneously

- In general an N-stage pipeline will improve throughput N-fold (or reduce CPI N-fold)
	- Ignoring initial delay to fill pipeline
	- Assuming stages are balanced i.e. all complete in one clock cycle
	- No [[Pipeline Hazards|Hazards]] (e.g. conditional branching)
