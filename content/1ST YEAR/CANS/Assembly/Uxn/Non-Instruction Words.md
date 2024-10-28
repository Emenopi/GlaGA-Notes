---
tags:
  - Computer_Architecture_and_Network_Systems
---
Non-instruction words in uxn are indicated by 'runes' and fall into three categories:
- Labels
	- @ for parent, & for child
	- Child labels can be used for relative access within the parent section
- Addresses
	- ; for absolute,  ,& for relative, . for zero-page address
	- There are corresponding load and store instructions:
		- LDA/LDR/LDZ and STA/STR/STZ
- Padding
	- | for absolute, $ for relative