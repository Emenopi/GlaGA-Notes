---
tags:
  - Computer_Architecture_and_Network_Systems
---
Added to the Instruction Cycle - Processor checks for interrupt after every instruction:
- If no interrupt : Fetch next instruction
- If interrupt : 
	- Suspend execution of current [[Applications#|Application]]
	- Save context
	- Set PC to start address of [[Interrupts|Interrupt]] handler routine
	- Process interrupt
	- Restore context and continue interrupted program