---
tags:
  - Computer_Architecture_and_Network_Systems
---
[[Transmission Control Protocol (TCP)|TCP]] connection setup is a 3-way handshake whereby:
- A random number is sent by the sender
- The receiver sends that number back and requests an acknowledgement with another random number
- The sender sends the acknowledgement number back

Connection progress is shown by SYN and ACK flags in the TCP header.

This combination of operations ensures robustness, while the acknowledgements ensure [[TCP Reliability]]