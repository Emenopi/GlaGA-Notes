---
tags:
  - Computer_Architecture_and_Network_Systems
---
- Data is queued for transmission then split into segments
- Each segment is placed in a TCP segment
- When allowed by [[Congestion & Flow Control|Congestion Control]] system, the segment is sent

Since data is split, the data returned by the received doesn't necessarily correspond to a single send and can be in unpredicably sized chunks