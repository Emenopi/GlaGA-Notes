---
tags:
  - Computer_Architecture_and_Network_Systems
---
A test which is commonly needed as it's unsafe to perform an action on a list p unless p actually points to a node


```
;p
#0000 EQU2 ( compare p with 0 )
,&pIsEmpty JCN
...
&pIsEmpty
```
