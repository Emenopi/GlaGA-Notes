---
tags:
  - Computer_Architecture_and_Network_Systems
---
Each high level programming construct is translated according to a standard pattern
- Assignment [[Statements]] :
	- Load
	- Arithmetic
	- Store in assembly
- Branching and Looping :
	- Goto label
	- If bexp then goto label


Useful to translate in two steps:
- Translate to simple low level language (pseudo-assembly)
	- Convert high level structures like if-else, for/while, to combination of conditional and unconditional goto statements
- Complete translation into [[Assembly Language]]