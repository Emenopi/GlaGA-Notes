---
tags:
  - Computer_Architecture_and_Network_Systems
---
Example:

```
while i < n do:
	statement1
statement2

.i LDZ .n LDZ LTH
,&body JCN
	,&done JMP
	&body
statement1
,&loop JMP
&done
statement2
```

Example 2:

```
while true:
	statement

&loop
	statement
	,&loop JMP
```
