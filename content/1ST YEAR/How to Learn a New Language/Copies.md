---
tags:
  - How_to_Learn_a_New_Language
aliases:
  - Copy
---
Copies can be either shallow or deep - in either case a new [[1ST YEAR/How to Learn a New Language/Variables/Variables|Variable]] is initiated with the same values as the original

Shallow copies initiate a new variable with the same pointers as the original, meaning that any changes to the original or copy will also change the other.

Deep copies, on the other hand initiate a new variable with new pointers despite the values stored being identical. This allows safe manipulation of data in one without it also changing the other