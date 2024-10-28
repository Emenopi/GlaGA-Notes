---
tags:
  - Computer_Architecture_and_Network_Systems
---
Since noise and interference at the [[Physical Layers|Physical Layer]] can cause bit errors, an error detecting code is added to each packet. This is generally done:
- At source: by adding redundant data that is calculated based on some property of the data (the error code)
- At destination: by recalculating the redundant data and checking it against the code received

The simplest of such codes are Parity codes which calculate how many 1 bits are in the data: party 1 if odd numbers, parity 0 if even.

Another example is Internet Checksum which sums data values and sends this checksum in each frame which is recalculated and checked at destination. This is more effective than parity codes and capable of detecting the most multiple bit errors


Error detecting codes can be extended to correct errors by transmitting an error correcting code additional to each frame which allows the receiver to correct errors without having to contact the sender.