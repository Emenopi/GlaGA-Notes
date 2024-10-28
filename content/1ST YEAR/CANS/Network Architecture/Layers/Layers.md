---
tags:
  - Computer_Architecture_and_Network_Systems
aliases:
  - Layer
---
The network architecture is organised into layers:
- [[Physical Layers]]
	- Handles transmission of physical bits over a communication link
- [[Data Link Layers|Data Link Layer]]
	- Structures and frames physical layer bits by splitting the bit stream into frames
- [[Network Layers|Network Layer]]
	- Interconnects multiple links to form connection between hosts and handles routing among nodes within packet-switched networks
- [[Transport Layer]]
	- End-to-end transport of data from source to destination processes
- Session Layer
	- Provides a namespace used to tie together transport streams that are part of a single application
- Presentation Layer
	- Manages presentation, representation, and conversion of data. Provides common services used by multiple applications and comprises of application [[Protocols]]