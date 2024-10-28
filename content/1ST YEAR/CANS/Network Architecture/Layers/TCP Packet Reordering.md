---
tags:
  - Computer_Architecture_and_Network_Systems
---
Since duplicate ACK flags can also be caused by packet delay, it will appear that packets have been lost as per [[TCP Reliability]] configuration. This is prevented by the Triple Duplicate condition, as it is expected delay will be small and not result in four identical ACKs in a row