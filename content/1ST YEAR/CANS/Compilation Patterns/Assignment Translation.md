---
tags:
  - Computer_Architecture_and_Network_Systems
---
Load operands, do calculations, store result

Example:

```
x = a + b*c

;a LDA2 ( a )
;b LDA2 ( a b )
;c LDA2 ( a b c )

MUL2 ( a (b*c) )
ADD2 ( a+(b*c) )

;x STA2
```
