---
tags:
  - Computer_Architecture_and_Network_Systems
---
A variable whose lifetime is that of the [[Procedures|Procedure]] of it's [[Scope]]. There may be many instances of the one variable in the case of functions implementing [[Recursion]] and therefore they cannot be stored in the static data segment but instead in [[Stack Frames]] (in uxn, this is the working [[Stacks|Stack]]) 