---
tags:
  - Computer_Architecture_and_Network_Systems
aliases:
  - MAC
---
Deals with how to allow a channel to be used by multiple signals to avoid data collisions. It is two-stage acces:
- Detects that a collision is occuring/will occur by listening to the channel while/before sending
- Sends data if no collision
- Otherwise backs off and retransmits. The back-off delay is randomised and increasing to prevent repeated collisions and can be arranged to give priority to certain hosts/users/traffic classes