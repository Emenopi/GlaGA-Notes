---
tags:
  - Computer_Architecture_and_Network_Systems
aliases:
  - Congestion Control
  - Flow Control
---
Control of the sending rate by the [[Transport Layer]]. This must be performed end-to-end since only the end points know the characteristics of the entire path

Congestion control can be implemented at either the [[Network Layers|Network Layer]] or the Transport Layer
- Network Layer:
	- Safe
	- Ensures all transport protocols are controlled
	- BUT requires all applications use the same congestion control scheme
- Transport Layer:
	- Flexible
	- Transport protocols can optimise congestion control for applications 
	- BUT a misbehaving transport can congest the network

The key principles to ensure stability of the network are:
- Conservation of packets
- Additive increase and multiplicated decrease (AIMD) of the sending rate

	Ultimately the network only has a certain capacity (bandwidth and delay product of the path), when in equilibrium, one packet is sent for each acknowledgement received so that the total number of packets in transit is constant. Sending rate is automatically decreased as the network gets congested