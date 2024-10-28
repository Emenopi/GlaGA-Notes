---
tags:
  - Computer_Architecture_and_Network_Systems
aliases:
  - Addressing
---
IP [[Addressing]] is a global scope meaning all addresses must be unique. These are logical addresses as they can change over time, hierarchical to allow for aggregating addresses, fixed length binary to optimise processing, and specify the location of the network interface. A host with several network interfaces will have one IP address per interface

Addresses are split into:
- Network part:
	- Number of bits in network part described by netmask
- Host part:
	- For the network itself, this is 0
	- The broadcast address has all bits of the host part equal to 1

IP addresses can be either:
- IPv4 (32 bit):
	- Has reached end of life due to insufficient addresses
- IPv6 ( 128 bit):
	- Intended as long term replacement for IPv4 mainly to increase address space
	- Also simplifies protocol, making high speed implementations easier
	- Requires changes to every host, router, firewall, and application so significant deployment challenge

Addresses can denote:
- Host identity:
	- Puts complexity in the network layer but simplifies upper layer protocols
- Location host attaches to network:
	- Simplifies network layer

The [[Network Layers|Network Layer]] address identifies the host, while the [[Transport Layer]] layer address identifies the user process. Multiple services operating at the Transport Layer level are multiplexed into a single IP Address