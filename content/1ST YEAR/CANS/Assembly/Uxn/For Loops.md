---
tags:
  - Computer_Architecture_and_Network_Systems
aliases:
  - Uxn For Loops
---
A for loop in Uxntal, assuming the [[Stacks|Stack]] has two 1 byte values (hibound, and lobound) is:

```
	@i $1 ( iterator, starts at lower bound of loop )
	@for
	;i STA
&loop DUP ( since hibound will be consumed; hibound hibound )
;i LDA ( load iterator; hibound hibound i )
SWP ( hibound i hibound )
GTH ( condition true when loop is over )
	,&done JCN
	statement1
	statement2
	;i LDA INC ;i STA ( inc loop counter at end of body )
	,&loop JMP
&done
	POP ( pop hibound off stack )
```

Similarly, the size of an array can be found as so:

```
@max-of-array ( upper-bound lower-bound )
;&i STA ( store lower-bound in max-of-array/i; upper-bound )
&loop
DUP ( since ub will be consumed; ub ub )
;&i LDA ( load iterator )
SWP ( need i>ub, not ub>i )
GTH ( condition true when loop is over; ub cond )
,&done JCN ( if condition true, exit loop; ub )
( max calc )
;x ;&i LDA ADD LDA ;&max LDA GTH ,&update-max JCN
,&continue JMP
&update-max
;x ;&i LDA ADD LDA ;&max STA
&continue
;&max LDA
JMP2r
&max $1
( rest of loop logic )
;&i LDA INC ;&i STA ( increment loop counter at end of loop body )
,&loop JMP
&done
POP
JMP2r
&i $1 ( allocate byte for iterator )
```
