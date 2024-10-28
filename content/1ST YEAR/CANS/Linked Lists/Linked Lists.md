---
tags:
  - Computer_Architecture_and_Network_Systems
aliases:
  - Linked List
---
A dynamic [[Data Structures|Data Structure]] consisting of a sequence of nodes arranged in a linear order

The order is determined by a pointer in each node, therefore each node is a record with two fields:
- value / key
- next: pointer to the next node
The last node has nil in the "next" field (0 / null pointer)

The three key operations with linked lists are:
- [[Linked List Empty?]]
- [[Linked List Next Value?]]
- [[Linked List Next Node?]]