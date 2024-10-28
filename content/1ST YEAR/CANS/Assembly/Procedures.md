---
tags:
  - Computer_Architecture_and_Network_Systems
aliases:
  - Procedure
---
Procedures are reusable code, equivalent to a [[Functions|Function]]

Both call and return of procedures is handled using [[GOTO]] instructions, however since multiple calls will necessitate a return to a different place in the [[Applications|Application]], the [[Jump-And-Link]] Instruction is needed

Limitations:
- If a procedure calls another procedure it can't use the same [[Registers|Register]] again to store [[Arguments]] and return address
- If the procedure modifies any [[Registers]], it may destroy data belonging to the caller
- The basic call mechanism doesn't allow a procedure to call itself