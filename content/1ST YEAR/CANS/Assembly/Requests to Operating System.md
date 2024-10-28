---
tags:
  - Computer_Architecture_and_Network_Systems
aliases:
  - Request to Operating System
---
Many programs can't be performed directly by a user, therefore the program must request that the operation is carried out by the [[Operating Systems|Operating System]]

This is usually due to **security**, but can also be due to ease of programming

Operating system requests are performed via  *trap* instruction, which is a jump to the operating system, [[Pointers]] are then used to tell the operating system what to do

The specific codes used to make the request are defined by the operating system, not the hardware, and typically are:
- [[Termination]]
- Read Files
- Write to Files
- Allocate [[RAM|Memory]]