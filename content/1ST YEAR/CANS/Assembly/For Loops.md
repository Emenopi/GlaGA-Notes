---
tags:
  - Computer_Architecture_and_Network_Systems
---
The general pattern of for loops in assembly is:

```
for (i = 0; i < end; i++) {
	statement1;
	statement2;
}

&loop
		.i LDZ .n LDZ LTH ( loop condition )
		,&body JCN ( jump to body if condition true )
	,&done JMP
		statement1
		,&loop JMP
&done
		statement2

	
```

More specifically, for Uxntal, there is [[1ST YEAR/CANS/Assembly/Uxn/For Loops|Uxn For Loops]]