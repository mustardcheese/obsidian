First, what is a distributed system?
- A system that does not share memory or a clock
Why do we want distributed systems?
- Thermal and Performance issues -- moores law is too slow, we need more compute

Distributed Systems are similar in design and considerations to Operating Systems
- Failure is a key aspect and MUST be accounted for in DS
- In OS, you can generally "ignore" failures

Distributed Systems are like a multi-pc operating system
- Isolation
- Performance
- Correctness

> Failure is a first class citizen

We want two computers to agree on something. 
- "think like a vertex" mindset, operating on only partial information
- rely on message passing for complete picture