---
tags:
  - Computer_Architecture_and_Network_Systems
aliases:
  - Record
---
Similar to [[Dictionaries]], accessed via field names using dot notation e.g. .record1

Defined in uxntal as so:

```
@x
&a 23 &b 21 &c 12

@y
&a $2 &b $2 &c $2
```


And accessed as so:

```
;x/a LDA
```

However, a better approach is [[Pointers]]:


```
;x .r1 STZ2 ( r1 = &x)

.r1 LDZ2 #0001 ADD2 LDA ( (*r1).fieldB )
.r1 LDZ2 #0002 ADD2 LDA ( (*r1).fieldB (*r1).fieldC )
ADD
.r1 LDZ2 STA ( *r1.fieldA = (*r1).fieldB + (*r1).fieldC )
```
