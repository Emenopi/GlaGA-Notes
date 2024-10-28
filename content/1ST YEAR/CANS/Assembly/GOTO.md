---
tags:
  - Computer_Architecture_and_Network_Systems
---
GOTO is an instruction in [[Assembly Language]] for controlling the flow of the program, however:
- Overuse can make the program hard to understand, unlikely to work, and difficult to debug

All jump instructions refer to *effective addresses* using the displacement+index format, for example:

```
jump loop[R0] ( GOTO instruction whose address is the label loop+0 )

jump 0[R14] ( GOTO instruction whose address is in R14 )

jump const[R2] ( GOTO Instruction whose address is const+R2)
```
