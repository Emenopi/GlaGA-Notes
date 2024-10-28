---
tags:
  - Computer_Architecture_and_Network_Systems
---
Pseudo-assembly example:

```
if x < y:
	statement1
statement2

;x LDA ;y LDA LTH
,&true JCN
,&false JMP
&true
statement1
&false
statement2
```

Example 2:

```
if x < y:
	statement1
else:
	statement2
statement3

;x LDA ;y LDA LTH
,&then JCN
,&else JMP
&then
statement1
&else
statement2
&done
statement3
```
