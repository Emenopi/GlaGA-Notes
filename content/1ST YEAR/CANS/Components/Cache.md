---
tags:
  - Computer_Architecture_and_Network_Systems
---
A small amount of fast memory between [[RAM|Main Memory]] and CPU - typically located on CPU or separate module

Cache includes tags to identify which block of main memory is in each cache slot

If required word is not available in cache, the entire block is transferred to the cache from the main memory (not just the word)

Writing to cache can be:
- Write-through policy
	- Writes to both cache and main memory
- Write-back policy
	- Write to cache only, then back-up to main memory when evicted from cache