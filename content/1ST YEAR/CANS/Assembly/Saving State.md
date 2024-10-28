---
tags:
  - Computer_Architecture_and_Network_Systems
aliases:
  - Save State
---
Saving state is used to retain the callers state when a [[Procedures|Procedure]] is called - this is achieved by storing the [[Registers]] to be used in [[RAM]] and later restoring them

There are two ways to achieve this:
- Allocate fixed [[1ST YEAR/How to Learn a New Language/Variables/Variables]] in memory to save the registers to
- Maintain a [[Stacks|Stack]] in memory (Most commonly used method)

The storage can be done by the caller or, more commonly, the callee

Every execution of a procedure pushes a [[Stack Frames|Stack Frame]] to memory