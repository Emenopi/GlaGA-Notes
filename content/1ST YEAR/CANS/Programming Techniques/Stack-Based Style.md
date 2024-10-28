---
tags:
  - Computer_Architecture_and_Network_Systems
---
Programming technique for [[Assembly Language]] where:
- [[1ST YEAR/How to Learn a New Language/Variables/Variables]] kept on [[Stacks|Stack]] across group of [[Statements]]
- Less loads and stores
- Have to keep track on whether variables are in [[RAM|Memory]] or [[Stacks|Stack]]
- Some statements executed entirely on stack
- Object code is concise but harder to see correspondence to source code

Example:

```
x = 33
z = 42
y = 2*z
z = z-1
x = x*2+z

#21 #2a ( 33 42 )
DUP #02 MUL ( 33 42 84 )
;y STA ( 33 42; y=84=2z )
#01 SUB DUP ( 33 41 41 )
;z STA ( z = 41 = z-1)
#02 ROT ( 41 2 33 )
MUL ( 41 66 )
ADD ( 107 )
;x STA
```
