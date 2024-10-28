---
tags:
  - Computer_Architecture_and_Network_Systems
aliases:
  - Framing
  - Synchronisation
---
Since a physical stream provides an unreliable raw bit stream due to corruption and time disruption, the [[Data Link Layers|Data Link Layer]] must correct for this or mitigate impact. This is achieved by:
- Breaking raw bits into frames
- Transmitting and repairing individual frames
- Limiting the scope of transmission errors so that if retransmission is required, only the impacted frame needs retransmitted

In order to detect the start of a message, a start code (unique bit pattern) is added to the beginning of each frame. This enables synchronisation after an error.

In order to avoid the scenario where the start code is in the data elsewhere, bit stuffing is used whereby the sender inserts a 0 bit after where any five 1 bits are sent unless sending a start code