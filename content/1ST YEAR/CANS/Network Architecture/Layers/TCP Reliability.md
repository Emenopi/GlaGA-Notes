---
tags:
  - Computer_Architecture_and_Network_Systems
---
[[Transmission Control Protocol (TCP)|TCP]] connections are reliable since:
- Each packet has a sequence number and an acknowledgement number
	- Sequence number counts how many bytes are sent
	- Acknowledgement number specifies next byte expected to be received

Only contiguous packets are acknowledged. If a packet is lost, receipt of subsequent packets will trigger duplicate acknowledgements. Four duplicate acknowledgement packets in a row (Triple duplicate) signals that a packet has been lost. The TCP layer will re-transmit lost packets.

Alternatively, if acknowledgements stop returning, the receiver or network path has failed and will trigger a timeout