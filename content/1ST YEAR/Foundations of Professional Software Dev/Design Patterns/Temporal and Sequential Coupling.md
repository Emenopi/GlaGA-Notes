---
tags:
  - Foundations_of_Professional_Software_Dev
---
Temporal and Sequential coupling is similar in that the coupling is based upon the order of execution of the modules

Temporal coupling is said to occur when one module's has to wait on another module completing execution before it can complete it's own execution. This can be remedied by adding an event handler which fires after the first method and calls the other method.

Sequential coupling, on the other hand, specifically relates to the output of one module being used as the input for another. This can be remedied by controlling the sequence by one module to avoid the sequentially coupled functions from being called out of order - however, this then couples the methods temporally