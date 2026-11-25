# Consistent hashing

Problem: with `server = hash(key) % N`, adding one server remaps almost every key, so the cache is wiped.

**Consistent hashing:** place servers and keys on a ring (hash space 0…2³²). A key goes to the next server clockwise.

```text
     key A → S2
  S1 ───── S2
   |        |
  S4 ───── S3
```

Adding or removing a server only moves the keys between it and its neighbour: about `1/N` of keys.

**Virtual nodes:** put each server at many points on the ring (e.g. 100) for an even spread and to share load when one fails.

Used by: DynamoDB/Cassandra partitioning, distributed caches, load balancers with sticky routing.
