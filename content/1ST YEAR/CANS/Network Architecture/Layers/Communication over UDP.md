---
tags:
  - Computer_Architecture_and_Network_Systems
---
- The send call sends a single datagram
- The receiver received this single datagram

These are exactly one IP [[Packets|Packet]]

Since transmission is unreliable, packets may be lost, delayed, reordered, or duplicated in transit. The application must therefore be able to correct for this so usually the sender is required to send some sequence number with each packet.