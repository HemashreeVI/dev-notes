# CAP theorem, practically

When the network **partitions** (nodes can't talk), a distributed store must choose:

- **C**onsistency: every read sees the latest write (some requests fail), or
- **A**vailability: every request gets an answer (it might be stale).

Partitions will happen, so the real choice is **CP vs AP** during one.

| System leans | Examples | Fits |
|---|---|---|
| CP | ZooKeeper, etcd, a single-leader SQL DB | bookings, payments, locks |
| AP | Cassandra, DynamoDB (default), DNS | feeds, likes, carts, analytics |

**PACELC** adds: *Else* (no partition) you still trade **L**atency vs **C**onsistency.

A booking system can't sell one seat twice, so it picks consistency for the seat and can be AP for things like view counts.
