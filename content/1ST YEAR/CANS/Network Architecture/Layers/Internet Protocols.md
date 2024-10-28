---
tags:
  - Computer_Architecture_and_Network_Systems
aliases:
  - Internet Protocol
---
IP provides common abstraction layer for interface with transport protocols and data link technologies and physical links.

Key features are:
- Global inter-networking protocol
- Hourglass protocol stack with:
	- Many transport and application layer protocols
	- Single standard network layer protocol (IP)

IP is a packet switched network with uniform network, host addressing, and end-to-end connectivity, and a range of supported link-layer technologies. The IP service model is a best effort, connectionless packet delivery meaning there is:
- No need to set up a connection
- Network makes best effort to deliver but provides no guarantees. Network discards packets it can't deliver

Services provided by the IP layer are:
- [[IP Addressing|Addressing]]
- [[Fragmentation]]
- [[Loop Protection]]
- [[Header Checksum]]
- [[Transport Layer Protocol Identifier]]
- [[Differentiated Services]]