---
tags:
  - Computer_Architecture_and_Network_Systems
aliases:
  - Instruction Word
---
Every instruction word in UXN has 8 bits arranged into four fields: 1 : 1 : 1 : 5

- The lowest 5 [[Bits]] are the [[Opcode]]
- The other 3 bits are the modes:
	- Bit 6 is the short mode: 1 means instruction operates on 2 bytes instead of 1
	- Bit 7 is the keep mode: 1 means operate without consuming operands from the [[Stacks|Stack]]
	- Bit 8 is the return mode: 1 means operate on return stack instead of working stack