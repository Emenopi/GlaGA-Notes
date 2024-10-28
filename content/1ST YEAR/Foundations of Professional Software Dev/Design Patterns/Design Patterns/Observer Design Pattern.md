---
tags:
  - Foundations_of_Professional_Software_Dev
---
Observer Design Pattern is a [[1ST YEAR/Foundations of Professional Software Dev/Design Patterns/Design Patterns/Design Patterns|Design Pattern]] where data is updated, the update is pushed to all dependant [[Objects]]

The Observer Design Pattern contains two interfaces: 
- Subject: able to register/remove observers and notify them
- Observer: able to update when notified

Implementation of the Observer Design Pattern should consider:
- Scale of updates: Better to update after certain degree of change
- Frequency of updates: Better to have minimum wait time before pushing
- Size of updates: Better to update only data which has changed rather than whole data structures

One method to reduce data transmission is to use a pull model rather than push model i.e. observers are notified of changes and decide whether to pull data or not
