---
tags:
  - Computer_Architecture_and_Network_Systems
aliases:
  - Multiplexor
---
Multiplexors (MUX) are data selectors. They chose one of the inputs and pass it through to the output

Takes two inputs plus selector input to determine the output - selector [[Bits|Bit]] is tells the MUX which input to select

out = (I<sub>0</sub> and !S) or (I<sub>1</sub> and S)

If a MUX has k select lines, it can select a max of 2<sup>k</sup> inputs

