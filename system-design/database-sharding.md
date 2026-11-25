# Sharding and replication

**Replication:** copies of the same data.
- Leader handles writes, followers serve reads.
- Scales reads, adds failover.
- Followers lag: a user may not see their own write (read from the leader right after writing).

**Sharding:** split data across databases by a key.

| Strategy | Example | Watch out for |
|---|---|---|
| Range | users A–M, N–Z | hot ranges |
| Hash | `hash(user_id) % shards` | resharding (use consistent hashing) |
| Directory | lookup table key → shard | the lookup service itself |

**Costs of sharding:** cross-shard joins and transactions get hard, rebalancing is work. Try indexes, caching, read replicas and vertical scaling first.

Pick the shard key from the main access pattern (usually tenant or user ID) so most queries hit one shard.
