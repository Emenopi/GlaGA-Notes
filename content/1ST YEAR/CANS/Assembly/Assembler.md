---
tags:
  - Computer_Architecture_and_Network_Systems
---
Translates [[Assembly Language]] to machine code

Maintains a [[1ST YEAR/How to Learn a New Language/Variables/Variables|Variable]] called the location counter:
- Address where it will place next piece of code
- Initially 0

1st pass : Reads through each line
- Decides how many words of [[RAM|Memory]] each line requires, adds this to the location counter
- If there is a label, remembers that address is current value of location counter (this goes into symbol table)

2nd pass : Read through each line again
- Generates words of machine code for each [[Statements|Statement]]
- If there is reference to a label that appears further on, looks up value in the symbol table