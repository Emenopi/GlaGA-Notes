---
tags:
  - Computer_Architecture_and_Network_Systems
---
The [[GOTO]] instruction in uxntal. The foundation of control structures, typically called jump

All high-level control structures which change the flow of execution are translated to a combination of conditional and unconditional gotos

- Requires target instruction to have a label

Jumps to a relative address are 1 byte and to an absolute address are 2 bytes:
- ,addr JMP
- ;addr JMP2