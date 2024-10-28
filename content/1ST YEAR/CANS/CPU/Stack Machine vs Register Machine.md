---
tags:
  - Computer_Architecture_and_Network_Systems
---
The key difference lies in the organisation of the [[Registers|Register]] file:
- In a [[Registers|Register]] machine:
	- Every register in the register file can be accessed independently so register has random access
	- Every instruction must contain the memory address of the register on which it will operate
- In a [[Stacks|Stack]] machine:
	- The register is organised as a stack, so new values can only be added to the top and values can only be read from the top two
	- Needs less information as no need for memory address