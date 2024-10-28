---
tags:
  - Computer_Architecture_and_Network_Systems
---
Programming technique for [[Assembly Language]] where:
- Each high level [[Statements|Statement]] is compiled independently
- Makes heavy use of [[1ST YEAR/How to Learn a New Language/Variables/Variables]] stored in [[RAM|Memory]]
- Straightforward but inefficient
- Multiple loads and stores of each variable
- A lot of redundancy
- Object code corresponds well to source code, but may be unnecessarily long

Example:

```
x = 33
z = 42
y = 2*z
z = z-1
x = x*2+z

#21 ;x STA ( x = 33 )
#2a ;z STA ( z = 42 )
( y = 2*z )
#02
;z LDA ( 2 z )
MUL ( 2*z )
;y STA ( y = 2*z )
( z = z-1 )
;z LDA
#01 SUB
;z STA
( x = x*2+z )
;x LDA
#02
MUL
;z LDA ( x*2 z )
ADD
;x LDA ( x = x*2+z )
```
